---
title: "I need some help with Radeon 9200se"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by Icemanyurt on 2007-02-25
I am sorry for making yet another thread concerning ATI, but I really need some help and I have been working on this all afternoon.

I have an ATI Radeon 9200se (by MSI).  I have been trying to get 3d stuff to work, but so far no dice. 

I have run Envy, but no dice.  Any advice or tips would be great.

Here is the output for fglrxinfo

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


Attached are the outputs for dmesg and Xorg.0.log, sorry they are zipped. They are too big fo r the forum

If I need to provide more info, just let me know...

---

### Post by tgalati4 on 2007-02-25
You seem to have enough video RAM, 128 MB according to xorg.0.log.  The fglrx module recognizes the chipset but not the maker of the card and it also states that it had trouble loading the DRI (direct rendering--3D) and therefore disabled direct rendering. 

What is the framerate of:

glxgears -printfps

Did you try the generic "ati" drivers, they support the Radeon chipset pretty well.  It could the the mesa drivers are picky about the card manufacturer and take the safe road by not enabling 3D unless a known card is recognized.  This is a safety, because you really can burn up a video card if you run it in a mode that is was not designed to run.

It is also possible that MSI used an ATI chipset, but for royalty reasons disabled 3d to save money.  Of course the hardware is all there, but the firmware won't allow access to it.  Perhaps there is a firmware update that would fix it.

This is all I have to offer at this point.

Good luck

---

### Post by Icemanyurt on 2007-02-25
Under Windows, the 3d worked fine...

Here is the output for glxgears: 
> 1809 frames in 5.1 seconds = 352.106 FPS
1824 frames in 5.3 seconds = 345.531 FPS
1596 frames in 5.0 seconds = 317.165 FPS
1824 frames in 5.3 seconds = 343.394 FPS
1824 frames in 5.3 seconds = 344.401 FPS
1824 frames in 5.3 seconds = 345.641 FPS
1710 frames in 5.0 seconds = 340.191 FPS
1824 frames in 5.1 seconds = 359.783 FPS
2052 frames in 5.1 seconds = 403.042 FPS
3648 frames in 5.1 seconds = 718.651 FPS
3762 frames in 5.2 seconds = 728.984 FPS
3762 frames in 5.1 seconds = 730.807 FPS
3534 frames in 5.0 seconds = 705.691 FPS
3648 frames in 5.1 seconds = 710.066 FPS
1824 frames in 5.1 seconds = 359.025 FPS
1710 frames in 5.0 seconds = 340.611 FPS
3648 frames in 5.1 seconds = 709.912 FPS
3648 frames in 5.1 seconds = 719.121 FPS
3762 frames in 5.2 seconds = 729.275 FPS
3534 frames in 5.1 seconds = 690.864 FPS
1368 frames in 5.1 seconds = 268.225 FPS
3534 frames in 5.0 seconds = 705.651 FPS
3534 frames in 5.0 seconds = 700.643 FPS
2280 frames in 5.1 seconds = 446.795 FPS
1710 frames in 5.1 seconds = 336.506 FPS
1824 frames in 5.4 seconds = 336.663 FPS
1710 frames in 5.2 seconds = 330.024 FPS


What bugs me is that some programs worked fine up until about a week ago (planet pengiun racer, gl-117 and the like), and then after an update, just quit performing at all citing frame rate issues...

---

### Post by Del Piero on 2007-02-25
I have the same video card Radeon 9200SE (gigabyte) and i am having trouble myself been working on it since yesterday and i cant even play movies normally yet. please check this thread if you know anything about the 9200SE [http://www.ubuntuforums.org/showthread.php?t=370064](http://www.ubuntuforums.org/showthread.php?t=370064)

---

### Post by tgalati4 on 2007-02-25
I think the update may have loaded the Mesa drivers and overwrote the standard ati drivers (which support Radeon 3d modes).  There are some forum posts on how to reinstall the generic ati drivers.  It's a pain because you loose video for a while and you have to operate from the console to reinitialize video.

3d video is a moving target right now in the Ubuntu universe.  The fact that is was working previously is a good sign.  It's just a matter of effort to get back to that state.

Did you install Beryl by chance?

---

### Post by Icemanyurt on 2007-02-25
No, I am going baby step at a time...I am not even sure what Byerl is...

---

### Post by SurR3AL on 2007-03-10
check [this]("http://odintsoff.wordpress.com/2007/01/27/english-ubuntu-610-ati-radeon-xgl-beryl/") site..... :D

and btw beryl makes ur desktop look awesome! :) search youtube for beryl...

---

