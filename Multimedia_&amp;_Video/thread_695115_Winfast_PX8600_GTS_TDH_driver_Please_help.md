---
title: "Winfast PX8600 GTS TDH driver Please help"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by zacorbul on 2008-02-12
Hello all,
Can anybody point me in the right direction pls as I'm going crazy here.
I need the driver for a Winfast PX8600 GTS TDH. Works fine on windows but I can't find drivers for linux...
I saw something about the driver being included in Nvidia Forceware release 169 (Dunno what is this suposed to be do Leadtek belong to Nvidia ?!) but even this is just for windows.
 I am a newbie regarding Linux, I've tried it before but every time i bump into this graphic driver bussiness...
I tried to install a Nvidia driver for geforce 8600 (I realised now that it was silly) and it killed the xorg and now I don't get any GUI. Funny thing, when I installed Gutsy, the display was fine, i killed it and I tried to switch back to the previous (the installed version) driver using :
sudo dpkg-reconfigure xserver-xorg
but it didn't do much so still no GUI :(

If anybody can help me, I would be very gratefull.....

Why don't they make drivers for linux as well ?! Surely it can't be that hard....

---

### Post by overdrank on 2008-02-12
> **zacorbul said:**
> Hello all,
Can anybody point me in the right direction pls as I'm going crazy here.
I need the driver for a Winfast PX8600 GTS TDH. Works fine on windows but I can't find drivers for linux...
I saw something about the driver being included in Nvidia Forceware release 169 (Dunno what is this suposed to be do Leadtek belong to Nvidia ?!) but even this is just for windows.
 I am a newbie regarding Linux, I've tried it before but every time i bump into this graphic driver bussiness...
I tried to install a Nvidia driver for geforce 8600 (I realised now that it was silly) and it killed the xorg and now I don't get any GUI. Funny thing, when I installed Gutsy, the display was fine, i killed it and I tried to switch back to the previous (the installed version) driver using :
sudo dpkg-reconfigure xserver-xorg
but it didn't do much so still no GUI :(

If anybody can help me, I would be very gratefull.....

Why don't they make drivers for linux as well ?! Surely it can't be that hard....

HI and you can try to reconfigure from recovery mode, which is the usually the second choice at the grub. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by zacorbul on 2008-02-13
Thank you, I'll try that now.

---

### Post by x-dragon on 2008-02-13
When you have your GUI back, install the following programm, 'ENVY' it helped me uninstall unneeded drivers and install the correct ones. If you don't succeed in getting ur GUI back, still download envy and run it with envy -t (text based menu)
Link : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by zacorbul on 2008-02-13
Thank you, I got my GUI back. I tried Envy, unfortunately it doesn't work and it messed up my GUIagain. Luckily the command you told me did the trick and got the GUI back. I guess the Nvidia drivers don't work on WinFast. I'll wait maybe (a long shot maybe) the Leadtek people will do a linux driver.
Thank you overdrank.

---

### Post by zacorbul on 2008-02-13
Thank you x-dragon, but Envy didn't work for me.

---

### Post by overdrank on 2008-02-13
> **zacorbul said:**
> Thank you x-dragon, but Envy didn't work for me.

HI and after using Envy you may still have to reconfigure your xorg. :)

---

### Post by zacorbul on 2008-02-13
> **overdrank said:**
> HI and after using Envy you may still have to reconfigure your xorg. :)
What do you mean by reconfiguring ?

---

### Post by overdrank on 2008-02-13
> **zacorbul said:**
> What do you mean by reconfiguring ?

The command I posted previously. That will reconfigure you xorg after Envy installs the drivers for you graphics card.

---

### Post by zacorbul on 2008-02-13
I install the envy driver and do I use your command before or after the reboot ?
Sorry for asking silly questions but i am quite new at this...

---

### Post by zacorbul on 2008-04-24
Right...since Feb I kept on looking for a linux driver for the blasted card... to no avail.

I hope someone shoots the Leadtek's idiotic manager who decided that they'll only make drivers for windows. 
There is a lesson to learn here, always, always check for drivers availability....oh and also 


DON'T BUY Leadtek!!!!!!!

---

