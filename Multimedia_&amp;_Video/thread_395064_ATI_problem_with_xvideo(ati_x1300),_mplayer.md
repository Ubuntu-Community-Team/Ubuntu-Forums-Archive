---
title: "ATI problem with xvideo(ati x1300), mplayer"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Pett on 2007-03-27
I know this problem has been discussed several times before, but none of them  gave me answer to this issue.. I have the latest ATI drivers (8.34.8), and as I read in release notes the problem with xvideo has been solved. So I would expect mplayer to work without problems with xvideo but apparently it's not. I can play videos using -vo gl or -vo gl2, but video is in very slow motion. But I'm newbie in linux so it's quite possible I'm doing something wrong. I have ATI mobility radeon x1300 and mplayer gives me an error:
```
It seems there is no Xvideo support for your video card available...
```
xvinfo gives me:
```
pett@pett-ntbk:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```
fglrxinfo gives me:
```
pett@pett-ntbk:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```
I'd be very thankful for any help..

---

### Post by Pett on 2007-03-28
bump.. please

---

### Post by Pett on 2007-03-28
Problem solved!!!!

Thanks to the creator of envy!!

Envy can be downloaded from here..

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

