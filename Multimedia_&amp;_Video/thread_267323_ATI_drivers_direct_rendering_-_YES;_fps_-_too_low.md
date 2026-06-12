---
title: "ATI drivers direct rendering - YES; fps - too low"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by chelya on 2006-09-28
I have installed new ATI drivers 8.29.6, but also had this problem with the 8.28.8, but just had no time to try to solve it.

The problem is. glxinfo shows me that direct rendering is enabled:
chelya@chelya:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
........
client glx vendor string: ATI

fglrxinfo gives me correct info:
chelya@chelya:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6065 (8.29.6)

but when I'm running glxgears I get fps about 100
chelya@chelya:~$ glxgears -printfps
556 frames in 5.0 seconds = 111.130 FPS
577 frames in 5.0 seconds = 115.225 FPS
579 frames in 5.0 seconds = 115.697 FPS

or
chelya@chelya:~$ fgl_glxgears -fbo
Using GL_EXT_framebuffer_object
556 frames in 5.0 seconds = 111.200 FPS
578 frames in 5.0 seconds = 115.600 FPS
572 frames in 5.0 seconds = 114.400 FPS

PlanetPenguinRacer is also gives me about 100 fps

if I'm running fgl_glxgears without -fbo, I get
chelya@chelya:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Floating point exception

Before I installed Kubuntu and get this problem I was working in Mandriva 2006 and glxinfo there was around 3800 (don't remember for sure, but more than 3000 and less than 4000)

I have Radeon 9600 Pro and 64-bit Kubuntu installed.

Does anybody know how to solve this problem?

---

### Post by WalmartSniperLX on 2006-09-28
Hey i dont have a solution but I have the same problem (kubuntu too). I made another thread before seeing this one. Dont mind if I join you in the qwest for the answer :D ?

---

### Post by chelya on 2006-10-29
Still the same... Help someone!!! Still no actual direct rendering, despite glxinfo gives me direct "rendering: Yes"... games are not working, as xgl, compiz... just don't know what to do... Help me, please!

---

### Post by kthakore on 2006-10-29
Try the guide here and increase your 2d speed by entering that into your fglrx device section in xorg.conf 

Go here : [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#2D_speed]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#2D_speed")

---

