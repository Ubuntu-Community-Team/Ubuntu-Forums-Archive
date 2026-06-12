---
title: "Goodbye NVidia 8400GS PCI board, and now?"
date: 2011-12-01
forum: Multimedia Software
---

### Post by kabeza on 2011-12-01
Its very frustrating

Tried everything, added ppas, downloaded nvidia-latest, downloaded old (which used to work) drivers, v176, and prior, but couldn't make the nvidia video to work.

I have Ubuntu 10.10 because I don't want (yet) to upgrade because I have lots of stuff installed, configured, and lots of files I should move/backup.

Video is not working yet, after I:

1- uninstalled nvidia v176 driver 
2- sudo apt-get --purge remove nvidia*
3- sudo dpkg-reconfigure xserver-xorg
3- sudo shutdown -P now
4- remove pci board, nvidia 8400gs

**It is supposed the OS should use the onboard integrated graphics, right?**

I have "**Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)**"

Should I install or re-configure anything else? Thanks

---

### Post by kurt18947 on 2011-12-01
It's possible you have video conflict between Nvidia & Intel.  You may need to make changes in your BIOS settings.  I'm using an Nvidia 8400GS in this machine but I disabled any references to the AMD/ATI onboard video on this machine and asked the BIOS to use the PCIe slot for video display.  You'll have the opposite situation.  You'll want to give priority to your onboard Intel video and disable any references to PCI or PCIe video cards.  I hope this is helpful for you.

---

### Post by MoreOrLess on 2011-12-01
Make sure you don't have an /etc/X11/xorg.conf file (nvidia driver might have left it behind with explicit reference to nvidia driver).

---

### Post by MartyBuntu on 2011-12-01
> **kabeza said:**
> 
Video is not working yet,

Do you mean there's no display at all on your screen, or the Nvidia drivers don't seem to be activated?

---

### Post by kabeza on 2011-12-02
> **MartyBuntu said:**
> Do you mean there's no display at all on your screen, or the Nvidia drivers don't seem to be activated?


No display at all in my screen. In fact:

1- Plymouth displays but PC seems to freeze

2- I have to press "ESC" key while in plymouth screen so I can see a text-only login

3- startx gives "No screens found"

And finally:

I've started PC with a 11.10 liveCD and display works, correct resolution, etc. **How could I grab the xorg.conf liveCD generated? Where is it located? In Ram?**

---

### Post by kabeza on 2011-12-02
Finally solved everything by:

1- removing plymouth and leaving text-only boot

2- this xorg.conf

> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


The problem I'm having now is that compiz/3d/acceleration/etc doesn't work. Any ideas?

> 
glxinfo | grep direct
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


---

### Post by MoreOrLess on 2011-12-02
```
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
```
Log out and back in.

---

