---
title: "AMD Radeon™ HD 7970 Graphics : drivers."
date: 2012-03-04
forum: Multimedia Software
---

### Post by Abbadon1988 on 2012-03-04
Hi everybody!

I am using ubuntu 11.10 64 bits with AMD Radeon™ HD 7970 Graphics, i2600k and would like to install drivers for this graphic card in order to use pyrit with it.

I am quite new to Linux (no really used to though configuration :)) and I have already fighted hard with this brand new video card. Whatever I install I get stuck and can't start grahical interface. Here is the lace installation procedure I have followed : 

[http://www.upubuntu.com/2012/01/how-to-install-ati-amd-catalyst-121.html](http://www.upubuntu.com/2012/01/how-to-install-ati-amd-catalyst-121.html)

This was in order to install the latest propretary drivers of AMD. I have also tried to install the two driver proposed in the additional driver screen of ubuntu but the FGLRX give me a failure (error occured can't install the driver) and the other one crash when I restart.

Do you have any idea of what I should do ? And how can I rollback when I installed wrong drivers? Because at the moment I simply reinstall ubuntu^^, which is sort of overkill :p (but with an SSD and USB stick hopefully it's quite quick :p)

Thanks a lot!

Hope it was clear and have a nice day!

---

### Post by P-I H on 2012-03-04
In case I'am not using Additional Drivers, I'am using the instructions in this site to install the latest AMD proprietary driver.
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Abbadon1988 on 2012-03-04
Thansk! Do you know if it work with 7970? How can I rollback in case of problem?

EDIT : Do you know why it is necessary to build the .pkg files and it is wrong to do sh ...run with the original file?

---

### Post by Abbadon1988 on 2012-03-04
Just tyried your procedure following everything and got the following message : aticonfig: No supported adapters detected


I am quite annoyed, I know that if i restart my computer it will fail :(. 

I want to modify xorg.conf to put the minimal file but can't find it, do you know what i should do?

EDIT : I could start but i have the message amd unsupported hardware at the bottom right corner of my screen.

---

### Post by Yellow Pasque on 2012-03-04
AMD put out a special version of Catalyst:
[http://support.amd.com/us/kbarticles/Pages/catalyst121linuxdriver.aspx](http://support.amd.com/us/kbarticles/Pages/catalyst121linuxdriver.aspx)
..or you could wait for Catalyst 12-2, which should be released early this week, and see if it supports 7000-series.

---

### Post by P-I H on 2012-03-04
I bought a 6850 when it was quite new and got the issue with the message. However the card worked OK and later AMD released a driver to support Linux.

---

### Post by midden on 2012-03-08
It looks like the Catalyst 12.2 driver is out. I managed to install on Xubuntu 11.10 using some of the methods you link to above; however, it is not perfect. I still get system hangs, although not as badly as I did before the upgrade.

---

