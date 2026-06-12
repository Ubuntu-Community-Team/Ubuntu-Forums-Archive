---
title: "Totem fullscreen: no antialiasing"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by [CPR]-AL.exe on 2007-09-18
I've read a lot of thread about problems quite similar to mine, but no one helped me to resolve it.

I can watch video only with totem (gstreamer). Xine totem doesn't work for me. Kaffeine just crashes, outputing that it cannot initialize video output device, mplayer works, but in the fullscreen mode video remains the same size (just blackness around the video in it's original size).

I'm satisfied with totem and i don't ask to help me with kaffeine or mplayer... but there's only one irrirating thing in Totem: there is no any type of antialiasing in the fullscreen mode. Video just scales o the screen, but it's pixelated... 

Maybe, that's the only thing that keeps windows on my hard drive in the separate partition: i can't watch fullscreen video normally :(

---

### Post by [CPR]-AL.exe on 2007-09-19
bump up ^

Please, help me :( I'm totally noob to Linux...

---

### Post by eye208 on 2007-09-19
If you are using an ATI video card and ATI's accelerated driver, you need to enable the XVideo extension by entering

sudo aticonfig --ovt Xv

into a terminal window. This needs to be done only once. The changes will be applied the next time you start up the desktop.

This will also make all the other players work normally.

---

### Post by [CPR]-AL.exe on 2007-09-19
Wow, thank you very much! That worked for normal fullscreen in totem and mplayer :) Kaffeine still doesn't work, but i'm not too worried about it :)

Thanks again :)

---

### Post by eye208 on 2007-09-19
If you are looking for a third option besides Totem and MPlayer, try VLC.

---

### Post by iczman on 2007-09-29
I also have the same problem, but I'm using Intel 945GM and another computer using GeForce 8800GTS. Does anyone know the solution for both Intel and Nvidia video cards?

---

### Post by gp95ac on 2007-10-28
Bump, same problem with nvidia, pixelated fullscreen :(

---

### Post by gp95ac on 2007-10-31
Still my only complaint with Gusty so far, never had this problem with Fiesty and dont want to go back for movies and lose compiz (not the prob btw, happens in metacity too).

Am I stuck booting with the live Fiesty CD to watch fullscreen movies, or is there gonna be a patch for these obvious video driver issues?

---

### Post by gp95ac on 2008-02-23
Wow, 4 months and no ideas/patches....how about this work around, save yourself a vesa driven xorg and use that when you want to watch a full screen movie....no compositing, but minimal pixelation.

---

### Post by xtimesninety on 2008-05-01
this also happens on my laptop, which has Intel 945GM. video works fine, but becomes pixelated on fullscreen. I tried it on VLC. Also, when you zoom a website on Firefox 3, images scale but doesn't use antialiasing (pixelated)

---

