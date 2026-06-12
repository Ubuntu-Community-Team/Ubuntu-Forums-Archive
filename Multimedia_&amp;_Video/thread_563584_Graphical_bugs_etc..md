---
title: "Graphical bugs etc."
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by eZtaR on 2007-09-30
Yesterday i had a presentation to do at school  on a projector, i have a CRT/LCD-hotkey here on my laptop, but it doesn't work under ubuntu, but works at the grub screen. So i rebooted and pressed the hotkey at the grub menu, the picture showed on both projector and my laptop screen. Perfect i thought. 
Untill i got home to discover that some weirdlooking artifacts infest my screen at random times and XGL (compiz-fusion + xgl setup) took 75% CPU when viewing video in windowed mode, and utterly lagged it in fullscreen. So i did a fglrxinfo to discover that my system had reverted to the MESA driver and display read 0.0 instead of the usual 0.1.
So i thought i'd reinstall the driver. And so i did. To no prevail. So now i'm using GNOME which also has problems with artifacts, loads display 0.0 but loads the ATi driver.


Any ideas?


[pastebin of my current xorg.conf]("http://pastebin.org/3764")


(in gnome)
[PHP]eztar@eztar-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6849 Release
[/PHP]

Oh and i've tried 'sudo dpkg-reconfigure xserver-xorg' to no prevail :(


/eZtaR

---

