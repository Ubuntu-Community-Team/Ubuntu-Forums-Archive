---
title: "WNA3100 WIFI cannot install drivers"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by szechman on 2013-03-12
I can get online on my windows side only with my Netgear WNA3100 wifi stick. I have a real chicken and egg problem. I dont even know where to get started here. If someone could give me a few things to type to get some info posted that would be great.

I do not think that I have ndiswrapper installed correctly. 

I have been trying to follow the thread [http://ubuntuforums.org/showthread.php?t=1965989](http://ubuntuforums.org/showthread.php?t=1965989) but things just are not lining up.

Any help would be great.

Thanks,

Scott

---

### Post by chili555 on 2013-03-12
What things are just not lining up? Where did you get an error? What is the error? If you need to reboot to the Ubuntu side and jot the error down on paper, we need to see it before we can propose a solution.

---

### Post by carl4926 on 2013-03-12
It's quite simply not worth the messing about
These things are so cheap to get one that actually works! OOTB!
[COLOR=#333333]Belkin F5D7050[/COLOR]

---

### Post by szechman on 2013-03-12
Here is what I have done so far:

lsusb 
...
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
...

---------------------

scott@scott-Inspiron-1750:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

-----------------------

Downloaded:
 File Type: zip wna3100-drivers.zip (448.2 KB, 932 views) 

-----------------------

scott@scott-Inspiron-1750:~$ sudo modprobe ndiswrapper
[sudo] password for scott: 
FATAL: Module ndiswrapper not found.

-----------------------

scott@scott-Inspiron-1750:~$ ndiswrapper -l
bcmwlhigh5 : invalid driver!

------------------------

dmesg | grep ndis

returns nothing.

-----------------------
I am running 12.04LTS x64

---

### Post by szechman on 2013-03-12
Carl4926, If that where an option for me that is what I would have done. but thanks for the suggestion.  :)

---

### Post by chili555 on 2013-03-12
> scott@scott-Inspiron-1750:~$ sudo modprobe ndiswrapper
[sudo] password for scott:
FATAL: Module ndiswrapper not found.Let's solve this first and see if everything else falls into place. How did you install ndiswrapper? From Software Center or similar or ...? Do you have ethernet capabilities so we can try to repair this? Or is a USB key all you have?

---

### Post by szechman on 2013-03-12
I can only get online on my windows side. I do have a thumbdrive to transfer files and such. To install ndiswrapper I downloaded the following:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.57-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.57-1ubuntu1_all.deb)

Then I ran dpkg -i on the above packages.

I do have a memstick with the wbui install on it.

---

### Post by chili555 on 2013-03-12
I have no idea if those are appropriate for your installation, I somehow suspect not. What does this tell us?```
arch
lsb_release -d
```Then go here and get the Ubuntu packages for your distribution (Quantal, Precise, Hardy, etc.) and your architecture; either 32- or 64-bit: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 

I would also get ndiswrapper-dkms.

Before you install the new packages, uninstall the old:```
sudo dpkg -r ndiswrapper*
```Our near-term objective is to succeed here:```
sudo modprobe ndiswrapper
```

---

### Post by szechman on 2013-03-12
scott@scott-Inspiron-1750:~$ arch
x86_64

-----------------

scott@scott-Inspiron-1750:~$ lsb_release -d
Description:    Ubuntu 12.04.2 LTS

-----------------

scott@scott-Inspiron-1750:~$ sudo dpkg -r ndiswrapper*
[sudo] password for scott: 
(Reading database ... 253973 files and directories currently installed.)
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
dpkg: warning: while removing ndiswrapper-common, directory '/etc/ndiswrapper' not empty so not removed.
Processing triggers for man-db ...

-----------------


I installed the following packages:

dkms_2.2.0.3-1ubuntu3_all.deb
ndisgtk_0.8.5-1_amd64.deb
ndiswrapper-common_1.57-1ubuntu1_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb

Now when I run sudo modprobe ndiswrapper it just hangs. I checked the system resources and it is just locking up no cpu activity at all. I have tried removing ndiswrapper and reinstalling the above packages in an order that did not throw any dependency problems. 

Now I am stuck again.

---

### Post by chili555 on 2013-03-12
Any clues as to what went wrong here?```
cat /var/log/syslog | grep ndis
sudo dpkg -s dkms
sudo dpkg -s ndisgtk
sudo dpkg -s ndiswrapper-common
sudo dpkg -s ndiswrapper-utils
sudo dpkg -s ndiswrapper-dkms
```Hopefully, all will report: Installed OK, but one or some may not.

If syslog refers to an error and refers you to another log, look at it too and try to see what went wrong and post it here. Perhaps  /var/lib/dkms/ndiswrapper/1.57/build/make.log.

---

### Post by szechman on 2013-03-12
-
this one seems to be the problem but no idea as to how to fix it. here is what I tried:

scott@scott-Inspiron-1750:/media/9016-4EF8$ sudo dpkg -r ndiswrapper-utils
dpkg: warning: there's no installed package matching ndiswrapper-utils

scott@scott-Inspiron-1750:/media/9016-4EF8$ sudo dpkg -i ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb
(Reading database ... 254030 files and directories currently installed.)
Preparing to replace ndiswrapper-utils-1.9 1.57-1ubuntu1 (using ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb) ...
Unpacking replacement ndiswrapper-utils-1.9 ...
Setting up ndiswrapper-utils-1.9 (1.57-1ubuntu1) ...
Processing triggers for man-db ...

scott@scott-Inspiron-1750:/media/9016-4EF8$ sudo dpkg -s ndiswrapper-utils
Package `ndiswrapper-utils' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

-------------------------------------------------------

here is all the logs you asked for:

[http://pastebin.com/5kP2GeZW](http://pastebin.com/5kP2GeZW)

---

### Post by chili555 on 2013-03-12
Please try:```
sudo dpkg -s ndiswrapper-utils-1.9
```If it's installed OK, then we'll turn our attention to bcmwlhigh5.

---

### Post by szechman on 2013-03-12
yes it did install correctly. here is the log.

sudo modprobe ndiswrapper still locks up though.
-------------------------------------------------------

scott@scott-Inspiron-1750:~$ sudo dpkg -s ndiswrapper-utils-1.9
Package: ndiswrapper-utils-1.9
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 107
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ndiswrapper
Version: 1.57-1ubuntu1
Depends: libc6 (>= 2.7), ndiswrapper-common
Suggests: ndiswrapper-dkms, ndiswrapper-source
Description: Userspace utilities for the ndiswrapper Linux kernel module
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains the userspace tools. You will also need the kernel
 module package.
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by chili555 on 2013-03-12
Now let's see if we can fix the bcmwlhigh5 issue. I assume you have this file on your desktop:> Downloaded:
File Type: zip wna3100-drivers.zip (448.2 KB, 932 views)
...and that you right-clicked it and selected 'Extract Here.' Let's erase whatever is faulty:```
sudo modprobe -r ndiswrapper
```It may not be loaded; that's fine, please continue:```
sudo rm -rf /etc/ndiswrapper/*
cd Desktop/wna3100-drivers 
sudo ndiswrapper -i bcmwlhigh5.inf
```Please note and post any errors or warnings. If there are none, proceed:```
sudo modprobe ndiswrapper
```Is there life?```
iwconfig
dmesg | grep ndis
```

---

### Post by szechman on 2013-03-13
scott@scott-Inspiron-1750:~/Desktop/wna3100-drivers$ sudo modprobe -r ndiswrapper
scott@scott-Inspiron-1750:~/Desktop/wna3100-drivers$ sudo rm -rf /etc/ndiswrapper/*
scott@scott-Inspiron-1750:~/Desktop/wna3100-drivers$ sudo ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...


sudo modprobe ndiswrapper returns nothing

scott@scott-Inspiron-1750:~/Desktop/wna3100-drivers$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

scott@scott-Inspiron-1750:~/Desktop/wna3100-drivers$ dmesg | grep ndis
[  763.403017] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  763.693374] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  763.693382] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmwlhigh5'
[  763.693498] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh5'
[  763.697636] usbcore: registered new interface driver ndiswrapper
[  783.761342] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  783.761351] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmwlhigh5'
[  783.761459] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh5'


looks like i need to find 64bit drivers

---

### Post by szechman on 2013-03-13
I tried the drivers that where installed on my 64bit windows 7 side but it did not like those drivers either. Guess I need to find xp drivers. Any ideas would be great. Netgear drivers is an exe file.

---

### Post by chili555 on 2013-03-13
>  kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BHowever, the .inf file clearly says:> ;-----------------------------------------------------------------
; [COLOR="#FF0000"]x64 (AMD64, Intel EM64T) - WinXP[/COLOR]
;
[BROADCOM.NTamd64]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="#FF0000"]0846[/COLOR]&PID_[COLOR="#FF0000"]9020[/COLOR]

;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[BROADCOM]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_0846&PID_9020

Please do the following terminal command:```
sudo what the heck is wrong with you, can't you read, stupid ndiswrapper!!!
```Just kidding. Try these files. First erase the old:```
sudo ndiswrapper -e bcmwlhigh5
sudo rm -rf /etc/ndiswrapper/*
```After you've dragged and dropped the file I attached to your desktop, right-click and select 'Extract Here.' Then do:```
cd Desktop/Broadcom_bcm43xx_USB_32_64bit_v2
sudo ndiswrapper -i bcmn43xx64.inf
dmesg |grep ndis
```Any errors, warnings, smoke, sparks?? If not, then do:```
sudo modprobe ndiswrapper
iwconfig
```Any good news for old Chili??

---

### Post by szechman on 2013-03-13
SUCSESS!! I ended up starting windows xp in a VM and installed the drivers there from the exe file and then copied them from there. Thanks So much for all your help.

---

### Post by chili555 on 2013-03-13
Awesome. Glad it's working.

---

### Post by szechman on 2013-03-14
I ran into another problem. Although it works, I have to run through the entire prossess in post #14 everytime I reboot. Any Ideas?

---

### Post by chili555 on 2013-03-14
> **szechman said:**
> I ran into another problem. Although it works, I have to run through the entire prossess in post #14 everytime I reboot. Any Ideas?Reboot and try:```
sudo modprobe ndiswrapper
```Does it kick your wireless to life? If so, let's make it persistent:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```

---

### Post by szechman on 2013-03-14
that all worked great. rebooted a good dozen times. thanks for the help, again :)

---

