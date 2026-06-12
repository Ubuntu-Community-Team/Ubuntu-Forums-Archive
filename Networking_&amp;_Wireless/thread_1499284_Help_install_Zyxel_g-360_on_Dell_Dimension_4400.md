---
title: "Help install Zyxel g-360 on Dell Dimension 4400"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by daphnia on 2010-06-01
I picked up the computer for free (Dell P4 with no HD), stuck in a hard drive I had laying around and installed Ubuntu Studio 10.04 yesterday.  I am completely clueless about how to do anything with Linux.

I put in a Zyxel g-360 wireless pci card, and found the ACX111 driver online.  I found the wiki here: [ttp://acx100.sourceforge.net/wiki/ACX](ttp://acx100.sourceforge.net/wiki/ACX) 
Are those installation instructions?  I can't understand what it says. :confused:

I have the Zyxel installation disk for Windows XP if that helps.

I need step by step instructions, please.  Absolute complete pure green newbie here.

---

### Post by daphnia on 2010-06-03
Ok, somehow I found a way to list drivers that came with Ubuntu and the ACX111 is listed there.  So how do I get it to see that the card is in the computer?  Do I need to reinstall Ubuntu?  Would that work?  It took a few hours to install Ubuntu, so I hope there is an easier way.

---

### Post by chili555 on 2010-06-03
If you found it on your 10.04 installation, you found something my install doesn't have. *acx.ko* was dropped after kernel version 2.6.31 because it's buggy and simply doesn't work very well. I discourage you from downloading it and installing it anyway. 

Until *acx.ko* is competently rewritten, I think ndiswrapper and the Windows driver is the only reasonable solution. Do you have the driver CD that came with the device?

---

### Post by daphnia on 2010-06-03
Yes, I have the windows driver for the card.  What is ndiswrapper?  Where do I get it and what do I do with it?

---

### Post by chili555 on 2010-06-03
Do you have System > Administration > Windows Wireless Drivers? If so, you have nearly everything you need. Drag and drop the files from the CD to your desktop. Is one of the files a zip file? Right-click it and select Extract Here. A folder will be created, G-360-something and within that a folder called Driver. Open System > Administration > Windows Wireless Drivers and click Install and point it to the tnet1130.INF files you found.

Here is an explanation of ndiswrapper, although the method of installation is outdated compared to what you have.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by daphnia on 2010-06-03
I didn't have the "Windows Wireless Drivers" so I found out how to  downloaded and install it.  It asks for an .inf file to install, but the  only .inf on the Zyxel CD is autorun.inf.  Other than that there is  only setup.exe.  So I looked for another version online.

The only  .inf file that comes with the online driver is net5513.inf.  I tried to  install it with that Wireless Network Drivers, but nothing happened.   It doesn't go into the "Currently Installed Windows Drivers" list.

---

### Post by chili555 on 2010-06-03
Perhaps this will help. Please download the attached and proceed as above.

---

### Post by daphnia on 2010-06-03
Thanks, but still nothing happens when I tell it to install that .inf file.

---

### Post by chili555 on 2010-06-03
Please post:```
ndiswrapper -l
iwconfig
```I would also like to see the part of this that relates to your wireless:```
lspci -nn
```Thanks.

---

### Post by daphnia on 2010-06-03
when I put in ndiswrapper -1, I get "Error: no ndiswrapper utils found!"  But i did install the utils.

iwconfig:
lo          no wireless extensions.
eth0      no wireless extensions.

lspci -nn:  
02:0c.0 Network controller [0280]: Texas Instruments ACX 111 54 Mbps Wireless Interface [104c:9066]

---

### Post by chili555 on 2010-06-03
> 02:0c.0 Network controller [0280]: Texas Instruments ACX 111 54 Mbps Wireless Interface [[COLOR="Red"]104c:9066[/COLOR]]
And this is from tnet1130.INF:> ;For WinXP

[TexasInstruments.NT.5.1]

%TIACX.DeviceDesc% = TIACXXP, PCI\VEN_104C&DEV_9066&SUBSYS_003217CF	; Cardbus

%TIACX1.DeviceDesc% = TIACXXP, PCI\VEN_[COLOR="Red"]104C[/COLOR]&DEV_[COLOR="Red"]9066[/COLOR]&SUBSYS_161216A5	; PCIIt is evidently the correct .inf for the device.

Please open System > Administration > Synaptic and be sure that ndiswrapper-utils-1.9, ndiswrapper-common and ndisgtk are installed. If you have, or can get an ethernet connection, install them if they are not. Then try again.

---

### Post by daphnia on 2010-06-04
They are in the list of packages installed.  But it's still not working.

---

### Post by chili555 on 2010-06-04
Quite often, a program run in a terminal will give off error or warning messages that are simply not available in a GUI. Please open Applications > Accessories > Terminal and do:```
cd Desktop/Driver
ndiswrapper -i tnet1130.INF
```Note any error or warning messages and post them here. If there are none. please post:```
ndiswrapper -l
```> ndiswrapper -1Ah, ha! I see now. It's not ndiswrapper -1 (one) it's ndiswrapper -l (L for 'list'). 

Please let us know how it goes.

---

### Post by daphnia on 2010-06-04
It's the same error with -l.  Everytime I try to call on ndiswrapper or ndisgtk I get the error, "no ndiswrapper utils found!"  I tried to install the utils again but it didn't make any difference.

Thank you so much for having patience and helping me out!  I really appreciate it.  I just hope that using Linux doesn't continue to be such a struggle.  Nothing has gone smoothly yet.

---

### Post by chili555 on 2010-06-04
If you have an internet connection, please do:```
sudo apt-get remove --purge ndis*
sudo apt-get install ndisgtk
```Installing ndisgtk will pull in any other dependencies. Then try again to open System > Administration > Windows Wireless Drivers and click Install and point it to the tnet1130.INF files you downloaded.

---

### Post by daphnia on 2010-06-04
no internet access on that computer.  I just uninstalled ndiswrapper with Synaptic, downloaded it from a different source in case there were corrupt files.  On re-installing I get:

> make -C driver
make[1]: Entering directory '/home/user/ndiswrapper-1.56/driver'
Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.32-21-generic/build, is it configured?. Stop.
make[1]: Leaving directory '/home/user/ndiswrapper-1.56/driver' 
make: *** [all] Error 2

---

### Post by chili555 on 2010-06-04
Do you still have the install CD? I think ndiswrapper is on it. You can enable the CD under Synaptic > Settings > Repositories and install ndiswrapper. I am not sure about ndisgtk; you may have to install the .inf the long way as in the link I provided above.

---

### Post by daphnia on 2010-06-06
I've had enough.  I've spent too many hours trying to figure this out.   Ubuntu Studio is just not the least bit new user friendly.  I will try a  different version of Ubuntu.

Thanks for trying to help me!

---

