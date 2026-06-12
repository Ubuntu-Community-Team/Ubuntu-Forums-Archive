---
title: "mythtv-setup 0.26 - no picture"
date: 2012-08-22
forum: Mythbuntu
---

### Post by jksj on 2012-08-22
I have not been able to reliably run mythtv-setup since installing mythtv 0.26 / ubuntu 12.04 on Aug 10th. The front and back ends run fine and I did not need to use setup, so it took a while before I noticed the issue, I am running :=
Ubuntu 12.04 32 bit 3.2.0-29.
Nvidia proprietary.
I have tried both Unity 3 & 2d - same result.

running either[INDENT]mythtv-setup
or
/usr/share/mythtv/mythtv-setup.sh
[/INDENT]fails to bring up the gui of mythtv-setup.
Stopping the backend and then running :-[INDENT]/usr/bin/mythtv-setup.real --syslog local7 "$@"
[/INDENT]works perfectly.
I note that the setup script has not changed since 0.25 so the issue must be related to 12.04 desktop.
I think that  the problem is that setup is failing to create an xterm and found this bug report, which may be related :-
[https://bugs.launchpad.net/mythbuntu/+bug/1038668](https://bugs.launchpad.net/mythbuntu/+bug/1038668)
The log from a failed run contains :-
```
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythtv-setup version: master [v0.26-beta-32-g7203f17] www.mythtv.org
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/tv/.mythtv
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of tv
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: I Logger logging.cpp:306 (run) Added logging to the console
```

---

### Post by tgm4883 on 2012-08-22
> **jksj said:**
> I have not been able to reliably run mythtv-setup since installing mythtv 0.26 / ubuntu 12.04 on Aug 10th. The front and back ends run fine and I did not need to use setup, so it took a while before I noticed the issue, I am running :=
Ubuntu 12.04 32 bit 3.2.0-29.
Nvidia proprietary.
I have tried both Unity 3 & 2d - same result.

running either[INDENT]mythtv-setup
or
/usr/share/mythtv/mythtv-setup.sh
[/INDENT]fails to bring up the gui of mythtv-setup.
Stopping the backend and then running :-[INDENT]/usr/bin/mythtv-setup.real --syslog local7 "$@"
[/INDENT]works perfectly.
I note that the setup script has not changed since 0.25 so the issue must be related to 12.04 desktop.
I think that  the problem is that setup is failing to create an xterm and found this bug report, which may be related :-
[https://bugs.launchpad.net/mythbuntu/+bug/1038668](https://bugs.launchpad.net/mythbuntu/+bug/1038668)
The log from a failed run contains :-
```
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythtv-setup version: master [v0.26-beta-32-g7203f17] www.mythtv.org
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/tv/.mythtv
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of tv
Aug 22 10:30:50 tv mythlogserver: mythtv-setup[5541]: I Logger logging.cpp:306 (run) Added logging to the console
```

Did you add the timezone tables to MySQL?

---

### Post by jksj on 2012-08-23
Yes the timezones are fine. Both the front and backend are working properly. Playback recording - everything. The only issue is that the 'normal' way of running set up does not work. Running mythv-setup.real works perfectly - so this issue is minor, but may put off the inexperienced user.

---

### Post by jksj on 2012-08-24
Things got worse with today's update [v0.26-beta-39-g6566c3c]. Now running the frontend from mythwelcome segfaults. Running the frontend directly works!

Can somebody please confirm that they are not experiencing these issues on a vanilla 12.04 unity 2d desktop otherwise I will have to do a clean system install.

Terminal log follows :-
```
tv@tv:~$ mythwelcome 
2012-08-24 10:27:51.110520 C  mythwelcome version: master [v0.26-beta-39-g6566c3c] www.mythtv.org
2012-08-24 10:27:51.110606 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-08-24 10:27:51.110633 N  Enabled verbose msgs:  general
2012-08-24 10:27:51.110695 N  Setting Log Level to LOG_INFO
2012-08-24 10:27:51.111779 I  Added logging to the console
2012-08-24 10:27:51.115252 I  Setup Interrupt handler
2012-08-24 10:27:51.115305 I  Setup Terminated handler
2012-08-24 10:27:51.115344 I  Setup Segmentation fault handler
2012-08-24 10:27:51.115387 I  Setup Aborted handler
2012-08-24 10:27:51.115425 I  Setup Bus error handler
2012-08-24 10:27:51.115469 I  Setup Floating point exception handler
2012-08-24 10:27:51.115515 I  Setup Illegal instruction handler
2012-08-24 10:27:51.115671 N  Using runtime prefix = /usr
2012-08-24 10:27:51.115750 N  Using configuration directory = /home/tv/.mythtv
2012-08-24 10:27:51.116153 I  Assumed character encoding: en_GB.UTF-8
2012-08-24 10:27:51.119226 N  Empty LocalHostName.
2012-08-24 10:27:51.119252 I  Using localhost value of tv
2012-08-24 10:27:51.205057 N  Setting QT default locale to EN_GB
2012-08-24 10:27:51.205288 I  Current locale EN_GB
2012-08-24 10:27:51.205506 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2012-08-24 10:27:51.233600 I  Starting process signal handler
2012-08-24 10:27:51.237410 I  Starting IO manager (write)
2012-08-24 10:27:51.237584 I  Starting process manager
2012-08-24 10:27:51.237654 I  Starting IO manager (read)
2012-08-24 10:27:51.369083 I  Added logging to mythlogserver at TCP:35327
2012-08-24 10:27:51.387452 I  ScreenSaverX11Private: DPMS is active.
2012-08-24 10:27:51.433290 N  Desktop video mode: 1920x1080 59.934 Hz
cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory
2012-08-24 10:27:51.480912 I  Loading en_us translation for module mythfrontend
2012-08-24 10:27:51.485295 N  Desktop video mode: 1920x1080 59.934 Hz
2012-08-24 10:27:51.502670 I  Trying 1920x1080 0.000 Hz
2012-08-24 10:27:51.504990 I  SwitchToGUI: Switched to 1920x1080 0.000 Hz
2012-08-24 10:27:51.522192 E  LIRC: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2012-08-24 10:27:51.522335 E  JoystickMenuThread: Joystick disabled - Failed to read /home/tv/.mythtv/joystickmenurc
2012-08-24 10:27:51.542539 E  CECAdapter: Failed to load libcec.
2012-08-24 10:27:51.636085 I  Using Frameless Window
2012-08-24 10:27:51.636201 I  Using Full Screen Window
2012-08-24 10:27:51.985903 I  Trying the OpenGL painter
2012-08-24 10:27:52.064762 I  OpenGL: Sync to VBlank is enabled (good!)
2012-08-24 10:27:52.230532 I  OpenGL1: Fragment program support available
2012-08-24 10:27:52.230810 I  OpenGL: OpenGL vendor  : NVIDIA Corporation
2012-08-24 10:27:52.230850 I  OpenGL: OpenGL renderer: ION/integrated/SSE2
2012-08-24 10:27:52.230878 I  OpenGL: OpenGL version : 3.3.0 NVIDIA 295.49
2012-08-24 10:27:52.230922 I  OpenGL: Max texture size: 8192 x 8192
2012-08-24 10:27:52.230951 I  OpenGL: Max texture units: 4
2012-08-24 10:27:52.230979 I  OpenGL: Direct rendering: Yes
2012-08-24 10:27:52.231005 I  OpenGL: PixelBufferObject support available
2012-08-24 10:27:52.231030 I  OpenGL: Initialised MythRenderOpenGL
2012-08-24 10:27:52.920096 E  MythUIHelper: LoadScaleImage(mm_prev_off.png) Unable to find image file
2012-08-24 10:27:52.920899 E  MythUIHelper: LoadScaleImage(mm_prev_on.png) Unable to find image file
2012-08-24 10:27:52.921502 E  MythUIHelper: LoadScaleImage(mm_prev_off.png) Unable to find image file
2012-08-24 10:27:52.922112 E  MythUIHelper: LoadScaleImage(mm_prev_off.png) Unable to find image file
2012-08-24 10:27:52.922654 E  MythUIHelper: LoadScaleImage(mm_prev_pushed.png) Unable to find image file
2012-08-24 10:27:52.925225 E  MythUIHelper: LoadScaleImage(mm_prev_off.png) Unable to find image file
2012-08-24 10:27:52.924760 E  MythUIHelper: LoadScaleImage(mm_next_off.png) Unable to find image file
2012-08-24 10:27:52.928482 E  MythUIHelper: LoadScaleImage(mm_next_on.png) Unable to find image file
2012-08-24 10:27:52.929042 E  MythUIHelper: LoadScaleImage(mm_next_off.png) Unable to find image file
2012-08-24 10:27:52.929562 E  MythUIHelper: LoadScaleImage(mm_next_off.png) Unable to find image file
2012-08-24 10:27:52.930394 E  MythUIHelper: LoadScaleImage(mm_next_off.png) Unable to find image file
2012-08-24 10:27:52.930850 E  MythUIHelper: LoadScaleImage(mm_next_pushed.png) Unable to find image file
2012-08-24 10:27:53.581866 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-08-24 10:27:53.585439 I  Using protocol version 75
2012-08-24 10:27:53.649974 I  Locking input devices
2012-08-24 10:27:54.936840 I  Locking input devices
2012-08-24 10:27:55.558801 N  mythshutdown --startup returned: 1
2012-08-24 10:27:55.592386 I  Locking input devices
2012-08-24 10:27:56.670058 I  Unlocking input devices
2012-08-24 10:27:56.670127 I  Unlocking input devices
2012-08-24 10:27:56.670286 I  Locking input devices
2012-08-24 10:27:57.765286 I  Unlocking input devices
2012-08-24 10:27:57.821528 I  Unlocking input devices
2012-08-24 10:28:01.006285 I  Locking input devices
2012-08-24 10:28:01.006337 I  UDPListener: Disabling
Handling Segmentation fault
Segmentation fault

```The stack trace has been submitted in
[https://bugs.launchpad.net/mythbuntu/+bug/1041152](https://bugs.launchpad.net/mythbuntu/+bug/1041152)
Launchpad seems to have lost it, I will try to submit it again tomorrow.
FWIW it was a malloc in the nvidia driver.

---

### Post by jksj on 2012-08-26
v0.26-rc-8-g3b81805 clears the problem starting mythfrontend from mythwelcome.  The problem I have with mythsetup remains.  I did a clean install on my laptop (64 bit) which showed similar faults with the previous version but is fully working with rc-8. So I must assume the fault with mythsetup is unique to my tv system, will try a full re-install.:(

---

### Post by nickrout on 2012-08-26
try clearing the cache directories in ~/.mythtv

---

### Post by jksj on 2012-08-28
Thanks for the response. I was so impressed with the responsiveness and stability of 0.26 that I am using it as my main TV, so I did not want to risk changing anything. However I have a dual boot system so I tried doing a clean install on the other partition. I installed [v0.26-rc-14-gae54e3b]. The result is identical, everything works fine apart from mythtv-setup which will not display an xterm when run from the mythbuntu shell script but runs fine as /usr/bin/mythtv-setup.real (stop the backend first).

For the benefit of anybody else trying to install 0.26, I could only get the database to connect on a bare system by:-[INDENT]Installing 0.25 
Get this running by importing a 0.25 database or using setup.
Remove 0.25 (may not be necessary)
Install 0.26 and import a 0.26 database if you have one.
[/INDENT]So keep a 0.25 database backup in case you need to do a clean install.
I suspect that there are some lurkers in there that still need the old configuration files from 0.25.

---

### Post by jksj on 2012-10-10
This issue is resolved in the current version of 0.26 - 2:0.26.0+fixes.20121009.2d2932a-0ubuntu0mythbuntu2. I believe the underlying cause to have been, the issue with config.xml not being updated to the 0.26 format as tracked in the following thread.:p

[http://www.mythtv.org/pipermail/mythtv-users/2012-October/340743.html](http://www.mythtv.org/pipermail/mythtv-users/2012-October/340743.html)

---

