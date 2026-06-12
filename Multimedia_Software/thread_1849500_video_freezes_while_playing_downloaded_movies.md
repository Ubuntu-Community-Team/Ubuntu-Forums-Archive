---
title: "video freezes while playing downloaded movies"
date: 2011-09-24
forum: Multimedia Software
---

### Post by toranaga007 on 2011-09-24
Hello community.

First time posting a help thread.
      So,  when I play my downloaded movies the video randomly freezes for 5 to 10  seconds. During this time the audio continues and then the video starts  up again in synch with the audio. The program becomes unresponsive too,  cant close it or pause it, or anything. This happens with vlc and movie  player. It seems to happen more often in fullscreen mode.  There are no  problems with streaming or watching youtube though. I am using a 32 bit  lucid 10.04 lts on a e-machines et1161-07 with NVIDIA Geforce 6150se  integrated graphics card. After installing the os I also installed all  the popular applications and software to make ubuntu work well. 
the list of installed apps and software are:
updated the software manager
*Installed the libdvdcss2 decoder
*sun java6
*vlc 1.1.4
*the restricted codecs
*flash 10 
*under the hardware drivers I selected the "NVIDIA accelerated graphics driver (version  current) [recomended]"
*the popular codecs from OMG ubuntu via the link button
*Installed Compiz Fusion (the cube works flawless plus the wobbly etc.)
*installed WINE
Hope this is enough info to help figure out what the issue might be.

P.S.  I am not up on the jargon used in ubuntu so explain things in simple  step by step methods. Hopefully this works and other noobs see the light  from this solution too. thanx

video freezes, NVIDIA Geforce 6150se, 10.04 32 bit, media, movie freezes

---

### Post by papibe on 2011-09-24
I believe that card is a bit old to support hardware acceleration. If those videos are in HD or require significant decoding, maybe your system is too slow to play them.

Could you post what codecs the video has?

In VLC you can go to Tools -> Codec Information, and paste what it says there.

Regards.

---

### Post by toranaga007 on 2011-09-24
thanx
here is the info
Stream 0
type: video
codec: xvid
resolution: 720x304
display resolution: 720x304
frame rate: 24

Stream 1
type: audio
codec: a52
channels:3f2r/LFE
sample rate: 4800hz
bitrate: 384 kb/s

pretty much all videos freeze some worse than others. Should I try downloading 700 mb movies with specific codec info. and what would the max info be to run without freezing?

---

### Post by toranaga007 on 2011-09-24
Another bit of curious info is that I had no problems playing these same movies on windows. I had the same graphics card with both OS, so doesn't that rule out the card being to old.

---

### Post by LinuxFan999 on 2011-09-24
What are the other specifications of your computer (CPU, RAM, Hard Drive)?

---

### Post by papibe on 2011-09-24
What is the output video driver on VLC?

You can change that in Tools -> Preferences -> Video -> Output. My guess it is set to default, but you may try to other values like 'X11..' or 'XVideo...'. It may be necessary restart VLC for the change to take on.

Regards.

---

### Post by toranaga007 on 2011-09-24
memory=2.8 Gib
processor=AMD Athlon x2 dual core 4050e
Available disk space=161 Gib (but I also have a 1 terabyte external)
CPU= Didnt know where to find with this os. First thought was to look in the system monitor, but doesn't give speed values.
linux kernel= 2.6.32-33-generic
GNOME 2.30.2

---

### Post by toranaga007 on 2011-09-24
ok Im trying the xvideo output. Ill let you know if it continues to freeze. thanx

---

