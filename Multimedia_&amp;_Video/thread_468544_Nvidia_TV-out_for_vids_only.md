---
title: "Nvidia TV-out for vids only"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by Corey on 2007-06-09
I have a monitor hooked up to a vga port, and a TV hooked up to my s-video. I've messed around with a number of configurations for tv-out. They all, however, treat the TV as another monitor. I don't want this. Its not a HDTV, its not even digital, in fact its not even in good shape =), so its really useless at text rendering, reading webpages, or doing anything "desktop-oriented" with. The only reason I have it hooked up is so I can watch videos and DVDs on it. In windows I was able to get the TV to clone whatever "video overlay" there was. In other words if I opened VLC, or windows media player, whatever was shown in that window would be duplicated on the TV. Other than that the TV stayed black and didn't take up any desktop space. Is it possible to do this in linux? I only want my TV to display video overlays from totem, vlc etc.

---

### Post by kostos on 2007-06-09
If you have set TV as second monitor in X, you could start VLC or mplayer in fullscreen mode on it from your desktop using commands like 
  DISPLAY=:0.1 mplayer -fs -vf eq2  something.avi 
or 
  DISPLAY=:0.1 vlc -f --no-spdif --vout X11 --aout ALSA --no-drop-late-frames --video-on-top --aspect-ratio 4x3 --extraintf http --http-host 192.168.0.12:7373 --browse-dir /media/location

---

### Post by Corey on 2007-06-09
Its not that I can't get video on the TV. Its that I don't want the TV to work as a desktop. I don't want a big combined X surface. I don't want programs and other windows to open on the TV.

---

### Post by kostos on 2007-06-09
[I do not want it too]("http://ubuntuforums.org/showthread.php?t=468407") ](*,)

---

### Post by Corey on 2007-06-11
Kostos, LOL, i feel your pain. I find it strange that this is possible is possible in windows with the same hardware, but not in Linux. You would think defining the TV as a separate X screen would be a viable solution, but I've had no luck with that. You would also think it would be a common usage case. I mean there are still a ton more old analog sets out there than HDTVs, and most cards that have TV out are svideo. Who honestly uses analog TV as a separate desktop monitor (regardless of OS)? But i can't find any info anywhere on it. Please PM me or reply here too if you find a solution, any solution.

---

### Post by rich86 on 2007-06-13
Hi i found this command:
Option "MonitorLayout" "CRT,LFP"
Option "Clone" "true"
here [http://ubuntuforums.org/showthread.php?t=428187](http://ubuntuforums.org/showthread.php?t=428187) 
but i am trying to do the same thing, all i want is a clone of my main desktop to watch stuff on the tv which is on a wireless box to downstairs. i am sure there is a way i just don't know how to integrate it into my xorg.conf file!
any help would be greatly appreciated

EDIT: i also found this thread: [http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)

anyone any ideas how i integrate this with nvidia??

---

### Post by rich86 on 2007-06-13
ok well i found the solution that works for me, i added these to the Device section of the xorg.conf:
Option "TwinView"
Option "TwinViewOrientation" "Clone"
Option "SecondMonitorHorizSync" " 30- 50"
Option "SecondMonitorVertRefresh" "50-90"
Option "TVStandard" "PAL-I"
Option "TVOutFormat" "SVIDEO"

this worked for my nvidiaFX 5200 card. you can add options to changet he resolutions but i don;t need that. this is my source btw: [http://www.nvnews.net/vbulletin/showthread.php?t=36096](http://www.nvnews.net/vbulletin/showthread.php?t=36096)

it does mean i have lost my title bars and window borders when i use beryl, any one know a solution to this?

EDIT: my only idea is a little script to copy the relevent settings to the xorg file then restart X. i only need it for watching dvds on the tv, which isn't that common.

---

### Post by kostos on 2007-06-13
Hi Rich86, you can find a lot of useful options [here]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html") :D

But it doesn't solve the issue that nor beryl, nor X by itself not needed to read MPEG-stream from drive, decode it and send to TV-output in common case.

---

