---
title: "How can smplayer play &quot;WMV file&quot; smoothly?"
date: 2008-11-16
forum: Multimedia Software
---

### Post by mothorchid on 2008-11-16
I have a wmv file which has high quality and compression ratio. 
Here is informations of the file and my PC

[COLOR="grey"][WMV file]
166 MB, 2min 17sec, (it's a music video)
Video Codec : WMV3 / Windows Media Video 9
24bits, 1920 x 1080, 60 fps
Bit Rate : 10 Mbps
WM/ToolName : TMPGEnc 4.0 Xpress 

Audio Codec : WMA2
streo, 48 KHz
Bit Rate : 160 Kbps

[My PC]
OS : Ubuntu 8.10
CPU : AMD 64x2 Brisbane 4000+ (@2.79 GHz)
ram : 2 GB
Video : ATI X1250 
Totem : v2.24.3 
   (at "multi media selector" auto. i think it use hardware acceleration)
smplayer : v0.6.1 (mplayer 1.0rc2) 
    output driver : xv, checked allow frame drop[/COLOR]

When I play it on Totem Player, it's good, perfect performance. 
On MS Windows application, this file played well. not a file defect.
but on smplayer, it's almost impossible to see.
Video goes on playing for 1~2 seconds and stopping for 1~2 seconds 
while audio is playing smoothly.of course, They are not synchronized.

Other media files do not consume cpu resources that much on smplayer. 
Most AVC media files play well on smplayer, but only this file don't.
System monitoring panel tells totem use both of dual-core, and 
smplayer do only one of them. it use core#1 100% and core#2 less than 10%.

I think If smplayer use both of dual-core, maybe this problem will 
be solved. 

or Maybe codec problem??
Smplayer use 'asf-ASF demuxer(ASF, WMV, WMA)' as demutiplexer, 
'ffwmv3 - FFmpeg M$ WMV3/WMV9 [wmv3]' as video codec, and
'ffwmav2 - DivX audio v2 (ffmpeg) [wmav2]' as audio codec.

one solution is just using totem player. but I prefer smplayer.
How can i play this file on smplayer smoothly?? 
I need Some Advises. Help me please~

---

### Post by rvm4000 on 2008-11-16
Have you tried to play the file directly with mplayer?

If it plays it smoothly then it would be possible to do it in smplayer too, maybe disabling some options.

But if it can't play the file smoothly then maybe you can try to update mplayer.

---

### Post by mothorchid on 2008-11-28
thank you for your advice. 
I tried with mplayer.mplayer give the error messages continuously.
"Too many video packets in the buffer : (419 in 8395333)"
(numerical values are various.)
I'll sent you a private message. please read it.

---

