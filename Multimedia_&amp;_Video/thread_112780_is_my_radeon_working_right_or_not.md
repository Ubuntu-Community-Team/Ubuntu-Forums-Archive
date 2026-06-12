---
title: "is my radeon working right or not?"
date: 2006-01-05
forum: Multimedia &amp; Video
---

### Post by porsher_puddles on 2006-01-05
i just need to know whats going on here, i have followed the tutorials read every darn thread and i'm still none the wiser.
card is a radeon 9550
when i type fglrxinfo at the terminal i get the correct read out as it tells me in the tutorial. i now seem to have 3d acceleration although i think it could be better.
when i go to devices and check there it still says unknown ati  bla bla bla.
so is it right or not i wonder.
i'm not on the computer with the radeon video card at the moment so can't post all the read out. this ones a nvidia card no worries at all there card detected worked first go, radeon never again!

---

### Post by mcduck on 2006-01-05
if fglrxinfo says that you're using Ati drivers and not mesa your card is working right. You can try running 'glxgears -iacknowledgethatthistoolisnotabenchmark', and if you get anything around 1000 fps or more everything is fine. Ati's linux drivers just aren't that good, so you never get the same performance you get with windows drivers :/

---

### Post by DoorGunner on 2006-01-05
to know if you did it right 

$ sudo fglrxinfo 

should say ATI Radeon .....not mesa

$ glxgears -printfps
should be about 4000 to 5000 fps depending on card

$ fgl_glxgears 
should see the cube with the gears rotating.....

here are my results for a Radeon 9800 pro
john@DoorGunner:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

john@DoorGunner:~$ glxgears -printfps
25781 frames in 5.0 seconds = 5156.185 FPS
25712 frames in 5.0 seconds = 5142.385 FPS
john@DoorGunner:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
4256 frames in 5.0 seconds = 851.200 FPS
john@DoorGunner:~$


:)

---

### Post by porsher_puddles on 2006-01-05
well my cards not as good as yours i only get just over 2000 fps, but i do see the dancing gears and the cube.
so i guess its working !

---

### Post by stratotak on 2006-01-05
my laptop with go5200  only got around 1300..lol..using the nvidia drivers,,

---

### Post by DoorGunner on 2006-01-05
you bet it works.....congrats......

A radeon 9550 is a good card...... sorry my intent was to show what it might look like:D

---

### Post by porsher_puddles on 2006-01-05
[QUOTE=DoorGunner]you bet it works.....congrats......

A radeon 9550 is a good card...... sorry my intent was to show what it might look like:D[/QUOTE]
not a worry ! to tell you the truth i'm not overly impressed with the card myself, think i might stick to nvidia in future.
ty for your help

---

