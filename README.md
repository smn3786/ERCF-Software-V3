# ERCF-Software-V3 "Happy Hare"
저의 ERCF를 사랑하며, 3D 프린팅 취미 생활의 많은 해들 중 가장 즐거운 경험이었습니다. 디자인은 뛰어나지만, 소프트웨어에 몇 가지 문제가 있었고 몇 가지 기능을 추가하고 사용자 친화성을 향상시키고자 했습니다. 특히 "sensorless filament homing" 브랜치 도입 이후에는 이것이 더욱 뚜렷해졌습니다. Klipper 플러그인으로서의 새로운 파이썬 구현이 마음에 들었지만, (매우 신뢰할 만한) 도구 헤드 센서를 활용하고 싶었습니다. 그래서 ERCF의 소프트웨어를 다시 작성했습니다. 여전히 기존의 구조와 코드 대부분을 유지하고 있지만, 더 중요한 것은 많은 새로운 기능을 갖추고 도구 헤드 센서와 센서리스 옵션을 통합했습니다. 저는 이것을 "Happy Hare" 릴리스 또는 v3이라고 부르고 있습니다.

또한, 몇몇 분들이 제가 마시는 모든 커피 비용을 지원하기 위해 기부를 하고 싶어했습니다. 저는 이 작업을 어떠한 금전적 보상을 위해 하는 것은 아니지만, 만약 기부를 하고 싶으신 분들은 PayPal https://www.paypal.me/moggieuk로 기부하시면 제가 ERCF와 함께하는 여러분의 삶을 더 즐겁게 만드는 데 사용될 것입니다.

감사합니다!

## 주요한 새로운 기능들::
<ul>
<li>툴헤드 센서 기반 로딩/언로딩과 최신 센서리스 필라멘트 홈 기능을 모두 지원합니다 (툴헤드 센서 없음).
<li>추가 기어 모터와 함께 에스트루더와 기어 모터를 함께 움직이는 동기화된 로딩 및 언로딩 단계를 지원하며, FLEX 재료와 함께 작동할 수 있는 툴헤드 센서를 사용하는 구성도 지원합니다!
<li>새로운 도구 - 게이트 매핑 개념과 함께 "EndlessSpool"을 완전히 구현했습니다. 이를 통해 비어 있는 게이트를 식별하고, 소진 후에도 올바른 필라멘트 스풀을 사용하여 툴 체인지를 할 수 있습니다. 또한, 슬라이싱과 스풀 로딩의 불일치 시 게이트를 도구에 매핑하는 장점이 있습니다.
<li>파일 기반의 새로운 로그 기능을 포함한 크게 개선된 로깅 기능입니다. 콘솔 로그를 최소화하고 Klipper 로그와 동일한 디렉토리에 위치한 `ercf.log` 파일로 디버깅 정보를 보낼 수 있습니다.
<li>로딩 및 언로딩 순서를 재미있게 시각화할 수 있는 선택적인 기능입니다.
<li>비어 있는 도구(게이트)를 지정하고 자동으로 사용 가능 여부를 확인할 수 있는 기능이 추가되었습니다.
<li>연관된 새로운 명령어와 상태를 사용하는 경우 필라멘트 바이패스 블록을 정식으로 지원합니다.
<li>기어 전류를 충돌 홈 프로시저 중에 (현재 TMC2209에만 해당) 그라인딩을 방지하기 위해 줄일 수 있는 기능입니다.
<li>편리한 필라멘트 "자동로드" 기능 및 인쇄 전에 모든 필라멘트가 준비되었는지 확인하는 게이트 체크 기능이 있습니다.
<li>기존 매크로에서 사용자 정의 작업을 수행할 필요가 없습니다.
<li>Moonraker 업데이트 관리자 지원
<li>재시작 시 상태와 통계의 완전한 지속성 보장!
<li>신뢰할 수 있는 서보 작동 - 더 이상 "킥백" 문제가 없습니다.
<li>필라멘트 측정 및 자동 메뚜기 탐지를 구현한 통합된 엔코더 드라이버!
<li>제 자매 프로젝트를 지원합니다...
</ul>

이제 ERCF를 위한 맞춤형 [KlipperScreen for ERCF](#klipperscreen-happy-hare-edition) 터치스크린 컨트롤이 가능합니다.

<img src="doc/my_klipperscreen.png" width="400" alt="KlipperScreen-Happy Hare edition">

## 기타 기능들::
<ul>
<li>측정 값을 평균화하고 필라멘트의 스프링에 기반한 보상을 추가하여 보덴 파이프의 ID와 길이에 따른 보정을 수행하고 구성 옵션을 고려하는 보정 루틴 재작업
<li>대부분의 옵션에 대해 새로운 명령어(ERCF_TEST_CONFIG)를 통한 런타임 구성을 지원하여 Klipper를 계속 재시작하거나 설정 중에 재보정하는 번거로움을 피할 수 있도록 합니다.
<li>Klipper "Timer too close" 오류를 유발하는 몇 가지 방법에 대한 해결책(하지만 Klipper 펌웨어에는 확실히 버그가 있을 수 있음)
<li>더 정확한 보정 기준을 위해 에스트루더 홈 이후 필라멘트의 스프링을 측정합니다.
<li>기어에서 에스트루더로 필라멘트 전환 시 신뢰성을 높이기 위해 servo_up 지연을 추가합니다(압력 유지)
<li>문제점을 진단하는 데 도움이 되는 새로운 "TEST_TRACKING" 명령어를 추가합니다.
<li>스톨가드 필라멘트 홈을 사용하는 실험적인 로직 추가(EASY-BRD를 사용한 설정이 쉽지 않으며, 센서리스 선택기 홈 옵션과 호환되지 않을 수 있음)
</ul>
  
## 코드 재작성의 다른 이점들:
<ul>
<li>공급된 매개변수와 설정의 오류 감지/확인이 크게 개선되었습니다.
<li>오류 처리의 일관성이 확보되었습니다. 예를 들어, "pause" 호출을 여러 번 하지 않도록 예외 처리를 사용합니다.
<li>모든 스테퍼 이동을 래핑하여 "DEVELOPER" 로깅 레벨 및 디버깅을 더 쉽게 할 수 있도록 하였습니다.
<li>새로운 로드 및 언로드 순서 (모든 빌드 구성을 지원하기 위해) 및 센서와 센서리스 로직을 효과적으로 결합하였습니다.
</ul>
  
## 설치
이 모듈은 설치 스크립트를 사용하여 기존 Klipper 설치에 설치할 수 있습니다. 설치가 완료되면 Moonraker update-manager에 추가되어 다른 Klipper 플러그인과 같이 쉽게 업데이트할 수 있습니다.

    cd ~
    git clone https://github.com/moggieuk/ERCF-Software-V3.git
    cd ERCF-Software-V3

    ./install.sh -i

`-i` 옵션을 사용하면 일부 혼동되는 매개변수 설정을 돕기 위해 대화식 프롬프트가 표시됩니다 (예: 센서리스 선택기 홈 설정). EASY-BRD 및 Fysetc ERB 설치의 경우 모든 핀을 자동으로 구성합니다. `-i` 플래그 없이 실행하면 새로운 템플릿인 `ercf*.cfg` 파일이 설치되지 않습니다. 기존의 `ercf*.cfg` 파일이 이미 존재하는 경우 이전 버전은 기존 구성을 덮어쓰지 않도록 `<file>.00` 확장자와 같이 번호가 매겨진 백업 파일로 이동됩니다. 새로운 `ercf*.cfg` 파일을 자동으로 설치하지 않기로 선택하는 경우 반드시 주의하여 해당 파일을 검토하고 제공된 템플릿과 비교하십시오 (이는 원래의 소프트웨어와 완전히 다른 소프트웨어입니다).
<br>

참고로, 설치 프로그램은 표준 위치에서 Klipper 설치 및 구성 파일을 찾습니다. 사용자 지정 위치가 있거나 설치 프로그램이 Klipper를 찾지 못하는 경우 `-k` 및 `-c` 플래그를 사용하여 각각 klipper 홈 디렉토리와 klipper 구성 디렉토리를 재정의할 수 있습니다. 또한, 설치 프로그램은 기기당 하나의 Klipper 인스턴스를 가정합니다. 여러 개의 Klipper 인스턴스가 있는 경우 `ercf*.cfg` 파일을 수동으로 설치하고 구성해야 할 수 있습니다.
<br>

기억해 주세요. `ercf_hardware.cfg`, `ercf_software.cfg`, `ercf_parameters.cfg` 파일은 모두 `printer.cfg` 마스터 구성 파일에서 참조되어야 합니다. `client_macros.cfg` 파일도 참조되어야 합니다. 이미 작동하는 PAUSE/RESUME/CANCEL_PRINT 매크로가 없는 경우에도 참조되어야 합니다 (그러나 매크로에 대한 예상 사항을 먼저 읽어보십시오). 이러한 include 문은 설치 스크립트로 자동으로 추가될 수 있습니다.
<br>

전문가 팁: `install.sh -i`를 실행하는 데 우려가 있다면 다음과 같이 실행하십시오: `install.sh -i -c /tmp -k /tmp` 이렇게 하면 `*.cfg` 파일을 생성하지만 /tmp에 저장됩니다. 그런 다음 해당 파일을 읽고, 기존 설치를 보완할 부분을 추출하거나 단순히 다양한 질문에 대한 답변이 어떤 작용을 하는지 확인할 수 있습니다...
<br>

또한 [Encoder 문제에 대한 노트](doc/ENCODER.md)도 꼭 읽어보세요. 더 좋은 엔코더일수록 이 소프트웨어의 작동이 더 원활해집니다.
<br>

ERCF를 Happy Hare를 사용하여 구성 및 설정하는 방법은 [새로운 V2 매뉴얼](https://github.com/EtteGit/EnragedRabbitProject/raw/no_toolhead_sensor/Documentation/ERCF_Manual.pdf)에 문서화된 내용과 95% 동일합니다. README와 설치된 'ercf_*.cfg' 파일을 읽어 어떤 차이점이 있는지 이해하는 것이 중요합니다. [차이점 요약](doc/DIFFERENCES.md)도 확인해 보세요.

## Revision History
<ul>
<li> v1.0.0 - Initial Beta Release
<li> v1.0.3 - Bug fixes from community: Better logging on toolchange (for manual recovery); Advanced config parameters for adjust tolerance used in 'apply_bowden_correction' move; Fixed a couple of silly (non serious) bugs
<li> v1.1.0 - New commands: ERCF_PRELOAD & ERCF_CHECK_GATES ; Automatic setting of clog detection distance in calibration routine ; New interactive install script to help EASY-BRD setup; Bug fixes
<li> v1.1.1 - Fixes for over zealous tolerance checks on bowden loading; Fix for unloading to far if apply_bowden_correction is active; new test command: ERCF_TEST_TRACKING; Fixed slicer based tool load issue
<li> v1.1.2 - Improved install.sh -i to include servo and calib bowden length; Better detection of malfunctioning toolhead sensor
<li> v1.1.3 - Added ERCF_RECOVER command to re-establish filament position after manual intervention and filament movement. Not necessary if you use ERCF commands to correct problem but useful to call prior to RESUME; Much improved install.sh to cover toolhead sensor and auto restart moonraker on first time install
<li> v1.1.4 - Change to automatic clog detection length based on community feedback
<li> v1.1.5 - Further install.sh improvements - no longer need filament_sensor defined or duplicate pin override if not using clog detection; Cleaned up documentation in template config file; Stallguard filament homing should now be possible (have to configure by hand); Additional configuration checks on startup; minor useability improvements based on community feedback
<li> v1.1.6 - New feature to log to file independently to console (allows for clean console and debug to logfile);  New gate statistics (like slippage) are recorded and available with an augmented ERCF_DUMP_STATS command; Several minor improvements and fixes suggested by community
<li> v1.1.7 - Automatic setting of encoder state - no need to put anything ERCF related into existing macros (START/PAUSE/RESUME/STOP/CANCEL) anymore!;  Improvements to install script for non EASY-BRD config; Exposed all built-in gear/extruder feed speeds; Tweaks to tolerance checks to prevent false pauses; No annoying pause/unlock sequence while you are playing out of a print. UPDATE TO CONFIG FILES RECOMMENDED
<li> v1.1.8 - Enhanced ERCF_CHECK_GATES command; better configuraton of tip forming; Workarounds to Timer Too Close errors on selector; Fined grained current reduction control; less conservative restting of filament state; servo remains up on failed load; fixes typos and spelling mistakes. Full details here: https://discord.com/channels/460117602945990666/909743915475816458/1058586768791838791
<li> v1.1.9 - Installer support for the Fytsec ERB Burrows board; Inclusion of display setup for 12864 mini displays; Bug fixes
<li> v1.2.0 - Major new feature for being able to persist all ERCF state between restarts - now you can just turn on an print!; Various bug fixes, error message and status display improvements. SOME ADDITIONS TO `ercf_parameters.cfg` CONFIG FILE
<li> v1.2.1 - MAJOR: Bundled servo driver with careful PWM synchronization to avoid servo kickback!!! (Requires re-running ./install.sh)
<li> v1.2.2 - Automatic clog length setting. No more [filament_runout_sensor] or [duplicate_pin] setup (Required re-running ./install.sh)
<li> v1.2.3 - Update to support KlipperScreen; Additional printer variables exposed; Cleanup of bypass commands; Bug fixes
<li> v1.2.4 - Improvement of clog detection during wipetower movements generated by slicer; Enhanced ERCF_ENDLESS_SPOOL command; Restore users "idle_timeout" when print ends; Updated ercf_software for stand-alone tip formation
<li> v1.2.5 - New `_ERCF_ACTION_CHANGED` callback for LED setting and the list; Selector calibration automatically saves measurements in ercf_vars.cfg; New flow rate % printer variable on ercf_encoder; install now favors printer_data over old klipper location; added couple of soaktests; explicit encoder on/off command; better tolerance of TMC stallguard problems; minor bug fixes
</ul>
Note: Upgrade from versions prior to v1.2.0 requires the re-running of ./install.sh.  See [update notes](doc/UPGRADE.md) for more information

## 새로운 명령어 요약 (옵션은 [명령어 참조](#ercf-command-reference)를 참고하세요):
  | 명령어 | 설명 |
  | -------- | ----------- |
  | ERCF_STATUS | ERCF 상태, 기능 및 도구-게이트 매핑에 대한 보고 |
  | ERCF_TEST_CONFIG | 런타임에서 필수 로드/언로드 구성 옵션 확인/변경 |
  | ERCF_DISPLAY_TTG_MAP | 현재 도구-게이트 매핑 표시 (EndlessSpool을 위해 설계됨) |
  | ERCF_REMAP_TTG | 도구-게이트 매핑 (TTG) 재구성. 게이트를 비워둘 수도 있습니다. |
  | ERCF_SET_GATE_MAP | 필라멘트 유형, 색상 및 사용 가능 여부 구성 |
  | ERCF_ENDLESS_SPOOL | 정의된 EndlessSpool 그룹을 런타임에서 수정 |
  | ERCF_SELECT_BYPASS | 언로드하고 구성된 바이패스 선택기 위치 선택 |
  | ERCF_LOAD | 현재 도구 또는 단순히 엑스트루더 로드 |
  | ERCF_TEST_HOME_TO_EXTRUDER | 엑스트루더 홈을 보정하기 위한 테스트 - TMC 전류 설정 등 |
  | ERCF_TEST_TRACKING | 엔코더가 기어 모터를 추적하는 방식을 시각적으로 테스트 |
  | ERCF_PRELOAD | 필라멘트 로딩을 돕는 도우미. 필라멘트를 게이트에 피드하면 ERCF가 적절한 위치에 잡고 지정된 게이트로 배치합니다. |
  | ERCF_CHECK_GATES | 게이트를 검사하고 사용 가능 여부 표시 |
  | ERCF_RECOVER | 필라멘트 위치를 복구하고 필요한 경우 ERCF 상태 재설정 |
  | ERCF_ENABLE | ERCF를 활성화하고 비활성화 후 상태 재설정 |
  | ERCF_DISABLE | 모든 ERCF 기능을 비활성화 |
  | ERCF_RESET | ERCF 지속 상태를 기본값으로 재설정 |
  
  이번에 완전히 재작성되었기 때문에 일부 기존 명령어가 수정되고 향상되었습니다. 자세한 내용은 이 페이지의 맨 끝에 있는 [명령어 참조](#ercf-command-reference)를 참고하세요.

## 자세한 선택된 기능 설명:
### 로딩 및 언로딩 순서에 대한 구성 설명
툴헤드 센서가 구성되어 있는 경우 필라멘트 홈 방법이 기본값이 되고 엑스트루더로 홈하는 선택적이지만 불필요한 단계가 됩니다. 또한, 엑스트루더로 홈하는 단계는 도구 0의 보정 중 항상 수행됩니다 (`ercf_calib_ref`를 정확히 설정하기 위해). 정확한 홈 위치 결정과 그라인딩을 피하기 위해 기어 스테퍼의 전류 감소 비율인 `extruder_homing_current`를 기본 실행 전류의 %로 조정하세요.

#### 로드 순서 이해하기:
    1. ERCF [T1] >.... [encoder] .............. [extruder] .... [sensor] .... [nozzle] UNLOADED (@0.0 mm)
    2. ERCF [T1] >>>>> [encoder] >>>........... [extruder] .... [sensor] .... [nozzle] (@48.2 mm)
    3. ERCF [T1] >>>>> [encoder] >>>>>>>>...... [extruder] .... [sensor] .... [nozzle] (@696.4 mm)
    4. ERCF [T1] >>>>> [encoder] >>>>>>>>>>>>>> [extruder] .... [sensor] .... [nozzle] (@696.4 mm)
    5. ERCF [T1] >>>>> [encoder] >>>>>>>>>>>>>> [extruder] >>>| [sensor] .... [nozzle] (@707.8 mm)
    6. ERCF [T1] >>>>> [encoder] >>>>>>>>>>>>>> [extruder] >>>> [sensor] >>>> [nozzle] LOADED (@758.7 mm)
  
위의 "시각적 로그"는 로딩 과정의 개별 단계를 보여줍니다:
  <ol>
    <li>툴 1의 게이트에 언로드된 상태에서 시작
    <li>먼저 ERCF는 서보를 클램프하고 엔코더를 통해 짧은 길이의 필라멘트를 끌어냅니다. 필라멘트가 감지되지 않으면 'load_encoder_retries'번 (기본값 2) 시도합니다. 필라멘트가 여전히 없으면 오류를 보고합니다. 이 초기 움직임의 속도는 그런 다음 ERCF는 빠른 움직임으로 보덴을 통해 필라멘트를 로드합니다. 이 움직임의 속도는 'long_moves_speed'로 제어됩니다. 이 움직임은 "Timer too close" 오류를 극복하기 위한 한 가지 해결책으로 'num_moves'로 여러 번의 움직임으로 분할될 수 있습니다. 기어 모터의 단계 크기를 8로 유지하면 단일 빠른 움직임으로 작업할 수 있을 것입니다. 이 움직임의 길이는 ERCF를 보정할 때 설정되고 'ercf_vars.cfg'에 저장됩니다. 만약 슬리피지가 감지되면 이 움직임의 보정을 허용하는 고급 옵션인 'apply_bowden_correction'과 'load_bowden_tolerance'가 있습니다. (자세한 내용은 'ercf_parameters.cfg'의 주석을 참조하세요.)
    <li>예시에서는 툴헤드 센서를 사용했지만, 센서리스 필라멘트 홈을 구성하면 ERCF는 이 지점을 홈 위치로 인식하기 위해 엑스트루더 기어에 점진적으로 접근합니다. 이 홈 움직임은 'extruder_homing_max' (엑스트루더 홈을 시도하기 위해 전진해야 하는 최대 거리), 'extruder_homing_step' (충돌 감지로 엑스트루더 홈에 접근할 때 사용되는 단계 크기), 'extruder_homing_current' (충돌로부터 필라멘트 그라인딩을 방지하기 위해 임시로 기어 스테퍼 전류를 얼마나 %로 감소시킬지 조정 가능)로 제어됩니다.
    <li>이것은 툴헤드로 이동하는 단계로서 가장 중요한 전환점입니다. ERCF는 필라멘트가 제대로 잡혔는지 확인하기 위해 엑스트루더를 전진시킵니다. 툴헤드 센서의 경우 이것은 결정적인 결과입니다. 센서로 전진하여 새로운 홈 위치로 사용합니다. 센서리스 ERCF의 경우 필라멘트가 잡혔음을 의미하는 엔코더 움직임을 찾습니다. 선택적으로 이 움직임은 신뢰성을 높이기 위해 기어와 엑스트루더 모터를 동기적으로 작동시킬 수 있습니다. 'sync_load_length' (엑스트루더에 진입 시 동기화된 로드의 길이)입니다. 신뢰성을 더 향상시키기 위해 ERCF는 필라멘트의 "스프링"을 활용하여 'delay_servo_release' mm로 서보 해제를 지연시킵니다. 동기 로드를 사용할 때 이는 필라멘트의 압축을 완화하여 더 조용한 로딩을 가능하게 하며, 엑스트루더 전용 로드에서는 필라멘트를 잡기 위해 기어에 압력을 유지합니다.
<br>
툴헤드 센서가 활성화된 경우 이 단계에는 약간 더 있습니다. ERCF는 툴헤드 센서로 필라멘트의 끝을 홈하며 이는 'toolhead_homing_max' (툴헤드 센서에 홈하기 위해 전진해야 하는 최대 거리)와 'toolhead_homing_step' (툴헤드 센서로 홈하기 위해 사용되는 단계 크기)로 제어됩니다. 'sync_load_length'가 0보다 크면 이 홈 단계는 동기화됩니다.
<br>이 단계의 모든 움직임 속도는 'sync_load_speed'로 제어됩니다.
    <li>이제 필라멘트는 엑스트루더에 독점적으로 제어됩니다. 필라멘트는 용융 영역까지 남은 거리로 이동합니다. 이 거리는 'home_position_to_nozzle'에 의해 정의되며, 툴헤드 센서에서 노즐까지의 거리 또는 엑스트루더 기어에서 노즐까지의 거리에 따라 달라집니다. 이 움직임 속도는 'nozzle_load_speed'로 제어됩니다. 이제 로드되어 인쇄할 준비가 된 상태입니다.
  </ol>

#### 언로드 순서 이해하기:
    1. ERCF [T1] <<<<< [encoder] <<<<<<<<<<<<<< [extruder] <<<< [sensor] <... [nozzle] (@34.8 mm)
    2. ERCF [T1] <<<<< [encoder] <<<<<<<<<<<<<< [extruder] <<<| [sensor] .... [nozzle] (@87.7 mm)
    3. ERCF [T1] <<<<< [encoder] <<<<<<<<<<<<<< [extruder] .... [sensor] .... [nozzle] (@91.7 mm)
    4. ERCF [T1] <<<<< [encoder] <<<<<<<<...... [extruder] .... [sensor] .... [nozzle] (@729.9 mm)
    5. ERCF [T1] <<<<< [encoder] <<<........... [extruder] .... [sensor] .... [nozzle] (@729.9 mm)
    6. ERCF [T1] <<<.. [encoder] .............. [extruder] .... [sensor] .... [nozzle] (@795.5 mm)
    7. ERCF [T1] <.... [encoder] .............. [extruder] .... [sensor] .... [nozzle] UNLOADED (@795.5 mm)
  
위의 "시각적 로그"는 로딩 과정의 개별 단계를 보여줍니다:
  <ol>
    <li>툴 1에 로드된 필라멘트로 시작합니다. 이 예시는 슬라이서의 제어를 받지 않은 언로드에서 가져온 것이므로 가장 먼저 필라멘트의 끝에 팁이 형성되고, 이로 인해 필라멘트가 엑스트루더의 냉각 영역에 위치합니다. 이 작업은 'ercf_software.cfg'의 사용자가 편집한 '_ERCF_FORM_TIP_STANDALONE' 매크로에 의해 제어됩니다.
    <li>이 단계는 툴헤드 센서와 함께 발생합니다. 필라멘트가 툴헤드 센서에 더 이상 감지되지 않을 때까지 당겨집니다. 이는 'nozzle_unload_speed'에서 수행되며, 필라멘트를 얼마나 더 철수해야 하는지를 더 정확하게 결정하고, 필라멘트가 노즐에 막히지 않았는지 안전성을 확인하는 역할을 합니다.
    <li>그런 다음 ERCF는 필라멘트를 'nozzle_unload_speed'로 엑스트루더에서 밀어냅니다. 센서리스인 경우에는 대략적인 값이지만, 툴헤드 센서를 사용하는 경우 'extruder_to_nozzle'와 'sensor_to_nozzle'의 설정에 따라 이동한 거리를 최적화할 수 있습니다. (차이는 이동한 거리를 나타냄)
    <li>엑스트루더 기어 진입 지점으로 간다고 믿는 위치에 도달하면 선택적으로 짧은 동기화(기어와 엑스트루더) 이동을 구성할 수 있습니다. 이는 'sync_unload_speed'와 'sync_unload_length'로 제어됩니다. 이는 안전한 단계이자 "머리 빠지는" 작업이지만, ERCF 기어가 필라멘트를 잡고 있는지 확인하기 위해서도 사용됩니다. 동기화된 언로드가 구성되어 있지 않은 경우에도 ERCF는 여전히 기어 모터만 사용하여 보덴 언로드를 수행하며, 다시 한 번 필라멘트가 잡히는지 확인합니다.
    <li>이제 필라멘트는 보덴을 통해 빠르게 추출됩니다. 이 속도는 'long_moves_speed'로 제어되며, 움직임은 로딩할 때와 마찬가지로 'num_moves'로 분할할 수 있습니다.
    <li>빠른 보덴 움직임 완료
    <li>이 시점에서 ERCF는 필라멘트가 엔코더에서 나올 때까지 짧은 움직임을 연속적으로 수행합니다. 이 속도는 'short_moves_speed'로 제어됩니다.
    <li>필라멘트가 엔코더에서 해제되면 남은 거리를 'short_moves_speed'로 이동하여 파크 위치로 이동됩니다. 이제 필라멘트가 언로드되었습니다.
  </ol>

ERCF가 상태를 알 수 없는 경우, ERCF는 다른 움직임을 수행하고 센서를 통해 필라멘트 위치를 확인하려고 합니다. 이로 인해 위의 순서가 수정되고 언로드 시 빠른 보덴 움직임이 생략될 수 있습니다.

#### Possible loading options (explained in ercf_parameters.cfg template):
     If you have a toolhead sensor for filament homing:
        toolhead_homing_max: 35            # Maximum distance to advance in order to attempt to home to toolhead sensor (default 20)
        toolhead_homing_step: 1.0          # Step size to use when homing to the toolhead sensor (default 1)

    Options without toolhead sensor (but still needed for calibration with toolhead sensor)

        extruder_homing_max: 50            # Maximum distance to advance in order to attempt to home the extruder
        extruder_homing_step: 2.0          # Step size to use when homing to the extruder with collision detection (default 2)
    
    For accurate homing and to avoid grinding, tune the gear stepper current reduction

        extruder_homing_current: 40        # Percentage of gear stepper current to use when extruder homing (TMC2209 only, 100 to disable)
    
    How far (mm) to run gear_stepper and extruder together in sync on load and unload. This will make loading and unloading
    more reliable and will act as a "hair pulling" step on unload.  These settings are optional - use 0 to disable
    Non zero value for 'sync_load_length' will synchronize the whole homing distance if toolhead sensor is installed

        sync_load_length: 10               # mm of synchronized extruder loading at entry to extruder
        sync_unload_length: 10             # mm of synchronized movement at start of bowden unloading
    
    This is the distance of the final filament load from the homing point to the nozzle
    If homing to toolhead sensor this will be the distance from the toolhead sensor to the nozzle
    If extruder homing it will be the distance from the extruder gears (end of bowden) to the nozzle
    
    This value can be determined by manually inserting filament to your homing point (extruder gears or toolhead sensor)
    and advancing it 1-2mm at a time until it starts to extrude from the nozzle.  Subtract 1-2mm from that distance distance
    to get this value.  If you have large gaps in your purge tower, increase this value.  If you have blobs, reduce this value.
    This value will depend on your extruder, hotend and nozzle setup.

        home_position_to_nozzle: 72        # E.g. Revo Voron with CW2 extruder using extruder homing

    Advanced and optional. If you regularly switch between sensorless and toolhead sensor or you want to optimize extruder
    unload when using toolhead sensor you can override 'home_position_to_nozzle' with these more specific values
    (Note that the difference between these two represents the extruder to sensor distance and is used as the final
    unload distance from extruder. An accurate setting can reduce tip noise/grinding on exit from extruder)

        extruder_to_nozzle: 72		# E.g. Revo Voron with CW2 extruder using extruder homing
        sensor_to_nozzle: 62		# E.g. Revo Voron with CW2 extruder using toolhead sensor homing

    Again, these last two settings are optional and can be omitted

*물론, 위에 표시된 실제 거리는 사용자 정의될 수 있습니다.*
  
**고급 옵션**
동기 로드 이동을 사용하지 않을 때, 서보가 잡고 있는 필라멘트의 스프링 장력을 활용하여 필라멘트를 엑스트루더에 공급하는 데 도움이 됩니다. 이는 `delay_servo_release` 설정으로 제어됩니다. 기본값은 2mm이며, 수정할 필요가 없을 것입니다.
<br>스톨가드를 사용하여 엑스트루더로 홈을 잡는 옵션인 `homing_method=1`이 있지만 권장되지 않습니다: (i) 현재 감소로 인해 필요하지 않습니다. (ii) EASY-BRD와 즉시 호환되지 않습니다. (iii) 현재 센서리스 선택기 홈과 호환되지 않으며 기어 엔드스톱 구성을 사용합니다.
<br>'apply_bowden_correction' 설정이 활성화되어 있는 경우, 드라이버는 엔코더 값을 "신뢰"하고 필라멘트를 원하는 보덴 위치의 끝으로 이동시키기 위해 보정 움직임을 수행합니다. 이는 고속 로딩 시 필라멘트가 슬리피지되는 것을 의심할 때 유용합니다. (정확한 엔코더가 필요함). 비활성화된 경우, 기어 스테퍼가 보덴에서 필라멘트 위치 조정에 완전히 책임을집니다. (피더 튜브에서 최소한의 마찰이 필요함). 연관된 (고급) 'load_bowden_tolerance'은 보정 움직임을 적용할 지점을 정의합니다. 자세한 내용은 'ercf_parameters.cfg'를 참조하세요.

  **홈 위치 이후의 거리에 대한 참고 사항**
위의 로딩 설정과 관계없이 `home_to_nozzle` 거리를 정확히 설정하는 것이 중요합니다. 툴헤드 센서로 홈을 잡지 않는 경우, 이 거리는 엑스트루더 진입부터 노즐까지의 거리가 될 것입니다. 툴헤드 센서로 홈을 잡는 경우, 이는 (더 작은) 센서부터 노즐까지의 거리가 될 것입니다. 예를 들어, Revo & Clockwork 2 설정에서의 거리는 각각 72mm 또는 62mm입니다.

#### 가능한 언로딩 옵션:
로딩보다 훨씬 간단합니다. 툴헤드 센서가 설치된 경우, 엑스트루더에서 추출할 때 자동으로 체크포인트로 활용됩니다.
`sync_unload_length`는 보덴 언로딩 시작 시 동기화된 이동의 mm를 제어합니다. 이는 팁이 기어에 걸린 경우 언로딩을 더 신뢰할 수 있게 만들어주며, 언로딩 시 "머리를 빠지게 하는(hair pulling)" 단계로 작용합니다. 이는 선택적인 단계이며, 비활성화하려면 0으로 설정하십시오.

### Clog/Runout 감지
ERCF는 필라멘트의 런아웃이나 잡힘 상태를 감지하기 위해 엔코더를 사용할 수 있습니다. 이 기능은 ercf_parameters.cfg의 `enable_clog_detection`로 활성화됩니다. 이 기능은 엑스트루더가 밀어내는 필라멘트 양과 엔코더로 측정한 필라멘트 양을 모니터링하여 비교합니다. 엑스트루더가 보정된 `clog_detection_length`보다 더 앞서게 되면 런아웃/잡힘 감지 로직이 작동합니다. 만약 잡힘이 감지되면 프린터는 보통대로 일시 중지되고 `ERCF_UNLOCK` 및 `RESUME`을 요구하여 계속 진행할 수 있습니다. 만약 런아웃이 감지되고 무한 스풀이 활성화된 경우, 해당 툴이 다시 매핑되고 인쇄가 자동으로 계속됩니다.

이 값을 `1`로 설정하면 정적인 잡힘 감지 길이를 사용하여 잡힘 감지가 활성화됩니다. `2`로 설정하면 감지 길이를 자동으로 조정합니다. 이는 잘못된 트리거가 발생하지 않을 때까지 지속적으로 조정되므로 완전한 보장을 제공하지는 않습니다. 자동 알고리즘은 `[ercf_encoder]` 섹션의 두 가지 변수로 제어됩니다:

    desired_headroom: 5.0		# The runout headroom that ERCF will attempt to maintain (closest ERCF comes to triggering runout)
    average_samples: 4		# The "damping" effect of last measurement. Higher value means clog_length will be reduced more slowly

### Tool-to-Gate (TTG) 매핑 및 EndlessSpool 적용
`Tx` 명령을 사용하여 도구를 변경할 때, ERCF는 기본적으로 같은 번호의 게이트 (스풀)에 있는 필라멘트를 선택합니다. 이 *Happy Hare* 드라이버에 내장된 매핑을 사용하여 이를 수정할 수 있습니다. 이 기능에는 3가지 주요 사용 사례가 있습니다:
<ol>
  <li>슬라이스한 gcode 파일과 필라멘트를 다르게 로드한 경우... 문제 없습니다. 인쇄하기 전에 적절한 재매핑 명령을 실행하기만 하면 됩니다.
  <li>일부 "도구"에는 필라멘트가 없고 선택을 피하려는 경우 해당 도구를 비어있음으로 표시할 수 있습니다.
  <li>가장 중요한 것은 EndlessSpool입니다. 필라멘트가 한 게이트 (스풀)에서 끝나면 순서대로 다음 게이트에 자동으로 매핑되어 원래 도구에서 계속 인쇄됩니다. 또한 스풀을 교체하고 맵을 업데이트하여 인쇄 중에 사용 가능 여부를 표시할 수도 있습니다.
</ol>

*Note that the initial availability of filament at each gate can also be specified in the `ercf_parameters.cfg` file by updating the `gate_status` list. E.g.
>gate_status = 1, 1, 0, 0, 1, 0, 0, 0, 1

  on a 9-gate ERCF would mark gates 2, 3, 5, 6 & 7 as empty
 
To view the current mapping you can use either `ERCF_STATUS` or `ERCF_DISPLAY_TTG_MAP`
  
![ERCF_STATUS](doc/ercf_status.png "ERCF_STATUS")

<br>

Since EndlessSpool is not something that triggers very often you can use the following to simulate the action:
  > ERCF_ENCODER_RUNOUT FORCE_RUNOUT=1

This will emulate a filament runout and force ERCF to interpret it as a true runout and not a possible clog. ERCF will then run the following sequence:
<ul>
  <li>Move the toolhead up a little (defined by 'z_hop_distance & z_hop_speed') to avoid blobs
  <li>Call '_ERCF_ENDLESS_SPOOL_PRE_UNLOAD' macro.  Typically this where you would quickly move the toolhead to your parking area
  <li>Perform the toolchange and map the new gate in the sequence
  <li>Call '_ERCF_ENDLESS_SPOOL_POST_LOAD' macro.  Typically this is where you would clean the nozzle and quickly move your toolhead back to the position where you picked it up in the PRE_UNLOAD macro
  <li>Move the toolhead back down the final amount and resume the print
</ul>

The default supplied _PRE and _POST macros call PAUSE/RESUME which is typically a similar operation and may be already sufficient. Note: A common problem is that a custom _POST macro does not return the toolhead to previous position.  ERCF will still handle this case but it will move very slowly because it is not expecting large horizontal movement.
  
### Visualization of filament position
  The `log_visual` setting turns on an off the addition of a filament tracking visualization in either long form or abbreviated KlipperScreen form.  This is a nice with log_level of 0 or 1 on a tuned and functioning setup.
  
![Bling is always better](doc/visual_filament.png "Visual Filament Location")

### Filament bypass
If you have installed the optional filament bypass block your can configure its selector position by setting `bypass_selector` in `ercf_parameters.cfg`. Once this is done you can use the following command to unload any ERCF controlled filament and select the bypass:
  > ERCF_SELECT_BYPASS`
  
  Once you have filament loaded <u>up to the extruder</u> you can load the filament to nozzle with:
  > ERCF_LOAD

  Finally, you can unload just the extruder using the usual eject.
  > ERCF_EJECT

### Adjusting configuration at runtime
  All the essential configuration and tuning parameters can be modified at runtime without restarting Klipper. Use the `ERCF_TEST_CONFIG` command to do this:
  
  <img src="doc/ercf_test_config.png" width="500" alt="ERCF_TEST_CONFIG">
  
  Any of the displayed config settings can be modified.  E.g.
  > ERCF_TEST_CONFIG home_position_to_nozzle=45
  
  Will update the distance from homing position to nozzle.  The change is designed for testing was will not be persistent.  Once you find your tuned settings be sure to update `ercf_parameters.cfg`

### Updated Calibration Ref
  Setting the `ercf_calib_ref` is slightly different in that it will, by default, average 3 runs and compensate for spring tension in filament held by servo. It might be worth limiting to a single pass until you have tuned the gear motor current. Here is an example:
  
  <img src="doc/Calibration Ref.png" width="500" alt="ERCF_CALIBRATION_SINGLE TOOL=0">
  
### Useful pre-print functionality
  The `ERCF_PRELOAD` is an aid to loading filament into the ERCF.  The command works a bit like the Prusa MMU and spins gear with servo depressed until filament is fed in.  Then parks the filament nicely. This is the recommended way to load filament into ERCF and ensures that filament is not under/over inserted blocking the gate.

Similarly the `ERCF_CHECK_GATES` command will run through all the gates (or those specified), checks that filament is loaded, correctly parks and updates the "gate status" map of empty gates. Could be a really useful pre-print check...

### Gate statistics
  Per-gate statistics that aggregate servo/load/unload failures and slippage are recorded throughout a session and can be logged at each toolchange.  An augmented `ERCF_DUMP_STATS` command will display these stats and will give a rating on the "quality assessment" of functionality of the gate (more info is sent to debug level typically found in the `ercf.log`).  The per-gate statistics will record important data about possible problems with individual gates.  Since the software will try to recover for many of these conditions you might not know you have a problem.  One particularly useful feature is being able to spot gates that are prone to slippage.  If slippage occurs on all gates equally, it is likely an encoder problem.  If on one gate if might be incorrect calibration of that gate or friction in the filament path.  Note that `ERCF_DUMP_STATS` will display this data but the details are sent to the DEBUG log level so you will only see it in the ercf.log file if you setup as I suggest.

### Logging
There are four configuration options that control logging:

    log_level & logfile_level can be set to one of (0 = essential, 1 = info, 2 = debug, 3 = trace, 4 = developer)
    Generally you can keep console logging to a minimal whilst still sending debug output to the ercf.log file
    Increasing the console log level is only really useful during initial setup to save having to constantly open the log file
      log_level: 1
      logfile_level: 3            # Can also be set to -1 to disable log file completely
      log_statistics: 1           # 1 to log statistics on every toolchange, 0 to disable (still recorded)
      log_visual: 1               # 1 to log a fun visual representation of ERCF state showing filament position, 0 disable

The logfile will be placed in the same directory as other log files and is called `ercf.log`.  It will rotate and keep the last 5 versions (just like klipper).  The default log level for ercf.log is "3" but can be set by adding `logfile_level` in you `ercf_parameters.cfg`.  With this available my suggestion is to reset the console logging level `log_level: 1` for an uncluttered experience knowing that you can always access `ercf.log` for debugging at a later time.  Oh, and if you don't want the logfile, no problem, just set `logfile_level: -1`

### Pause / Resume / Cancel_Print macros:
It is no longer necessary to added anything to these macros -- ERCF will automatically wrap anything defined.   If you have used other versions of the software then you should remove these customizations. To understand the philosophy and expectations here is the sequence:
<br>
  
During a print, if ERCF detects a problem, it will record the print position, safely lift the nozzle up to `z_hop_height` at `z_hop_speed` (to prevent a blob).  It will then call the user's PAUSE macro (which can be the example one supplied in `ercf_software.cfg`).  It is expected that pause will save it's starting position (GCODE_SAVE_STATE) and move the toolhead to a park area, often above a purge bucket, at fast speed.
<br>

The user then calls `ERCF_UNLOCK`, addresses the issue and calls `RESUME` to continue with the print.
<br>
  
The user's RESUME macro may do some purging or nozzle cleaning, but is expected to return the toolhead at higher speed to where it was left when the pause macro was called.  At this point the ERCF wrapper takes over and is responsible for dropping the toolhead back down to the print and resumes printing.
<br>
  
ERCF will always return the toolhead to the correct position, but if you leave it in your park area will will move it back very slowly.  You can to follow the above sequence to make this operation fast to prevent oozing from leaking on your print. 

### Recovering ERCF state:
At some point when a project occurs during a multi-color print ERCF will go into a `pause/locked` state.  Generally the user would then call `ERCF_UNLOCK`, fix the issue and then resume print with `RESUME`.   While fixing the problem you may find it useful to issue ERCF commands to move the filament around or change gate. If you do this the ERCF will "know" the correct state when resuming a print and everything will be copacetic. However, if you manually move the filament you are able to tell ERCF the correct state with the `ERCF_RECOVER` command.  This command is also useful when first turning on an ERCF with filament already loaded.  Instead of ERCF having to unload and reload to figure out the state you can simple tell it!  Here are some examples:

    ERCF_RECOVER - attempt to automatically recover the filament state.  The tool or gate selection will not be changed.
    ERCF_RECOVER TOOL=0 - tell ERCF that T0 is selected but automatically look at filament location
    ERCF_RECOVER TOOL=5 LOADED=1 - tell ERCF that T5 is loaded and ready to print
    ERCF_RECOVER TOOL=1 GATE=2 LOADED=0 - tell ERCF that T1 is being serviced by gate #2 and the filament is Unloaded

### State persistence
This is considered advanced functionality but it is incredibly useful once you are familar with the basic operation of ERCF. Essentially the state of everything from the EndlessSpool groups to the filament position and gate selection can be persisted accross restarts (homing is not even necessary)! The implication of using this big time saver is that you must be aware that if you modify ERCF whilst it is off-line you will need to correct the appropriate state prior to printing. Here is an example startup state:

  <img src="doc/persisted_state.png" width=600 alt="Persisted Startup State">

(note this was accomplished by setting `startup_status: 1` in ercf_parameters.cfg and can be generated anytime with the `ERCF_DISPLAY_TTG_MAP SUMMARY=1` command)
This graphic indicates how I left ERCF the day prior... Filaments are loaded in gates 0,1 & 6; Gate/Tool #1 is selected; and the filament is fully loaded. If you are astute you can see I have remapped T2 to be on gate #3 and T3 to be on gate #2 because previously I had loaded these spools backward and this saved me from regenerating g-code.
<br>

In addition to basic operational state the print statistics and gate health statistics are persisted and so occasionally you might want to explicitly reset them with `ERCF_RESET_STATS`.  There are 5 levels of operation for this feature that you can set based on your personal preference/habbits. The level is controlled by a single variable `persistence_level` in `ercf_parameters.cfg`:

    Advanced: ERCF can auto-initialize based on previous persisted state. There are 5 levels with each level bringing in
    additional state information requiring progressively less inital setup. The higher level assume that you don't touch
    ERCF while it is offline and it can come back to life exactly where it left off.  If you do touch it or get confused
    then issue an appropriate reset command (E.g. ERCF_RESET) to get state back to the defaults.
    Enabling `startup_status` is recommended if you use persisted state at level 2 and above
    Levels: 0 = start fresh every time (the former default behavior)
            1 = restore persisted endless spool groups
            2 = additionally restore persisted tool-to-gate mapping
            3 = additionally restore persisted gate status (filament availability)
            4 = additionally restore persisted tool, gate and filament position!

Generally there is no downside of setting the level to 2 and so that is the suggested default.  Really, so long as you are aware that persistence is happening and know how to adjust/reset you can set the level to 4 and enjoy immediate ERCF availability.  So what options are there for resetting state?  Here is the complete list:

<ul>
  <li>`ERCF_RESET` - Reset all persisted state back to defaults / unknown except for print stats and per-gate health stats
  <li>`ERCF_RESET_STATS` - Reset print stats and per-gate health stats back to 0
  <li>`ERCF_REMAP_TTG RESET=1` - Reset just the tool-to-gate mapping
  <li>`ERCF_ENDLESS_SPOOL_GROUPS RESET=1` - Reset just the endless spool groups back to default
  <li>`ERCF_SET_GATE_MAP RESET=1` - Reset information about the filament type, color and availability
  <li>`ERCF_RECOVER` - Automatically discover or manually reset filament position, selected gate, selected tool, filament availability (lots of options)
  <li>Needless to say, other operations can also be used to update state
</ul>

Couple of miscellaneous notes:
<ul>
  <li>Closely relevant to the usefulness of this functionality is the `ERCF_CHECK_GATES` command that will examine all or selection of gates for presence of filament
  <li>In the graphic depictions of filament state the '*' indicates presence, '?' unknown and ' ' or '.' the lack of filament
  <li>With tool-to-gate mapping it is entirely possible to have multiple tools mapped to the same gate (for example to force a multi-color print to be monotone) and therefore some gates can be made inaccessable until map is reset
  <li>The default value for `gate_status`, `tool_to_gate_map` and `endless_spool_groups` can be set in `ercf_parameters.cfg`.  If not set the default will be, Tx maps to Gate#x, the status of each gate is unknown and each tool is in its own endless spool group (i.e. not part of a group)
</ul>

### ERCF variables accessable in your own macros:
Happy Hare exposes the following 'printer' variables:

    printer.ercf.enabled : {bool}
    printer.ercf.is_locked : {bool}
    printer.ercf.is_homed : {bool}
    printer.ercf.tool : {int} 0..n | -1 for unknown | -2 for bypass
    printer.ercf.gate : {int} 0..n | -1 for unknown
    printer.ercf.material : {string} Material type for current gate (useful for print_start macro)
    printer.ercf.next_tool : {int} 0..n | -1 for unknown | -2 for bypass (during a tool change)
    printer.ercf.last_tool : {int} 0..n | -1 for unknown | -2 for bypass (during a tool change after unload)
    printer.ercf.last_toolchange : {string} description of last change similar to M117 display
    printer.ercf.clog_detection : {int} 0 (off) | 1 (manual) | 2 (auto)
    printer.ercf.endless_spool : {int} 0 (disabled) | 1 (enabled)
    printer.ercf.filament : {string} Loaded | Unloaded | Unknown
    printer.ercf.loaded_status : {int} state machine - exact location of filament
    printer.ercf.filament_direction : {int} 1 (load) | -1 (unload)
    printer.ercf.servo : {string} Up | Down | Unknown
    printer.ercf.ttg_map : {list} defined gate for each tool
    printer.ercf.gate_status : {list} per gate: 0 empty | 1 available | -1 unknown
    printer.ercf.gate_material : {list} of material names, one per gate
    printer.ercf.gate_color : {list} of color names, one per gate
    printer.ercf.endless_spool_groups : {list} group membership for each tool
    printer.ercf.action : {string} Idle | Loading | Unloading | Forming Tip | Heating | Loading Ext | Exiting Ext | Checking | Homing | Selecting

Exposed on ercf_encoder:

    printer['ercf_encoder ercf_encoder'].encoder_pos : {float} Encoder position measurement in mm
    printer['ercf_encoder ercf_encoder'].detection_length : {float} The detection length for clog detection
    printer['ercf_encoder ercf_encoder'].min_headroom : {float} How close clog detection was from firing on current tool change
    printer['ercf_encoder ercf_encoder'].headroom : {float} Current headroom of clog detection (i.e. distance from trigger point)
    printer['ercf_encoder ercf_encoder'].desired_headroom Desired headroom (mm) for automatic clog detection
    printer['ercf_encoder ercf_encoder'].detection_mode : {int} Same as printer.ercf.clog_detection
    printer['ercf_encoder ercf_encoder'].enabled : {bool} Whether encoder is currently enabled for clog detection
    printer['ercf_encoder ercf_encoder'].flow_rate : {int} % flowrate (extruder movement compared to encoder movement)

## KlipperScreen Happy Hare Edition
<img src="doc/ercf_main_printing.png" width="500" alt="KlipperScreen">

Even if not a KlipperScreen user you might be interested in my brand new [KlipperScreen version](https://github.com/moggieuk/KlipperScreen-Happy-Hare-Edition). Be sure to follow the install directions carefully and read the [panel-by-panel](https://github.com/moggieuk/KlipperScreen-Happy-Hare-Edition/blob/master/docs/ERCF.md) documentation.  It will make you even happier!!


## My Testing:
This software is largely rewritten as well as being extended and so, despite best efforts, has probably introduced some bugs that may not exist in the official driver.  It also lacks extensive testing on different configurations that will stress the corner cases.  I have been using successfully on Voron 2.4 / ERCF with EASY-BRD.  I use a self-modified CW2 extruder with foolproof microswitch toolhead sensor. My day-to-day configuration is to load the filament to the extruder in a single movement (`num_moves=1`) at 200mm/s, then home to toolhead sensor with synchronous gear/extruder movement (option #1 explained above).  I use the sensorless selector and have runout and EndlessSpool enabled.

### My Setup:
<img src="doc/My Voron 2.4 and ERCF.jpg" width="400" alt="My Setup">

### Some setup notes based on my learnings:

Firstly the importance of a reliable and fairly accurate encoder should not be under estimated. If you cannot get very reliable results from `ERCF_CALIBRATE_ENCODER` then don't proceed with setup - address the encoder problem first. Because the encoder is the HEART of ERCF I [created a how-to](doc/ENCODER.md) on fixing many possible problems with encoder.
<ul>
  <li>If using a toolhead sensor, that must be reliable too.  The hall effect based switch is very awkward to get right because of so many variables: strength of magnet, amount of iron in washer, even temperature, therefore I strongly recommend a simple microswitch based detection.  They work first time, every time.
  <li>The longer the bowden length the more important it is to calibrate correctly (do a couple of times to check for consistency).  Small errors multiply with longer moves!
  <li>Eliminate all points of friction in the filament path.  There is lots written about this already but I found some unusual places where filament was rubbing on plastic and drilling out the path improved things a good deal.
  <li>This version of the driver software both, compensates for, and exploits the spring that is inherently built when homing to the extruder.  The `ERCF_CALIBRATE_SINGLE TOOL=0` (which calibrates the *ercf_calib_ref* length) averages the measurement of multiple passes, measures the spring rebound and considers the configuration options when recommending and setting the ercf_calib_ref length.  If you change basic configuration options it is advisable to rerun this calibration step again.
  <li>The dreaded "Timer too close" can occur but I believe I have worked around most of these cases.  The problem is not always an overloaded mcu as often cited -- there are a couple of bugs in Klipper that will delay messages between mcu and host and thus provoke this problem.  To minimize you hitting these, I recommend you use a step size of 8 for the gear motor. You don't need high fidelity and this greatly reduces the chance of this error. Also, increasing 'num_moves' also is a workaround.  I'm not experiencing this and have a high speed (200 mm/s) single move load with a step size of 8.
  <li>The servo problem where a servo with move to end position and then jump back can occur due to bug in Klipper just like the original software but also because of power supply problems. The workaround for the former is increase the same servo "dwell" config options in small increments until the servo works reliably. Note that this driver will retry the initial servo down movement if it detects slippage thus working around this issue to some extent.
  <li>I also added a 'apply_bowden_correction' config option that dictates whether the driver "believes" the encoder or not for long moves.  If enabled, the driver will make correction moves to get the encoder reading correct.  If disabled the gear stepper movement will be applied without slippage detection.  Details on when this is useful is documented in 'ercf_parameters'.  If enabled, the options 'load_bowden_tolerance' and 'unload_bowden_tolerance' will set the threshold at which correction is applied.
  <li>I can recommend the "sensorless selector" option -- it works well once tuned and provides for additional recovery abilities if filament gets stuck in encoder preventing selection of a different gate. However there are some important things to note:
  <ul>
    <li>The selector cart must home against something solid. You need to make sure there are no wires or zip tie getting in the way.
    <li>If the motor audibly vibrates but doesn't appear to reliably detect home you selector belt might be too loose.
    <li>It is likely necessary to change the square head homing screw for a lower profile button head one -- the reason is that you will get inaccurate homing position if you are forceable stopping on the microswitch.  You just want to make sure the microswitch is triggered when the selector cart comes to a stop.
    <li>You can also add a small spacer to the slider mechanism make the selector cart physically stops before fully pressing the microswitch fully. Just be sure that the homing point is before gate #0. (I use a 1mm thick printed washer on the 8mm rods. See my repro for ERCF hacks).
    <li>Finally it is important to experiement and tune the `driver_SGTHRS` value which is the point at which the TMC driver detects the stepper has stalled. Lower values are less sensitive (selector can ram too hard) and too high a value can mean a bit of friction on the selector is detected as a stall and interpreted as a blocked selector.
  </ul>
  <li>Speeds.... starting in v1.1.7 the speed setting for all the various moves made by ERCF can be tuned.  These are all configurable in the 'ercf_parameters.cfg' file or can be tested without restarting Klipper with the 'ERCF_TEST_CONFIG' command.  If you want to optimise performance you might want to tuning these faster.  If you do, watch for the gear stepper missing steps which will often be reported as slippage.
</ul>

Good luck and hopefully a little less *enraged* printing.  You can find me on discord as *moggieuk#6538*

  
  ---
  
# ERCF Command Reference
  
  *Note that some of these commands have been enhanced from the original*

  ## Logging, Stats and Persisted state
  | Command | Description | Parameters |
  | ------- | ----------- | ---------- |
  | ERCF_RESET | Reset the ERCF persisted state back to defaults | None |
  | ERCF_RESET_STATS | Reset the ERCF statistics | None |
  | ERCF_DUMP_STATS | Dump the ERCF statistics (and Gate statistics to debug level - usually the logfile) | None |
  | ERCF_SET_LOG_LEVEL | Sets the logging level and turning on/off of visual loading/unloading sequence and stats reporting | LEVEL=\[1..4\] The level of logging to the console (1 recommended) <br>LOGFILE=\[1..4\] The level of logging to the ercf.log file (3 recommended) <br>VISUAL=\[0\|1\] Whether to also show visual representation <br>STATS=\[0\|1\] Whether to log print stats and gate summary on every tool change |
  | ERCF_STATUS | Report on ERCF state, capabilities and Tool-to-Gate map | SHOWCONFIG=\[0\|1\] Whether or not to describe the machine configuration in status message. Default 0 |
  | ERCF_DISPLAY_ENCODER_POS | Displays the current value of the ERCF encoder | None |
  <br>

  ## Core ERCF functionality
  | Command | Description | Parameters |
  | ------- | ----------- | ---------- |
  | ERCF_PRELOAD | Helper for filament loading. Feed filament into gate, ERCF will catch it and correctly position at the specified gate | GATE=\[0..n\] The specific gate to preload. If omitted the currently selected gate can be loaded |
  | ERCF_UNLOCK | Unlock ERCF operations after a pause caused by error condition | None |
  | ERCF_HOME | Home the ERCF selector and optionally selects gate associated with the specified tool | TOOL=\[0..n\] After homing, select this gate as if ERCF_SELECT TOOL=xx was called <br>FORCE_UNLOAD=\[0\|1\] Optional. If specified will override default intelligent filament unload behavior prior to homing |
  | ERCF_SELECT_TOOL | DEPRECATED but included as alias to 'ERCF_SELECT TOOL=' to be compatible with current documentation | DEPRECATED |
  | ERCF_SELECT | Selects the gate associated with the specified tool (TTG map) or the specific gate regardless of TTG map | TOOL=\[0..n\] The tool to be selected <br>GATE=\[0..n\] The gate to be selected (ignores TTG map) |
  | ERCF_SELECT_BYPASS | Unload and select the bypass selector position if configured | None |
  | ERCF_LOAD | Loads filament in currently selected tool/gate to extruder. Optionally performs just the extruder load part of the sequence - designed for bypass unloading | EXTRUDER_ONLY=\[0\|1\] To force just the extruder loading (automatic if in bypass) <br>NOTE: Owing to current documented use for test loading (correctly use ERCF_TEST_LOAD instead) it is necessary to pass `TEST=0` to force the loading of current tool/gate. This will be updated in the future |
  | ERCF_CHANGE_TOOL | Perform a tool swap (generally called from 'Tx' macros) | TOOL=\[0..n\] <br>STANDALONE=\[0\|1\] Optional to force standalone logic (tip forming)<br> QUIET=\[0\|1\] Optional to always suppress swap statistics |
  | ERCF_EJECT | Eject filament and park it in the ERCF gate or does the extruder unloading part of the unload sequence if in bypass | EXTRUDER_ONLY=\[0\|1\] To force just the extruder unloading (automatic if in bypass) |
  | ERCF_PAUSE | Pause the current print and lock the ERCF operations | FORCE_IN_PRINT=\[0\|1\] This option forces the handling of pause as if it occurred in print and is useful for testing |
  | ERCF_RECOVER | Recover filament position and optionally reset ERCF state. Useful to call prior to RESUME if you intervene/manipulate filament by hand | TOOL=\[0..n\] \| -2 Optionally force set the currently selected tool (-2 = bypass). Use caution! <br>GATE=\[0..n\] Optionally force set the currently selected gate if TTG mapping is being leveraged otherwise it will get the gate associated with current tool. Use caution! <br>LOADED=\[0\|1\] Optionally specify if the filamanet is fully loaded or fully unloaded. Use caution! If not specified, ERCF will try to discover filament position |
  | ERCF_ENABLE | Enable ERCF and reset state after disable | None |
  | ERCF_DISABLE | Disable all ERCF functionality | None |
  | ERCF_ENCODER | Explicitly enable or disable the encoder. Note that the encoder state is set automatically so this will only be sticky until next tool change | ENABLE=\[0\|1\] |
  <br>
  
  ## Servo and motor control
  | Command | Description | Parameters |
  | ------- | ----------- | ---------- |
  | ERCF_SERVO_DOWN | Engage the ERCF gear | None |
  | ERCF_SERVO_UP | Disengage the ERCF gear | None |
  | ERCF_MOTORS_OFF | Turn off both ERCF motors | None |
  | ERCF_BUZZ_GEAR_MOTOR | Buzz the ERCF gear motor and report on whether filament was detected | None |
  <br>
  
 ## Tool to Gate map and Endless spool
  | Command | Description | Parameters |
  | ------- | ----------- | ---------- |
  | ERCF_ENCODER_RUNOUT | Filament runout handler that will also implement EndlessSpool if enabled | FORCE_RUNOUT=1 is useful for testing to validate your _ERCF_ENDLESS_SPOOL\*\* macros |
  | ERCF_DISPLAY_TTG_MAP | Displays the current Tool -> Gate mapping (can be used all the time but generally designed for EndlessSpool  | SUMMARY=\[0\|1\] Whether to show complete or summary view |
  | ERCF_REMAP_TTG | Reconfiguration of the Tool - to - Gate (TTG) map.  Can also set gates as empty! | RESET=\[0\|1\] If specified the Tool -> Gate mapping will be reset to that defined in `ercf_parameters.cfg` <br>TOOL=\[0..n\] <br>GATE=\[0..n\] Maps specified tool to this gate (multiple tools can point to same gate) <br>AVAILABLE=\[0\|1\]  Marks gate as available or empty<br>QUIET=\[0\|1\] Optional. Supresses dump of current TTG map to log file<br>MAP={comma separated list of gates} Specify the entire TTG map for bulk updates |
  | ERCF_SET_GATE_MAP | Optionally configure the filament type, color and availabilty. Used in colored UI's and available via printer variables in your print_start macro | RESET=\[0\|1\] If specified the 'gate_materials, 'gate_colors' and 'gate_status' will be reset to that defined in `ercf_parameters.cfg` | DISPLAY=\[0\|1\] To simply display the current gate map<br>The following must be specified together to create a complete entry in the gate map:<br>GATE=\[0..n\] Gate numer<br>MATERIAL=.. The material type. Short, no spaces. e.g. "PLA+"<br>COLOR=.. The color of the filament. Can be a string representing one of the w3c color names found [here[(https://www.w3.org/TR/css-color-4/#named-colors) e.g. "violet" or a color string in the hexadeciaml format RRGGBB e.g. "ff0000" for red. NO space or # symbols. Empty string for no color<br>AVAILABLE=\[0\|1\] Optionally marks gate as empty or available<br>QUIET=\[0\|1\] Optional. Supresses dump of current gate map to log file |
  | ERCF_ENDLESS_SPOOL | Modify the defined EndlessSpool groups at runtime | RESET=\[0\|1\] If specified the EndlessSpool groups will be reset to that defined in `ercf_parameters.cfg` <br>GROUPS={comma separated list of groups} The same format as the default groups defined in ercf_parameters.cfg. Must be the same length as the number of ERCF gates | QUIET=\[0\|1\] Optional. Supresses dump of current TTG and endless spool map to log file<br>ENABLE=\[0\|1\] Optional. Force the enabling or disabling of endless spool at runtime (not persisted) |
  | ERCF_CHECK_GATES | Inspect the gate(s) and mark availability | GATE=\[0..n\] The specific gate to check <br>TOOL=\[0..n\] The specific too to check (same as gate if no TTG mapping in place) <br>TOOLS="comma separated list of tools" The list of tools to check. Typically used in print start macro to validate all necessary tools <br>If all parameters are omitted all gates will be checked (the default)<br>QUIET=\[0\|1\] Optional. Supresses dump of gate status at end of checking procedure |
  <br>

  ## Calibration
  | Command | Description | Parameters |
  | ------- | ----------- | ---------- |
  | ERCF_CALIBRATE | Complete calibration of all ERCF tools | None |
  | ERCF_CALIBRATE_SINGLE | Calibration of a single ERCF tool | TOOL=\[0..n\] <br>REPEATS=\[1..10\] How many times to repeat the calibration for reference tool T0 (ercf_calib_ref) <br>VALIDATE=\[0\|1\] If True then calibration of tool 0 will simply verify the ratio i.e. another check of encoder accuracy (should result in a ratio of 1.0) |
  | ERCF_CALIBRATE_SELECTOR | Calibration of the selector for the defined tool | GATE=\[0..n\] or TOOL=\[0..n\] |
  | ERCF_CALIB_SELECTOR | DEPRECATED, but included as alias to 'ERCF_CALIBRATE_SELECTOR' because of use in current documentation | DEPRECATED |
  | ERCF_CALIBRATE_ENCODER | Calibration routine for ERCF encoder | DIST=.. Distance (mm) to measure over. Longer is better, defaults to 500mm <br>REPEATS=.. Number of times to average over <br>SPEED=.. Speed of gear motor move. Defaults to long move speed <br>ACCEL=.. Accel of gear motor move. Defaults to motor setting in ercf_hardware.cfg <br>MINSPEED=.. & MAXSPEED=.. If specified the speed is increased over each iteration between these speeds (only for experimentation) |
  <br>
  
  ## User Testing
  | Command | Description | Parameters |
  | ------- | ----------- | ---------- |
  | ERCF_TEST_GRIP | Test the ERCF grip of the currently selected tool | None |
  | ERCF_TEST_SERVO | Test the servo angle | VALUE=.. Angle value sent to servo |
  | ERCF_TEST_MOVE_GEAR | Move the ERCF gear | LENGTH=..\[200\] Length of gear move in mm <br>SPEED=..\[50\] Stepper move speed <br>ACCEL=..\[200\] Gear stepper accel |
  | ERCF_TEST_LOAD | Test loading filament | LENGTH=..[100] Test load the specified length of filament into selected tool |
  | (ERCF_LOAD) | Identical to ERCF_TEST_LOAD | |
  | ERCF_TEST_UNLOAD | Move the ERCF gear | LENGTH=..[100] Length of filament to be unloaded <br>UNKNOWN=\[0\|1\] Whether the state of the extruder is known. Generally 0 for standalone use, 1 simulates call as if it was from slicer when tip has already been formed |
  | ERCF_TEST_HOME_TO_EXTRUDER | For calibrating extruder homing - TMC current setting, etc. | RETURN=\[0\|1\] Whether to return the filament to the approximate starting position after homing - good for repeated testing |
  | ERCF_TEST_TRACKING | Simple visual test to see how encoder tracks with gear motor | DIRECTION=\[-1\|1\] Direction to perform the test <br>STEP=\[0.5..20\] Size of individual steps <br>Defaults to load direction and 1mm step size |
  | ERCF_TEST_CONFIG | Dump / Change essential load/unload config options at runtime | Many. Best to run ERCF_TEST_CONFIG without options to report all parameters than can be specified |

  | ERCF_SOAKTEST_SELECTOR | QA reliability testing to put the selector movement under stress to test for failures | LOOP=..\[100\] Number of times to repeat the test <br>SERVO=\[0\|1\] Whether to include the servo down movement in the test |
  | ERCF_TEST_LOAD_SEQUENCE | Soak testing of load sequence. Great for testing reliability and repeatability| LOOP=..\[10\] Number of times to loop while testing <br>RANDOM=\[0\|1\] Whether to randomize tool selection <br>FULL=\[0 \|1 \] Whether to perform full load to nozzle or short load just past encoder |
  <br>

  ## User defined/configurable macros (in ercf_software.cfg)
  | Command | Description | Parameters |
  | ------- | ----------- | ---------- |
  | _ERCF_ENDLESS_SPOOL_PRE_UNLOAD | Called prior to unloading the remains of the current filament |
  | _ERCF_ENDLESS_SPOOL_POST_LOAD | Called subsequent to loading filament in the new gate in the sequence |
  | _ERCF_FORM_TIP_STANDALONE | Called to create tip on filament when not in print (and under the control of the slicer). You tune this macro by modifying the defaults to the parameters |
  | _ERCF_ACTION_CHANGED | Callback that is called everytime the `printer.ercf.action` is updated. Great for contolling LED lights, etc |
<br>

*Working reference PAUSE / RESUME / CANCEL_PRINT macros are defined in client_macros.cfg*

  
    (\_/)
    ( *,*)
    (")_(") ERCF Ready
  
