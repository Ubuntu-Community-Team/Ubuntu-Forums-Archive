---
title: "Screen capture with sound"
date: 2010-07-19
forum: Multimedia Software
---

### Post by xtracool_protik on 2010-07-19
So I've been trying to looks for a program which can capture my desktop with soundtrack that been played.
 I've looked upto glc-capture but it needs running program as its argument and I don't know instance name for watever happens on screen (if there is such a name)
 let me know if ffmpeg can do it - so I'll read through brief tutorial on these forums.

Thanks

---

### Post by xtracool_protik on 2010-07-21
bump..

---

### Post by xtracool_protik on 2010-07-22
I hate bumping :(
 Either its not possible or its too easy and I'm the only one who don't know how to do it. :-/

---

### Post by xtracool_protik on 2010-08-25
So instead of finding Capture with Sound. I found a way to add same sound to capture with use of mencoder command line 
I used gtk-recordmydesktop to record desktop (recorded it without sound - gnome alsa mixer - recording mute) then mencoder to convert to avi and again using mencoder added song to recording.
 mencoder worked very well i tried avidemux and few other tools but mencoder gave best result

---

### Post by williamts99 on 2010-09-20
You can record everything that comes out of the speaker using recordmydesktop.

In recordmydesktop I changed the Advanced>Sound>Device name from DEFAULT to default. (not sure if this is needed)
Then I installed pavucontrol using ```
sudo apt-get install pavucontrol
```
Run pavucontrol and go to the recording tab **while recordmydesktop is actively recording** something, you will see an item called
"ALSA plug-in[recordmydesktop]:ALSA capture from"
You must change this to Monitor of Internal Audio Analog Stereo

Best Regards,
Will

---

### Post by xtracool_protik on 2010-09-20
Thanks williamts99,
 That sounds nice will try it out sometime

---

### Post by dirghrabadia on 2010-09-20
How about this: [http://sourceforge.net/projects/xvidcap/](http://sourceforge.net/projects/xvidcap/) ?[URL="http://sourceforge.net/projects/xvidcap/"]
[/URL]

---

### Post by xtracool_protik on 2010-09-20
hmm,
 I'm not sure but I think I've tried xvidcap (not sure :confused:)
Will try again, Anyway for now I've recorded it ( check: [http://www.youtube.com/watch?v=6_1B9SGr3Ws](http://www.youtube.com/watch?v=6_1B9SGr3Ws) ) but sure these options r worth giving a try.

---

### Post by FakeOutdoorsman on 2010-09-20
This is an excellent screencasting guide using FFmpeg:

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by perspectoff on 2010-09-20
Also see a list of Screencasting programs at

[http://kubuntuguide.org/Lucid#Screencasts_and_Desktop_Recording](http://kubuntuguide.org/Lucid#Screencasts_and_Desktop_Recording)

or

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Screencasts_and_Desktop_Recording](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Screencasts_and_Desktop_Recording)

which includes a specialized howto at

[http://ubuntuguide.org/wiki/Screencasts](http://ubuntuguide.org/wiki/Screencasts)  or

[http://kubuntuguide.org/Screencasts](http://kubuntuguide.org/Screencasts)

---

