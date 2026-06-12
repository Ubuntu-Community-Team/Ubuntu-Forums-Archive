---
title: "radeon x1100 tried everything can't add fglrx drvier"
date: 2008-09-17
forum: Multimedia Software
---

### Post by S15_88 on 2008-09-17
hi there to make a long story short i've tried everything to get my ati x1100 to work! but my graphics are garbage: maximizing a window takes several seconds of the window choppily getting larger, full screen videos flicker every second, when desktop effects are enabled desktop cube rotation is very slow and animation is almost non existent, on log in takes ages for GNOME desktop environment to initialize!

No restricted drivers either, which i know should be there for my ATI card

i've tried:
> 
  sudo dpkg-reconfigure xserver-xorg
    -made new xorg, still mesa project and horrible horrible graphics!

  completely uninstalled compiz, mesa, fglrx
    -reinstalled fglrx...fglrxinfo in terminal still displays mesa project

followed many many guides to make the ati x cards work:

did both ways instructed:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

[http://ubuntuforums.org/showthread.php?p=4727013#post4727013](http://ubuntuforums.org/showthread.php?p=4727013#post4727013)

[http://www.linuxquestions.org/questions/linux-newbie-8/desktop-effects-could-not-be-enabled-ati-radeon-xpress-1100-compiz-635139/](http://www.linuxquestions.org/questions/linux-newbie-8/desktop-effects-could-not-be-enabled-ati-radeon-xpress-1100-compiz-635139/)

[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


My goal is to get my graphics to how i had them in gutsy:

NO choppiness 

Desktop Effects enabled and controlled by Advanced Desktop Settings 

Full screen videos working flawlessly

If there is any output anyone would like to see please ask for it and i will provide here are a few things i feel will help:

> 
alain@silvia:~$ lspci -n | grep 0300
01:05.0 0300: 1002:5975

alain@silvia:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]

alain@silvia:~$ fglrxinfo
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

Thanks in Advance, Alain

---

### Post by S15_88 on 2008-09-18
update: got desktop effects working and downloaded advanced desktop effects settings to control it.  helped a little with simple tasks, was able to increase the refresh rate of the screen but for some reason things still aren't right!

maximizing a window is still laggy and full screen videos verry choppy.

still trying to understand what is happening, if this really is a driver problem or just some ridiculous chaos with my graphics card...i just don't know what to think.  again if anyone needs any terminal output or specs let me know!

thanks in advance, Alain

---

### Post by timcredible on 2008-09-18
i have an ati 1150 on my laptop, i just clicked on system->administration->hardware drivers, and enabled the ati driver, 3d, video, resolution, etc. it all works perfect.  took about a minute for it to download whatever package it needed, i rebooted, and done.  have you tried that?

---

### Post by S15_88 on 2008-09-18
yes i did some more tinkering today and i have the driver enabled in restricted drivers and it is in use but still graphics are very choppy and slow and i'm just not sure of the cause because it performs the same with no eye candy of any sort and with all of it enabled.  maximizing a window is a slow choppy process and full screen videos choppy...i just don't get it and i have tried everything...i'm stumped :(

Thanks, Alain

---

