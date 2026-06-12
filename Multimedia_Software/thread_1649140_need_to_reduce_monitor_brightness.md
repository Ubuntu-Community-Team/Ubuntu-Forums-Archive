---
title: "need to reduce monitor brightness"
date: 2010-12-19
forum: Multimedia Software
---

### Post by senorian on 2010-12-19
Ubuntu 10.04.1
Nvidia gpu ( Asus GeForce GTS 450 Series graphic card)
dvi connection to monitor(dell 2405)
I asked on "absolute beginner" but the replies did not help
Using a vga connection I can use the buttons on the montor to control both contrast and brightness.
Using dvi there is no control(no contrast control and the brightness button changes the numbers but not the actual brightness!)
I cannot find the app that controls the Nvidia gpu
(it should exist as I found it on Zenwalk)
Thanks

EDIT

---

### Post by SeijiSensei on 2010-12-20
Did you install the proprietary Nvidia video driver using the "Additional Drivers" or "Hardware Drivers" application?  The package includes the Nvidia control application.

Others posting about this issue suggest using the "[setpci]("http://www.google.com/search?q=site%3Aubuntuforums.org+setpci")" command.  You can add it to /etc/rc.local to force it to run at boot.

---

### Post by senorian on 2010-12-21
Many thanks
No. I did not install the video drivers
Thank you for both suggestions

EDIT
there is no "hardware drivers" in "administration" in U10.04.1

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
go to
System->Administration->Hardware Drivers

---

