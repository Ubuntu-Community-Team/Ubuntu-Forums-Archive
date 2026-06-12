---
title: "Rendering crashes at the end ubuntu 12.04 X64 kdenlive 0.9"
date: 2012-05-24
forum: Multimedia Software
---

### Post by Chelidze on 2012-05-24
So i am having problem with rendering files on kdenlive 0.9 when it reaches 100% suddenly rendering crashes

terminal

```
levan@Margo:~$ kdenlive
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
[mpeg @ 0x7fcfa00084a0] max_analyze_duration reached
[mpeg @ 0x7fcfa000bde0] max_analyze_duration reached
[mpeg @ 0x7fcfa000a020] max_analyze_duration reached
[mpeg @ 0x7fcfa023ca60] max_analyze_duration reached
[mpeg @ 0x7fcfa023f080] max_analyze_duration reached
[mpeg @ 0x7fcfa0240300] max_analyze_duration reached
[mpeg @ 0x7fcfa0243e60] max_analyze_duration reached
[mpeg @ 0x7fcfa0244a80] max_analyze_duration reached
[mpeg @ 0x7fcfa0776b80] max_analyze_duration reached
[mpeg @ 0x7fcfa065c300] max_analyze_duration reached
[mpeg @ 0x7fcfa065fee0] max_analyze_duration reached
[mpeg @ 0x7fcfa065dbc0] max_analyze_duration reached
[mpeg @ 0x3200be0] max_analyze_duration reached
[mpeg @ 0x31d6d20] max_analyze_duration reached
[mpeg @ 0x31c0f60] max_analyze_duration reached
[mpeg @ 0x7fcfac003100] max_analyze_duration reached
[mpeg @ 0x7fcfac003f80] max_analyze_duration reached
[mpeg @ 0x7fcfac006040] max_analyze_duration reached
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
kbuildsycoca4(2323) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(2323) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(2323) kdemain: Emitting notifyDatabaseChanged ()
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Setting new source
New source: QUrl( "file:///usr/share/sounds/KDE-Sys-Warning.ogg" )
Transitioning to state "playing"
State change
Moving from "null" 0 to "ready" 1
State change
Moving from "ready" 1 to "paused" 4
Stream changed to file:///usr/share/sounds/KDE-Sys-Warning.ogg
State change
Moving from "paused" 4 to "playing" 2
About to finish
Got next source. Waiting for end of current.
New source: QUrl( "" )
Finally got a source
About to finish
Got next source. Waiting for end of current.
New source: QUrl( "" )
Finally got a source
//STARTING RENDERING: true , false , "/usr/bin/melt" , "atsc_1080p_2997" , "avformat" , "xine" , "/tmp/kde-levan/kdenliveXF2280.mlt" , "/home/levan/kdenlive/untitled.mpg" , () , ("f=mpeg", "acodec=mp2", "ab=384k", "ar=48000", "vcodec=mpeg2video", "minrate=0", "vb=12000k", "bf=2", "b_strategy=1", "trellis=1", "aspect=@16/9", "threads=1", "real_time=-1", "s=1920x1080") , 0 , 100
Started render process: "/usr/bin/melt" "/tmp/kde-levan/kdenliveXF2280.mlt in=0 out=100 -profile atsc_1080p_2997 -consumer avformat:/home/levan/kdenlive/untitled.mpg progress=1 f=mpeg acodec=mp2 ab=384k ar=48000 vcodec=mpeg2video minrate=0 vb=12000k bf=2 b_strategy=1 trellis=1 aspect=@16/9 threads=1 real_time=-1 s=1920x1080"
Transitioning to state "ready"
State change
Moving from "playing" 2 to "paused" 4
State change
Moving from "paused" 4 to "ready" 1
"Rendering of /home/levan/kdenlive/untitled.mpg aborted, resulting video will probably be corrupted."
```

Kdenlive crash screen

```
Rendering of /home/levan/kdenlive/untitled.mpg crashed
[mpeg @ 0xaf4420] max_analyze_duration reached
[mpeg @ 0xaf7d00] max_analyze_duration reached
[mpeg @ 0xaf5dc0] max_analyze_duration reached
[mpeg @ 0x7f3890007cc0] max_analyze_duration reached
[mpeg @ 0x7f389000a3e0] max_analyze_duration reached
[mpeg @ 0x7f389000eee0] max_analyze_duration reached
[mpeg @ 0x7f389800b2a0] VBV buffer size not set, muxing may fail
```

can some one help me fix this problem

thank you for your time

---

### Post by ttguy on 2012-06-01
I don't know the fix.
This happens on 12.04 32 bit Ubuntu too with Kdenlive 0.9  and MLT 0.7.8

The rendered files seem to be fine though. 

         So based on inspiration from another thread I tried to run the melt call from the the script that kdenlive writes.


 /usr/bin/melt   /home/ttguy/Videos/scripts/test_mpg_render.sh.mlt  -profile dv_pal_wide -consumer  avformat:/home/ttguy/Videos/home_movies_vol23a-test.mpg progress=1  f=mpeg acodec=mp2 ab=384k ar=48000 vcodec=mpeg2video minrate=0 vb=12000k  bf=2 b_strategy=1 trellis=1 aspect=@16/9 threads=1 real_time=-1 
 

And it renders the video and eventually returns 
 

[dv @ 0xb5b0c320] Estimating duration from bitrate, this may be inaccurate
[mpeg @ 0xb680adc0] VBV buffer size not set, muxing may fail
Current Frame:       1011, percentage:         99
Segmentation fault (core dumped)


 So it appears a real error reported by melt

---

