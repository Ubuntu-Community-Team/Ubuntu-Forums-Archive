---
title: "TvTime works but anything else doesnt"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by fxandrei on 2007-02-03
i use ubuntu edgy 6.10
i have a pixelview play tv pro tv tuner and i wanted to record some movies from a composite input that the card has....
so i did some searching and i found tvtime...
so i installed it and entered in the application
i sellected composite2 and voila... it worked . but tvtime doesnt have the recording capability and i started searching again .. so i found mythtv,mplayer,xatv and vlc sollution ... but none of them seem to work .. ive read a couple of forums .. but somethings seems to get away from me ; dont know why it doesnt work. 
i mean. tvtime works, but how can i record movies ?! for example with xawtv . how do i use it ? (cause it seems to the most simple)
please help me.. i really need this to work

---

### Post by fxandrei on 2007-02-03
come people ...
pls
i really need help on this.
i dont know what i have to do .
i mean what i found . doesnt work

---

### Post by gmc on 2007-02-03
Hi,

What you´re looking for is mencoder (sudo apt-get install mencoder). and you can start playing with the following:

```
#!/bin/bash

OUTPUT="/home/gord/Desktop/pvr/`date +%y%m%d-%H%M.avi`"

mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1400:keyint=30 \
         -oac mp3lame -lameopts cbr:br=128:mode=3 -vop scale=528:360,pp=lb \
         -endpos 00:29:59 /dev/video1 -o $OUTPUT &

while [ ¨$(pidof mencoder)¨ != ¨¨ ]; do sync; sleep 15; done

sync

exit 0


```Gord

---

### Post by fxandrei on 2007-02-03
after i enter :

mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1400:keyint=30 \
         -oac mp3lame -lameopts cbr:br=128:mode=3 -vop scale=528:360,pp=lb \
         -endpos 00:29:59 /dev/video1 -o $OUTPUT &

i get 

fx@Xtreme:~$ MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2600+ (Family: 6, Model: 10, Stepping: 0)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
98 audio & 216 video codecs
File not found: '/dev/video1'
Failed to open /dev/video1.
Cannot open file/device.

Exiting...

so i change /dev/video1 with /dev/video0 and i get :

[2] 21819
fx@Xtreme:~$ MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2600+ (Family: 6, Model: 10, Stepping: 0)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
98 audio & 216 video codecs
success: format: 0  data: 0x0 - 0x0
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Win32 LoadLibrary failed to load: avisynth.dll, /avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed







soo ?!
what now  ?:???:

---

### Post by gmc on 2007-02-03
> **fxandrei said:**
> after i enter :

mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1400:keyint=30 \
         -oac mp3lame -lameopts cbr:br=128:mode=3 -vop scale=528:360,pp=lb \
         -endpos 00:29:59 /dev/video1 -o $OUTPUT &

i get 

fx@Xtreme:~$ MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2600+ (Family: 6, Model: 10, Stepping: 0)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
98 audio & 216 video codecs
File not found: '/dev/video1'
Failed to open /dev/video1.
Cannot open file/device.

Exiting...

so i change /dev/video1 with /dev/video0 and i get :

[2] 21819
fx@Xtreme:~$ MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2600+ (Family: 6, Model: 10, Stepping: 0)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
98 audio & 216 video codecs
success: format: 0  data: 0x0 - 0x0
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Win32 LoadLibrary failed to load: avisynth.dll, /avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed







soo ?!
what now  ?:???:

AH HA! Looks like your missing the appropriate codecs. I would suggest installing [automatix]("http://www.getautomatix.com/")
 then go to the **multimedia tab** and only check the **AUD-DVD Codecs** and **Multimedia Codecs** (you can install other stuff if you want but be sure to choose those two packages) and try that.

Gord

---

### Post by fxandrei on 2007-02-09
i used automatix for that and i still get : 


fx@89:~$ MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2600+ (Family: 6, Model: 10, Stepping: 0)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
98 audio & 216 video codecs
success: format: 0  data: 0x0 - 0x0
Cannot seek backward in linear streams!
Seek failed
Win32 LoadLibrary failed to load: avisynth.dll, /avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

[2]+  Exit 1 





xawtv doesnt work either.......


what now ?

---

### Post by bambino56 on 2007-02-11
Hello, I have the same problem, but I found a solution. I record my composite signal (input2) with this command:


mencoder tv:// -tv driver=v4l2:device=/dev/video0:input=2:width=640:height=480:alsa \
       -of avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=3500 -oac \
       mp3lame -lameopts cbr:br=128 -vf pp=lb -o test.avi -endpos 119:00


Sound is captured from sound card as line-in, not from video card.

---

