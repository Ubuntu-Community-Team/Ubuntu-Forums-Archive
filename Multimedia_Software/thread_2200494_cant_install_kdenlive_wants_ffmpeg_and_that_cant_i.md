---
title: "cant install kdenlive? wants ffmpeg and that cant install either!"
date: 2014-01-19
forum: Multimedia Software
---

### Post by sdowney717 on 2014-01-19
what do I do?

```
ffmpeg:
 Depends: libavcodec53 but it is not going to be installed or
 	libavcodec-extra-53 (>=4:0.10.2) but 4:0.8.9ubuntu0.12.04.1 is to be installed
 Depends: libavdevice53 but it is not going to be installed or
 	libavdevice-extra-53 (>=4:0.10.2) but 4:0.8.9ubuntu0.12.04.1 is to be installed
 Depends: libavfilter2 but it is not going to be installed or
 	libavfilter-extra-2 (>=4:0.10.2) but 4:0.8.9ubuntu0.12.04.1 is to be installed
 Depends: libavformat53 but it is not going to be installed or
 	libavformat-extra-53 (>=4:0.10.2) but 4:0.8.9ubuntu0.12.04.1 is to be installed
 Depends: libavutil51 but it is not going to be installed or
 	libavutil-extra-51 (>=4:0.10.2) but 4:0.8.9ubuntu0.12.04.1 is to be installed
 Depends: libpostproc52 but it is not going to be installed or
 	libpostproc-extra-52 (>=4:0.10.2) but 4:0.8.9ubuntu0.12.04.1 is to be installed
 Depends: libswresample0 but it is not going to be installed or
 	libswresample-extra-0 (>=4:0.10.2) but it is not installable
 Depends: libswresample0 but it is not going to be installed or
 	libswresample-extra-0 (<4:0.10.2.99) but it is not installable
 Depends: libswscale2 but it is not going to be installed or
 	libswscale-extra-2 (>=4:0.10.2) but 4:0.8.9ubuntu0.12.04.1 is to be installed

```

[http://www.youtube.com/watch?v=JiTLWqImFp8](http://www.youtube.com/watch?v=JiTLWqImFp8)
using the ppa it works

---

### Post by sdowney717 on 2014-01-19
installed but kdenlive shows no clips in the timeline for any imported video.
It says it makes thumbnails but there is nothing showing.

I used to use this last install, so what is wrong?

---

### Post by sdowney717 on 2014-01-19
not easy, anyway you have to import a clip, then drag to timeline.
Then render, everytime I hit render, kdenlive crashes

```
scott@scott-P5QC:~$ kdenlive
Got bus address:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Registered DEC:  true 
project monitor connected 
clip monitor connected 
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
Can't open Jog Shuttle FILE DESCRIPTOR
Registered event listener change listener:  true 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x7f84efb85500) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0x7f84efb85500) "" 
FIXME: handle dialog start. 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
FIXME: handle dialog end. 
[mpeg @ 0x7f84a00082a0] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a0010260] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a05c1640] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a023bba0] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a0242ec0] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a07f5a40] max_analyze_duration 5000000 reached at 5016000
[mpeg2video @ 0x7f84a0243680] warning: first frame is no keyframe
[swscaler @ 0x7f84a05b3ee0] Warning: data is not aligned! This can lead to a speedloss
[mpeg2video @ 0x7f84a0243680] warning: first frame is no keyframe
FIXME: handle dialog start. 
FIXME: handle dialog end. 
kdenlive(23947) Render::checkMaxThreads: // TRACTOR PROBLEM 
[mpeg @ 0x7f84a05afe20] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a07f4e80] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a0008220] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a0235cc0] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a04f2060] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f84a04f3080] max_analyze_duration 5000000 reached at 5016000
[mpeg2video @ 0x7f84a04f12a0] warning: first frame is no keyframe
[mpeg2video @ 0x7f84a04f12a0] warning: first frame is no keyframe
KCrash: Application 'kdenlive' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/scott/.kde/socket-scott-P5QC/kdeinit4__0

[1]+  Stopped                 kdenlive
scott@scott-P5QC:~$ QSocketNotifier: Invalid socket 29 and type 'Read', disabling...
^C
[1]+  Exit 253                kdenlive
scott@scott-P5QC:~$ kdenlive
Got bus address:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Registered DEC:  true 
project monitor connected 
clip monitor connected 
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
Can't open Jog Shuttle FILE DESCRIPTOR
Registered event listener change listener:  true 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x7f63d4baf140) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0x7f63d4baf140) "" 
FIXME: handle dialog start. 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
FIXME: handle dialog end. 
[mpeg @ 0x7f637c0082a0] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f637c010260] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f637c5c1640] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f637c23bba0] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f637c242ec0] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f637c7f5a40] max_analyze_duration 5000000 reached at 5016000
[mpeg2video @ 0x7f637c243680] warning: first frame is no keyframe
[swscaler @ 0x7f637c5b3ee0] Warning: data is not aligned! This can lead to a speedloss
[mpeg2video @ 0x7f637c243680] warning: first frame is no keyframe
FIXME: handle dialog start. 
FIXME: handle dialog end. 
kdenlive(24004) Render::checkMaxThreads: // TRACTOR PROBLEM 
[mpeg @ 0x7f637c5afe20] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f637c5b2160] max_analyze_duration 5000000 reached at 5016000
[mpeg @ 0x7f637c00ef20] max_analyze_duration 5000000 reached at 5016000
KCrash: Application 'kdenlive' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/scott/.kde/socket-scott-P5QC/kdeinit4__0

[1]+  Stopped                 kdenlive
scott@scott-P5QC:~$ QSocketNotifier: Invalid socket 29 and type 'Read', disabling...
^C
[1]+  Exit 253                kdenlive
scott@scott-P5QC:~$ kdenlive
Got bus address:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Registered DEC:  true 
project monitor connected 
clip monitor connected 
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
Can't open Jog Shuttle FILE DESCRIPTOR
Registered event listener change listener:  true 
KCrash: Application 'kdenlive' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/scott/.kde/socket-scott-P5QC/kdeinit4__0

[1]+  Stopped                 kdenlive
scott@scott-P5QC:~$ kdenlive
Got bus address:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-ALsFQ0BLE6,guid=4a109d0d663e9f12799275e90000002b" 
Registered DEC:  true 
project monitor connected 
clip monitor connected 
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
Can't open Jog Shuttle FILE DESCRIPTOR
Registered event listener change listener:  true 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x7f012553af30) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0x7f012553af30) "" 
FIXME: handle dialog start. 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
FIXME: handle dialog end. 
[swscaler @ 0x7f00d435b580] Warning: data is not aligned! This can lead to a speedloss
FIXME: handle dialog start. 
FIXME: handle dialog end. 
KCrash: Application 'kdenlive' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/scott/.kde/socket-scott-P5QC/kdeinit4__0
[1]   Exit 253                kdenlive

[2]+  Stopped                 kdenlive
scott@scott-P5QC:~$ QSocketNotifier: Invalid socket 29 and type 'Read', disabling...
^C
[2]+  Exit 253                kdenlive
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2014-01-19
I installed openshot.
I am rendering, all I wanted to do was strip off 10 minutes from the end where I overshot the VHS vcr rip to mpeg2 video using VLC.

I plan to then convert to h264 using handbrake.
It looks like openshot can render h264, but I am used to handbrake.

So why is kdenlive crashing on render? Even if no clips loaded it crashes instantly.

---

### Post by sdowney717 on 2014-01-19
bug, i had 0.8.4
[http://www.kdenlive.org/mantis/view.php?id=2951](http://www.kdenlive.org/mantis/view.php?id=2951)

which links to this 'fix'
[http://www.kdenlive.org/mantis/view.php?id=2880](http://www.kdenlive.org/mantis/view.php?id=2880)

was supposed to be fixed in 0.9.4
So I did this
[http://www.noobslab.com/2013/02/kdenlive-094-for-ubuntu.html](http://www.noobslab.com/2013/02/kdenlive-094-for-ubuntu.html)

which gave me 0.9.6
and 0.9.6 also crashes!

go figure!

---

### Post by sdowney717 on 2014-01-20
[http://www.kdenlive.org/mantis/view.php?id=2662](http://www.kdenlive.org/mantis/view.php?id=2662)

clued me into the problem.
I simply deleted everything in the kdenlive script folder and now it renders with no crashing

---

### Post by FakeOutdoorsman on 2014-01-20
> **sdowney717 said:**
> I am rendering, all I wanted to do was strip off 10 minutes from the end where I overshot the VHS vcr rip to mpeg2 video using VLC.

An alternative method:
```
ffmpeg -i input -t 01:23:45 -codec copy output
```
[list]
[*]"-t" is duration time. In this example the input duration is 1 hour, 33 minutes, and 45 seconds. If you wanted to skip some of the beginning you can add the "-ss" option.
[*]"-codec copy" will tell ffmpeg to use [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) mode to remux instead of re-encode.
[/list]

---

### Post by sdowney717 on 2014-01-20
> **FakeOutdoorsman said:**
> An alternative method:
```
ffmpeg -i input -t 01:23:45 -codec copy output
```
[list]
[*]"-t" is duration time. In this example the input duration is 1 hour, 33 minutes, and 45 seconds. If you wanted to skip some of the beginning you can add the "-ss" option.
[*]"-codec copy" will tell ffmpeg to use [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) mode to remux instead of re-encode.
[/list]


I also discovered handbrake you can encode stop start times in seconds.

Also somehow VLC from commandline can set record time and stop time, but anyone know the format string for a record with number of seconds to run?

---

