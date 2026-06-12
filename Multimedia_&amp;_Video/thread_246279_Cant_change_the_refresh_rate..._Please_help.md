---
title: "Cant change the refresh rate... Please help"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by sumitsen on 2006-08-29
Hi All,

I am new to ubuntu and trying to run ubuntu 6.06 dapper properly on my laptop. Its a Toshiba A100 laptop. The configuration is :

Intel Centrino 1.6GHZ Processor
Graphics Chipset: Integrated Intel 82852/82855 GM/GME/PM/GMV
RAM: 256MB
Sound: Soundmax Integrated
Network: Intel integrated LAN.

Everything works fine except, that I cannot change the refresh rate of the screen from the screen resolution appelet.The refresh rate appears to be zero. It wont let me change it. No other thing appears.The resolution selected is 1024*768, but the refresh rate is 0. I cant change it, because of which I guess when I try to shutdown, or restart the machine, the screen becomes garbled and I cant see the normal shutdown or restart process.

In the Device Manager also the graphics chipset is detected properly.

Please help me to fix this problem.

Thanks & Regards
Sumit Sen

---

### Post by handy on 2006-08-29
Edit the **/etc/X11/xorg.conf** to reflect the correct horizontal & vertical refresh rate range for your monitor. Doing this, you won't be stuck with 60Hz refresh rate & an irritating screen, apparently Ubuntu can get this right sometimes. You can find the monitor info' on Google if you don't have the manual. I also set the screen res' to only 1024x768. If you **sudo gedit /etc/X11/xorg.conf** & have a look at the file you will see where to edit. 

***_Remember to make a copy of xorg.conf before editing it!_***

Here is a copy of the section with MY refresh rates.
==========================
Section "Monitor"
Identifier "Generic Monitor" **<-- don't edit**
Option "DPMS" **<-- don't edit**
HorizSync _30-107_ **<-- change these**
VertRefresh _48-120_ **<-- change these**
EndSection
==========================

---

### Post by sumitsen on 2006-08-30
Thanks handy for the help. That did help me solve the problem.

---

### Post by handy on 2006-08-30
Thanks for your reply!:) 

It's allways nice to know that you have helped someone... It just is! :KS

---

