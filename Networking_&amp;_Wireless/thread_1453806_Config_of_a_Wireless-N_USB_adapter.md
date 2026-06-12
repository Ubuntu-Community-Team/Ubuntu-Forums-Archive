---
title: "Config of a Wireless-N USB adapter"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by moonsush on 2010-04-13
Hi all. I spent $70 on a brand-new Wireless-N adapter for my Ubuntu computer in hopes that I could get it to connect to the main router in the house and get me internet access. However, the driver install CD is designed for Windows and thus will not run. I have tried to get it to set up, but it takes no action when plugged in and I am still without access to the internet.

Does anyone have any idea what I can do to get my computer connected and save me from having wasted $70?

---

### Post by chili555 on 2010-04-13
> Does anyone have any idea what I can doSure; we need information about your device. Please open a terminal and do:```
lsusb
```Post the result. Thanks.

---

### Post by moonsush on 2010-04-13
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 056a:00b5 Wacom Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the netgear one is the router port, i'm assuming.

---

### Post by chili555 on 2010-04-13
> the netgear one is the router port, i'm assuming.You mean the wireless adapter, don't you? What is the model number of this device? Is there any revision number, such as 'Model WXY, version 2'?

---

### Post by moonsush on 2010-04-13
it's a Netgear Wireless-N 150 USB adapter, model WNA1100

---

### Post by chili555 on 2010-04-13
Unless you can install the driver on a Windows machine and get the .inf and .sys files for XP, I know of no way to install your device. I am sorry I could not be of more help. Perhaps one of my learned colleagues will have an idea.

---

### Post by ryuuku11331 on 2010-05-10
i am having the same issue as the person that started this forum and i was wondering i have the .inf and .sys files from my xp install how do i get ubuntu to load my wireless adapter with this info? 

Please help i love ubuntu and dont want to have to dump it cuz of no internet!

---

### Post by pdc on 2010-05-11
[http://ubuntuforums.org/showthread.php?t=859481](http://ubuntuforums.org/showthread.php?t=859481)

try **post #8** here

.... as a guide ..

note your ID is

> 0846:9030

and post #8 had

> 0846:9000

but you have the MS CD ?

---

### Post by Slave2Metal on 2010-05-18
> **chili555 said:**
> Unless you can install the driver on a Windows machine and get the .inf and .sys files for XP, I know of no way to install your device. I am sorry I could not be of more help. Perhaps one of my learned colleagues will have an idea.

I have those files and after directing ndiswrapper to them, still nothing.  Network manager shows no "enable wireless".  The adapter's light is powered on, but buntu isn't recognizing it.

---

### Post by chili555 on 2010-05-18
What does this tell us?```
ndiswrapper -l
dmesg | grep ndis
iwconfig
```Thanks.

---

### Post by Slave2Metal on 2010-05-18
> **chili555 said:**
> What does this tell us?```
ndiswrapper -l
dmesg | grep ndis
iwconfig
```Thanks.

$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
arusb_xp : driver installed
    device (0846:9040) present

$ dmesg | grep ndis
[    9.377434] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   10.279664] ndiswrapper (load_wrap_driver:10: couldn't load driver arusb_xp; check system log for messages from 'loadndisdriver'
[   10.279760] usbcore: registered new interface driver ndiswrapper



$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by nmyrick on 2010-05-18
Return it and get this $20 adapter from WalMart. It works as soon as you plug it in. No setup or CD needed.  Unless you need the Wireless-N.

[http://www.walmart.com/catalog/product.do?product_id=10760297&findingMethod=rr](http://www.walmart.com/catalog/product.do?product_id=10760297&findingMethod=rr)

---

### Post by chili555 on 2010-05-18
> check system log for messages from 'loadndisdriver'I wonder what it says:```
sudo cat /var/log/syslog | grep loadndis
```Is there a .sys file in addition to the .inf? I wonder if it works better with the Windows 2000 driver or other than XP.

This part looks fine:> arusb_xp : driver installed
device (0846:9040) present

---

### Post by Slave2Metal on 2010-05-18
> **chili555 said:**
> I wonder what it says:```
sudo cat /var/log/syslog | grep loadndis
```Is there a .sys file in addition to the .inf? I wonder if it works better with the Windows 2000 driver or other than XP.

This part looks fine:

loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver arusb_xp

loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver arusb_xp

kernel: [  311.815593] ndiswrapper (load_wrap_driver:108): couldn't load driver arusb_xp; check system log for messages from 'loadndisdriver'

There is a .cat file, sysfile and .inf file

---

### Post by chili555 on 2010-05-18
I will have to search a bit; I'll check in tomorrow.

---

### Post by Slave2Metal on 2010-05-22
Any updates on this?

---

### Post by chili555 on 2010-05-22
Let's have a look at:```
ls /etc/ndiswrapper/arusb_xp
```Thanks.

---

### Post by Slave2Metal on 2010-05-22
$ ls /etc/ndiswrapper/arusb_xp
04BB:093F.F.conf  0846:9010.F.conf  0CF3:1001.F.conf  arusb_xp.inf
07D1:3C10.F.conf  0846:9040.F.conf  0CF3:9170.F.conf  wn111v2.sys
083A:F522.F.conf  0CDE:0023.F.conf  2019:5304.F.conf  wna1000.sys
0846:9001.F.conf  0CDE:0026.F.conf  arusb.sys         wnda31.sys

---

### Post by chili555 on 2010-05-22
While I continue my study, let me see:```
lsusb
```You can omit all the lines that are not your wireless device, if you wish.

---

### Post by Slave2Metal on 2010-05-22
Bus 001 Device 002: ID 0846:9040 NetGear Inc.

---

### Post by chili555 on 2010-05-22
> $ ls /etc/ndiswrapper/arusb_xp
04BB:093F.F.conf 0846:9010.F.conf 0CF3:1001.F.conf [COLOR="Red"]arusb_xp.inf[/COLOR]
07D1:3C10.F.conf [COLOR="Blue"]0846:9040.F.conf[/COLOR] 0CF3:9170.F.conf wn111v2.sys
083A:F522.F.conf 0CDE:0023.F.conf 2019:5304.F.conf wna1000.sys
0846:9001.F.conf 0CDE:0026.F.conf [COLOR="Red"]arusb.sys[/COLOR] wnda31.sys
I think you only need what is highlighted above. You may need the .conf files, as well, but I suspect you only need the one I highlighted. Let's try a fix. Remove your device and do:```
cd /etc/ndiswrapper/arusb_xp
sudo mv wn111v2.sys wn111v2.sys.bak
sudo mv wna1000.sys wna1000.sys.bak
sudo mv wnda31.sys wnda31.sys.bak
sudo rmmod -f ndiswrapper
```Now reinsert your device and do:```
sudo modprobe ndiswrapper
sudo iwlist wlan0 scan
```Any improvement?

---

### Post by Slave2Metal on 2010-05-22
desktop:~$ cd /etc/ndiswrapper/arusb_xp
desktop:/etc/ndiswrapper/arusb_xp$ 
desktop:/etc/ndiswrapper/arusb_xp$ sudo mv wn111v2.sys wn111v2.sys.bak
mv: cannot stat `wn111v2.sys': No such file or directory
desktop:/etc/ndiswrapper/arusb_xp$ 
desktop:/etc/ndiswrapper/arusb_xp$ sudo mv wna1000.sys wna1000.sys.bak
mv: cannot stat `wna1000.sys': No such file or directory
desktop:/etc/ndiswrapper/arusb_xp$ 
desktop:/etc/ndiswrapper/arusb_xp$ sudo mv wnda31.sys wnda31.sys.bak
mv: cannot stat `wnda31.sys': No such file or directory
desktop:/etc/ndiswrapper/arusb_xp$ 
desktop:/etc/ndiswrapper/arusb_xp$ sudo rmmod -f ndiswrapper
desktop:/etc/ndiswrapper/arusb_xp$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
desktop:/etc/ndiswrapper/arusb_xp$ 
desktop:/etc/ndiswrapper/arusb_xp$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

---

### Post by chili555 on 2010-05-22
> cannot stat `wn111v2.sys': No such file or directoryHow can that be?> $ ls /etc/ndiswrapper/arusb_xp
04BB:093F.F.conf 0846:9010.F.conf 0CF3:1001.F.conf arusb_xp.inf
07D1:3C10.F.conf 0846:9040.F.conf 0CF3:9170.F.conf [COLOR="Red"]wn111v2.sys[/COLOR]
083A:F522.F.conf 0CDE:0023.F.conf 2019:5304.F.conf wna1000.sys
0846:9001.F.conf 0CDE:0026.F.conf arusb.sys wnda31.sys^^^ There it is. Please try:```
ls -l /etc/ndiswrapper/arusb_xp
```Thanks.

---

### Post by BoneKracker on 2010-05-22
> **nmyrick said:**
> Return it and get this $18 adapter from WalMart. It works as soon as you plug it in. No setup or CD needed.  Unless you need the Wireless-N.

[http://www.walmart.com/catalog/product.do?product_id=10760297&findingMethod=rr](http://www.walmart.com/catalog/product.do?product_id=10760297&findingMethod=rr)

Wow.  Looks like something you'd find in the bottom of a Cracker Jack box.

---

### Post by Slave2Metal on 2010-05-22
$ ls -l /etc/ndiswrapper/arusb_xp
total 1884
-rw-r--r-- 1 root root    531 2010-05-19 07:57 04BB:093F.F.conf
-rw-r--r-- 1 root root    646 2010-05-19 07:57 07D1:3C10.F.conf
-rw-r--r-- 1 root root    538 2010-05-19 07:57 083A:F522.F.conf
-rw-r--r-- 1 root root    531 2010-05-19 07:57 0846:9001.F.conf
-rw-r--r-- 1 root root    543 2010-05-19 07:57 0846:9010.F.conf
-rw-r--r-- 1 root root    531 2010-05-19 07:57 0846:9040.F.conf
-rw-r--r-- 1 root root    518 2010-05-19 07:57 0CDE:0023.F.conf
-rw-r--r-- 1 root root    604 2010-05-19 07:57 0CDE:0026.F.conf
-rw-r--r-- 1 root root    538 2010-05-19 07:57 0CF3:1001.F.conf
-rw-r--r-- 1 root root    604 2010-05-19 07:57 0CF3:9170.F.conf
-rw-r--r-- 1 root root    518 2010-05-19 07:57 2019:5304.F.conf
-rw-r--r-- 1 root root 458752 2010-05-19 07:57 arusb.sys
-rw-r--r-- 1 root root  47480 2010-05-19 07:57 arusb_xp.inf
-rw-r--r-- 1 root root 458752 2010-05-19 07:57 wn111v2.sys.bak
-rw-r--r-- 1 root root 458752 2010-05-19 07:57 wna1000.sys.bak
-rw-r--r-- 1 root root 458752 2010-05-19 07:57 wnda31.sys.bak

---

### Post by chili555 on 2010-05-23
> -rw-r--r-- 1 root root 458752 2010-05-19 07:57 wn111v2.sys.bak
-rw-r--r-- 1 root root 458752 2010-05-19 07:57 wna1000.sys.bak
-rw-r--r-- 1 root root 458752 2010-05-19 07:57 wnda31.sys.bakExcellent. We have renamed the possibly irrelevant .sys files so they will not be used. Now what does this tell us?```
ndiswrapper -l
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Slave2Metal on 2010-05-23
ndiswrapper -l  driver installed

iwconfig  lo no wireless extensions
             eth0 no wireless extensions 

sudo iwlist wlan0 scan  Interface doesn't support scanning

---

### Post by moonsush on 2010-05-23
> **BoneKracker said:**
> Wow.  Looks like something you'd find in the bottom of a Cracker Jack box.

indeed. however, it might work. and i don't use my computers for gaming very much, so it might be worth a shot.

---

### Post by Slave2Metal on 2010-05-30
Fedora 13 live cd shows this adapter to use an AR9001U-2NG chipset, which has been in use for quite sometime.  I don't recall seeing this in ubuntu 10.04.

---

### Post by Slave2Metal on 2010-05-30
Hey chili555, wanted to thank you for your effort in trying to help me.  Also, big thanks go out to Indygunfreak!  Thanks for your patience.  When I get this figured out, I'll try and retrace my steps as to how I got the WNA1000 adapter to work in ubuntu 10.04.  I basically installed compat-wireless-2010-5-29 and still nothing.  So installed arusb_xp using ndiswrapper and lshw -c network shows an alternate driver(ar9170usb).  Once I modprobe ar9170usb and add it to modules list to start at boot (thanks indy), it's working.  

Isn't ndiswrapper supposed to conflict with the compat wireless driver file?  Anyway, still reluctant to think it's 100%, because I'm thinking a kernel update will undo all of the above and put me at square one.

---

### Post by chili555 on 2010-05-30
> Once I modprobe ar9170usb and add it to modules list to start at boot (thanks indy), it's working.

Isn't ndiswrapper supposed to conflict with the compat wireless driver file?Yes, it does. Once you modprobe the native driver and it works, we know that ndiswrapper is not working properly. You might as well remove it. If you are the least bit nervous, you could simply leave well enough alone.

---

### Post by chili555 on 2010-05-30
Sorry for the double post.

---

### Post by Slave2Metal on 2010-05-30
> **chili555 said:**
> Yes, it does. Once you modprobe the native driver and it works, we know that ndiswrapper is not working properly. You might as well remove it. If you are the least bit nervous, you could simply leave well enough alone.

Ok.  I will remove the windows driver and see what happens.  So, I assume after installing the latest compat, probing for the native driver was the missing step?

Oh, leaving well enough alone isn't in my nature.  My wife would tend to agree.

---

### Post by chili555 on 2010-05-30
> So, I assume after installing the latest compat, probing for the native driver was the missing step?It certainly looks like it.

---

### Post by Slave2Metal on 2010-05-30
> **chili555 said:**
> It certainly looks like it.

What are your thoughts on a kernel update?  Do you think the driver will need recompiled?  Thanks again for your help.

Yes, removing the xp driver for ndiswrapper did not undo anything.

---

### Post by chili555 on 2010-05-30
Where and how did you get compat? If you got a tar.gz and did make and make install, then you will have to recompile the driver, but with make clean, make and make install.

---

### Post by Slave2Metal on 2010-05-30
> **chili555 said:**
> Where and how did you get compat? If you got a tar.gz and did make and make install, then you will have to recompile the driver, but with make clean, make and make install.

[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

---

### Post by chili555 on 2010-05-30
> **Slave2Metal said:**
> [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)When you get a new kernel, or linux-image,  you will have to recompile the driver, but with make clean, make and make install as sudo.

---

### Post by Slave2Metal on 2010-06-04
> **chili555 said:**
> When you get a new kernel, or linux-image,  you will have to recompile the driver, but with make clean, make and make install as sudo.

What is the trick to recompiling?  I'm certain it's something simple I missed.  Ended up just downloading the most recent package and reinstalling.

---

### Post by chili555 on 2010-06-04
If you downloaded the file to, for example, Downloads, simply do, whenever a new kernel is installed:```
cd Downloads/compat-wireless-2010-05-30   [COLOR="Red"]<---or whatever your folder is named[/COLOR]
make clean
make
sudo make install
sudo modprobe ar9170usb
```You should be all set until the next kernel arrives.

---

### Post by jarl on 2010-12-16
> **Slave2Metal said:**
> $ ndiswrapper -l
$ dmesg | grep ndis
[    9.377434] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   10.279664] ndiswrapper (load_wrap_driver:10: couldn't load driver arusb_xp; check system log for messages from 'loadndisdriver'



I had a similar problem, and the reason was that I did not provide **full absolute path** when issuing the '[FONT="Courier New"]ndiswrapper -i[/FONT]' command, the man page for the ndiswrapper states explicitely that absolute paths must be provided.

Jarl

---

