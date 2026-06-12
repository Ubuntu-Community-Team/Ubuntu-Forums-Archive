---
title: "Games freezing on quit"
date: 2010-09-11
forum: Multimedia Software
---

### Post by KutViZ on 2010-09-11
When I play games and want to quit the system freezes and can't exit at any way. Sometimes even freezes while playing. Tried Urban Terror, Enemy Territory. 0 A.D. freezed while playing, but i was running it from terminal and in window mode so Alt+tab helped me out. 

I have Ati Radeon HD5650, 4 gb ram Turion P520 in laptop.

Here's exactly what the terminal has put out at 0. AD
> 
gepzsir@gepzsir-laptop:/usr/games$ sudo ./0ad
TIMER| InitVfs: 53.3489 ms
TIMER| InitScripting: 1.1325 ms
TIMER| CONFIG_Init: 2.78427 ms
TIMER| write_sys_info: 996.593 us
Compile log for shader shaders/globallight.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Compile log for shader shaders/model_light.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Linker log for shaders/model_light.xml:
Vertex shader(s) linked, no fragment shader(s) defined. 
 
Compile log for shader shaders/postouv1.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Compile log for shader shaders/model_lightp.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Linker log for shaders/model_lightp.xml:
Vertex shader(s) linked, no fragment shader(s) defined. 
 
Compile log for shader shaders/instancing_base.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Compile log for shader shaders/instancing_light.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Linker log for shaders/instancing_light.xml:
Vertex shader(s) linked, no fragment shader(s) defined. 
 
Compile log for shader shaders/instancing_lightp.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Linker log for shaders/instancing_lightp.xml:
Vertex shader(s) linked, no fragment shader(s) defined. 
 
Compile log for shader shaders/instancing.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Linker log for shaders/instancing.xml:
Vertex shader(s) linked, no fragment shader(s) defined. 
 
Compile log for shader shaders/instancingp.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Linker log for shaders/instancingp.xml:
Vertex shader(s) linked, no fragment shader(s) defined. 
 
TIMER| InitRenderer: 129.346 ms
TIMER| ps_console: 3.00495 ms
TIMER| ps_lang_hotkeys: 2.06345 ms
TIMER| common/setup.xml: 1.41606 ms
TIMER| common/styles.xml: 333.87 us
TIMER| common/sprite1.xml: 2.57041 ms
TIMER| common/init.xml: 5.07009 ms
TIMER| pregame/sprites.xml: 969.847 us
TIMER| pregame/styles.xml: 160.962 us
TIMER| pregame/mainmenu.xml: 9.26594 ms
TIMER| common/global.xml: 625.654 us
SND| alc_init: success, using PulseAudio Software
TIMER| common/setup.xml: 693.601 us
TIMER| common/styles.xml: 262.054 us
TIMER| common/sprite1.xml: 2.46322 ms
TIMER| gamesetup/setup.xml: 51.309 ms
TIMER| gamesetup/sprites.xml: 335.818 us
TIMER| gamesetup/styles.xml: 386.3 us
TIMER| gamesetup/gamesetup.xml: 28.929 ms
TIMER| common/setup.xml: 2.02685 ms
TIMER| common/styles.xml: 1.01893 ms
TIMER| common/sprite1.xml: 3.26415 ms
TIMER| common/init.xml: 4.8119 ms
TIMER| loading/loading.xml: 37.0227 ms
TIMER| common/global.xml: 1.16067 ms
WARNING: TextureManager: Couldn't find terrain 
TIMER| common/setup.xml: 2.39567 ms
TIMER| common/styles.xml: 1.07544 ms
TIMER| common/sprite1.xml: 7.74303 ms
TIMER| common/icon_sprites.xml: 22.1988 ms
TIMER| session_new/sprites.xml: 61.1731 ms
TIMER| session_new/styles.xml: 693.624 us
TIMER| session_new/session.xml: 68.3231 ms
TIMER| common/global.xml: 1.02277 ms
GAME STARTED, ALL INIT COMPLETE
Compile log for shader shaders/water_high.vs (type VERTEX_SHADER):
Vertex shader was successfully compiled to run on hardware.
Compile log for shader shaders/water_high.fs (type FRAGMENT_SHADER):
Fragment shader was successfully compiled to run on hardware.Linker log for shaders/water_high.xml:
Fragment shader(s) linked, vertex shader(s) linked. 
 
ERROR: CXeromyces: Failed to find XML file audio/actor/mounted/movement/walk.xml
ERROR: Failed to load sound group 'actor/mounted/movement/walk.xml'
snd_mgr.cpp(499): Assertion failed: "0"
udbg_bfd_init: loading symbols from /usr/lib/games/0ad/system/pyrogenesis.
Assertion failed: "0"
Location: snd_mgr.cpp:499 (srcs_remove)

Call stack:

(0x824e972) none:0 std::ut_of_range::~out_of_range()
(0x8220fa8) none:0 std::ut_of_range::~out_of_range()
(0x8221dea) none:0 std::ut_of_range::~out_of_range()
(0x8221f65) none:0 std::ut_of_range::~out_of_range()
(0x8241624) none:0 std::ut_of_range::~out_of_range()
(0x8241f5d) none:0 std::ut_of_range::~out_of_range()
(0x8236e8e) none:0 std::ut_of_range::~out_of_range()
(0x8241737) none:0 std::ut_of_range::~out_of_range()
(0x8240183) none:0 std::ut_of_range::~out_of_range()
(0x8243485) none:0 std::ut_of_range::~out_of_range()
(0x8243aae) none:0 std::ut_of_range::~out_of_range()
(0x8055e8c) ./pyrogenesis:0 0x8055e8c
(0x8056155) ./pyrogenesis:0 0x8056155
(0xb06bd6) /lib/tls/i686/cmov/libc.so.6:0 __libc_start_main
(0x8055551) ./pyrogenesis:0 0x8055551

errno = 0 (?)
OS error = ?


(C)ontinue, (S)uppress, (B)reak, Launch (D)ebugger, or (E)xit?
e 
Aborted
Please help if you can.

---

### Post by DrMelon on 2010-09-11
Seems to be trying to access memory that isn't there any more. Have you checked your RAM for faults recently? That may be the issue.

---

### Post by KutViZ on 2010-09-11
I did a MemTest, zero errors. The laptop is new.

---

### Post by DrMelon on 2010-09-11
I can only assume then that the game itself is bugging out. At least in this particular case.

---

### Post by KutViZ on 2010-09-11
i'm gonna try some other games, to see if that's true.

Well, you were right. Almost all other games (Savage 2, Lugaru, MegaGlest, Americas Army, Wormux) are running well, I'll try a reinstall for the ones which are freezing.

Enemy Territory works now, UrT needed to run not from apt install, but from downloaded zip.

---

