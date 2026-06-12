---
title: "x 1650pro ati card"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by docdagger on 2007-07-24
I've installed this card in my PCIe slot and have modified the BIOS to use the PCIe as the default video output.  I've tried to install the latest ATI driver manually as well as using Envy to due it automatically.  The board has an existing integrated X200 ATI chipset.  This set works fine, but once I put in the other card I only get no GUI.  The errors include the following:
(WW)pglrx: no matching device section for instance (Bus PCI:1:0:0)
(WW)pglrx: no matching device section for instance (Bus PCI:1:0:1)
(EE) No devices detected
No screens found

When it tries to boot into ubuntu it always gives a failure notice for  xwindows or something to that effect.

This is also the info it gives me about the card:
1:00.0 VGA compatible controller: ATI Technology Inc RV530Ce (Rad X1600)
1:00.1 Display controller : ATI Technologies Inc Unknown Device 71e6

These are the words it put out.  I didn't capitalize all of the basic words but it what was put out.

I'm new to linux and am really lost about where to go with this.

---

### Post by overdrank on 2007-07-25
> **docdagger said:**
> I've installed this card in my PCIe slot and have modified the BIOS to use the PCIe as the default video output.  I've tried to install the latest ATI driver manually as well as using Envy to due it automatically.  The board has an existing integrated X200 ATI chipset.  This set works fine, but once I put in the other card I only get no GUI.  The errors include the following:
(WW)pglrx: no matching device section for instance (Bus PCI:1:0:0)
(WW)pglrx: no matching device section for instance (Bus PCI:1:0:1)
(EE) No devices detected
No screens found

When it tries to boot into ubuntu it always gives a failure notice for  xwindows or something to that effect.

This is also the info it gives me about the card:
1:00.0 VGA compatible controller: ATI Technology Inc RV530Ce (Rad X1600)
1:00.1 Display controller : ATI Technologies Inc Unknown Device 71e6

These are the words it put out.  I didn't capitalize all of the basic words but it what was put out.

I'm new to linux and am really lost about where to go with this.

HI if you have not solved your problem with switching your graphics card, you will get a blue screen xorg error. You can just click ok and then get to the command prompt login with user name and password. Then you this command 
```
sudo dpkg-reconfigure xserver-xorg
```
Answer some questions and if you don't know the answer leave it as the default answer given. Then reboot with the command 
```
sudo shutdown -r now
```
Then this should bring you to the desktop. Good luck!

---

