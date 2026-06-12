---
title: "Broadcom 4306 firmware offline setup problems"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by ReasonablePatriot on 2013-05-13
Having issues installing b43- fwcutter. I am running Ubuntu 12.04 on my PowerBook G4 PPC. I cannot connect to Internet without setting up Broadcom 4306.  I am downloading from another machine and transferring with thumb drive.  If I can get b43-fwcutter setup I should be able to continue with instructions found on web to install Broadcom-wl-4.150.10.5. And wl-apsta-3.130.20.0.o. New to Linux and could really use some help.

---

### Post by Hadaka on 2013-05-13
Hi, please post the output of,,

Code:

lspci -n | grep 0280 

this will verify what wireless driver you need.
thanks.

---

### Post by stewnash on 2013-06-15
Having issues also,please help.

05:00.0 0280: 14e4:4320 (rev 03)

---

### Post by chili555 on 2013-06-15
Please see post #2 here; you have the same device. The corrected procedure is at post #11.

[http://ubuntuforums.org/showthread.php?t=1940540](http://ubuntuforums.org/showthread.php?t=1940540)

---

### Post by Hadaka on 2013-06-15
Hi,give this a try.. no internet required...
open a terminal..and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rfv wl
```
you may get a "not found" on that..but...its ok.
or your wired connection "may" be working now.

***If and only if your wired connection is now working**

then with the ethernet cable attached do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

**If your wired connection is not working from above commands**

then..First download the >>>>,b43.zip file attached below..
drag and drop the b43.zip to your Desktop....*note Desktop is uppercase "D"
then at the Desktop...RIGHT click the file and choose 'Extract Here' once that is done
then do..
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo modprobe b43
```

[ATTACH=CONFIG]243843[/ATTACH]


report any errors..
thanks.

---

