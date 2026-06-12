---
title: "3d not working on x700, can you help?"
date: 2006-01-12
forum: Multimedia &amp; Video
---

### Post by zasf on 2006-01-12
Hi, I have toshiba laptop with ATI X700 running ubuntu, cd install went very well, the only video issue was that during reboot or shutdown, the screen went "crazy" with some blue flashing around. 

Then I learned about ati driver **fglrx**, so I installed restricted modules and all that stuff following the wiki, then I added fglrx to /etc/modules and changed "ati" to "fglrx" in /etc/X11/xorg.conf. After reboot the screen was totally black.

Now i switched back to ati driver. The only little improve is that, with fglrx loaded in the modules file I don't get the blue flashing screen during reboot and shutdown.. but still 3d is not working.

this is what I get with fglrxinfo```

matteo@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

I also attach my xorg.conf and X log, can you please help me?

---

### Post by kakashi on 2006-01-12
i don't get it. 
you say that you don;t get blue falshing suring reboots so whats the problem

---

### Post by zasf on 2006-01-12
[QUOTE=kakashi]i don't get it. 
you say that you don;t get blue falshing suring reboots so whats the problem[/QUOTE]

The problem is that I cant load up X with fglrx, so I don't have graphics acceleration.. I load up X with ati even if fglrx module is up

Moreover if I do fglrxinfo i get an error

---

### Post by nilly on 2006-01-12
[QUOTE=zasf]The problem is that I cant load up X with fglrx, so I don't have graphics acceleration.. I load up X with ati even if fglrx module is up

Moreover if I do fglrxinfo i get an error[/QUOTE]

Sounds exaclty like my problem!!! With X800XL tough.. and non-lappy.... so some tips would help peeps.. i hope ati will get this right in the next driver version..

---

### Post by mlomker on 2006-01-13
I don't see any glaring problems in the output, but 8.16.20 was never designed to support your card...it's a lot newer than the driver is.  You could give the [latest driver]("http://ubuntuforums.org/showthread.php?t=78466") a try.

Also do a **dmesg | grep fglrx** to see if there are any errors when the driver loads.

---

### Post by nilly on 2006-01-13
[QUOTE=mlomker]I don't see any glaring problems in the output, but 8.16.20 was never designed to support your card...it's a lot newer than the driver is.  You could give the [latest driver]("http://ubuntuforums.org/showthread.php?t=78466") a try.

Also do a **dmesg | grep fglrx** to see if there are any errors when the driver loads.[/QUOTE]

Kinda hijacking the thread, but ive got same problems.. but ofcource on the latest and greates driver..

With Abit AN8 SLI Nforce4, Amd64 Dualcore 4200+, and Asus X800XL 512...

dmeg | grep fglrx with latest driver loaded but without DRI gives:

[4294704.408000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294704.410000] [fglrx] Maximum main memory to use for locked dma buffers: 1413 MBytes.
[4294704.410000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0

When DRI is activated screen gets black and ubuntu freezes..

Any tip would help us..

Any1 know when ati will drop the a new driver?? heard rumors of after christmas, but that could be next mounth or even later this summer.. hoping for better support..
//nilly

---

### Post by zasf on 2006-01-14
I got X700 to work with fglrx!!!! Thanks to mlonker's howto!!

```
matteo@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

matteo@ubuntu:~$ fgl
fgl_glxgears  fglrxconfig   fglrxinfo     fglrx_pplay   fglrx_xgamma
matteo@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2795 frames in 5.0 seconds = 559.000 FPS
4371 frames in 5.0 seconds = 874.200 FPS
4381 frames in 5.0 seconds = 876.200 FPS
4376 frames in 5.0 seconds = 875.200 FPS
4387 frames in 5.0 seconds = 877.400 FPS
4363 frames in 5.0 seconds = 872.600 FPS
matteo@ubuntu:~$
```

I need to think a bit about what I did, since the howto wasn't straightforward, then I'll post everything. Thank you all

---

### Post by ps2wayne on 2006-01-14
I am having same problem but with the 200M, if i comment out the    Load        "dri",  it will log me into X, though if its uncommented out, when X goes to load, black screen cannot do anything... i enabled ssh so I could login remotely to check things, but not really seeing any errors... i could just be over looking them.. any ideas?

---

### Post by nilly on 2006-01-14
[QUOTE=ps2wayne]I am having same problem but with the 200M, if i comment out the    Load        "dri",  it will log me into X, though if its uncommented out, when X goes to load, black screen cannot do anything... i enabled ssh so I could login remotely to check things, but not really seeing any errors... i could just be over looking them.. any ideas?[/QUOTE]

Yes its very odd.. it crashes without any error messages.. xorg.log just looks great until DRI intialized and there it just blacks out..

---

### Post by mlomker on 2006-01-15
[QUOTE=nilly]When DRI is activated screen gets black and ubuntu freezes..
[/QUOTE]

When you say 'freezes' do you mean that Ctrl-Alt-F2 won't get you to another terminal?  If so, then that tends to be a hardware problem.  I assume you've looked through /var/log/kern.log and Xorg.0.log for errors after a failed boot.

Your other questions would best be answered on the Rage3D board.

---

### Post by ps2wayne on 2006-01-15
It doesn't exactly freeze for me... because since I intall the ssh server I can ssh into my laptop from another machine, I just loose video. I am gonna start the process over and then I will put my log files / xorg file online for everybody to view and possibly help point me in the right directions.

---

### Post by nilly on 2006-01-15
[QUOTE=mlomker]When you say 'freezes' do you mean that Ctrl-Alt-F2 won't get you to another terminal?  If so, then that tends to be a hardware problem.  I assume you've looked through /var/log/kern.log and Xorg.0.log for errors after a failed boot.

Your other questions would best be answered on the Rage3D board.[/QUOTE]

Nope i cant open any new sessions.. its what i think a hard freeze.. ctrl-alt-del wont do anything.. dont know if its supposed to?? only hardware reset works.. o looked thru logs.. xorg.log and no errors there.. the file ends with DRI intialized.. havent looked in kern.log.. gonna take peek now.. havent found any answers on Rage3d either, only others with the same freeze. ati really should realese something by now..

//nilly

---

### Post by ps2wayne on 2006-01-15
My Xorg.conf - [http://geekpatrol.info/xorg.conf](http://geekpatrol.info/xorg.conf)
Xorg.0.log - [http://geekpatrol.info/Xorg.0.log](http://geekpatrol.info/Xorg.0.log) - This is during the black screen... (I copied the file when I SSH'd into the machine)
kern.log - [http://geekpatrol.info/kern.txt](http://geekpatrol.info/kern.txt) - Same thing, copied it while I was ssh'd into the machine with a blank screen.

---

### Post by mlomker on 2006-01-16
[QUOTE=ps2wayne]Same thing, copied it while I was ssh'd into the machine with a blank screen.[/QUOTE]

I don't see an obvious problem.  The big change in 8.18.x was the automatic detection of monitor resolution using plug-and-play.  I suspect a lot of these issues are related to misdetection for one reason or another.  You might want to look into the commands for disabling automatic detection and use a **modeline** to specify exactly the resolution that you want.

The only other thing that I noticed is that you're using the -386 kernel.  That shouldn't be a problem but switching to 686 or k7 (Intel or AMD) might offer you better performance in general.

---

### Post by nilly on 2006-01-16
[QUOTE=mlomker]I don't see an obvious problem.  The big change in 8.18.x was the automatic detection of monitor resolution using plug-and-play.  I suspect a lot of these issues are related to misdetection for one reason or another.  You might want to look into the commands for disabling automatic detection and use a **modeline** to specify exactly the resolution that you want.

The only other thing that I noticed is that you're using the -386 kernel.  That shouldn't be a problem but switching to 686 or k7 (Intel or AMD) might offer you better performance in general.[/QUOTE]

i tryed with a speciefied modeline, that i actually tryed and was ok with my monitor before i enabled DRI.. but as soon as DRI is enabled it goes black.. plz have a look in the thread i started, posted logs their for your pleasure :)

---

### Post by ps2wayne on 2006-01-17
Okay, I managed to get mine working... I enabled shared video memory in bios and sure enough it started working. Thanks to everybody that gave suggestions.

---

