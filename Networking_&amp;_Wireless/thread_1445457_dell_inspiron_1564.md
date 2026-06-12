---
title: "dell inspiron 1564"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by pirlo89 on 2010-04-02
Hi,

I have a Dell inspiron laptop 1564 that i installed ubuntu 9.10 on. And for some reason the internet connection wont work either by a cable connection nor a wireless connection. 

Another thing is that when i inserted the live cd prior to installation, an icon appeared at the top panel saying that there are proprietary drivers that needs to be installed. But after the installation, there was no such icon.

Please help as i am sick of windows and would like to use ubuntu as soon as possible.

EDIT: the cable connection is working now.

---

### Post by chili555 on 2010-04-02
What kind of Broadcom card is in there? Please open Applications > Accessories > Terminal and do:```
lspci -nn
```Post the part that describes your wireless card. If in doubt, post it all.

If you have an ethernet connection, you could first try to go to System > Administration > Hardware Drivers and activate the proprietary drivers.

---

### Post by pirlo89 on 2010-04-02
```
pirlo@pirlo-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Arrandale DRAM Controller [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Arrandale PCI Express x16 Root Port [8086:0045] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] [1002:9552]
02:00.1 Audio device [0403]: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series] [1002:aa38]
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Device [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Device [8086:2d13] (rev 02)
pirlo@pirlo-laptop:~$ 

```

hope it helps...

---

### Post by chili555 on 2010-04-02
Walk that little Dell over to the router and hook up an ethernet cable and do:```
sudo apt-get install bcmwl-kernel-source
```After it installs, detach the cable and reboot to working wireless.> Broadcom Corporation BCM4312 802.11b/g [14e4:4315]I sorta guessed.

---

### Post by Speedcuber on 2010-04-02
> **chili555 said:**
> Walk that little Dell over to the router and hook up an ethernet cable and do:```
sudo apt-get install bcmwl-kernel-source
```After it installs, detach the cable and reboot to working wireless.I sorta guessed.


Hi, 

I have the same problem...except I do not have access to an ethernet cable. My only internet access is through Windows. Is there any way to get my wireless card working in Linux?

---

### Post by chili555 on 2010-04-02
> **Speedcuber said:**
> Hi, 

I have the same problem...except I do not have access to an ethernet cable. My only internet access is through Windows. Is there any way to get my wireless card working in Linux?Do you have the same card? > Broadcom Corporation BCM4312 802.11b/g [[COLOR="Red"]14e4:4315[/COLOR]] 

---

### Post by Speedcuber on 2010-04-02
Yes--or very similar.

---

### Post by pirlo89 on 2010-04-02
> **chili555 said:**
> Walk that little Dell over to the router and hook up an ethernet cable and do:```
sudo apt-get install bcmwl-kernel-source
```After it installs, detach the cable and reboot to working wireless.I sorta guessed.


Thanks :D, im updating my system now (its a new install so it will take a while). I'll try it out as soon as its done.
Much appreciated.

---

### Post by chili555 on 2010-04-02
> **Speedcuber said:**
> Yes--or very similar.Very similar won't do it. Please run:```
lspci -nn
```Post the pci.id for your wireless card, similar to 123a:456b. We need to know the exact numbers only if you want your card to exactly work.

---

### Post by Speedcuber on 2010-04-02
Yes, my card is identical (Broadcom Corporation BCM4312 802.11b/g [[COLOR=Red]14e4:4315[/COLOR]]).

That is what I meant--the card is the same, but the rest of the computer is similar. Sorry about that.:sad:

---

### Post by chili555 on 2010-04-02
> **Speedcuber said:**
> Yes, my card is identical (Broadcom Corporation BCM4312 802.11b/g [[COLOR=Red]14e4:4315[/COLOR]]).

That is what I meant--the card is the same, but the rest of the computer is similar. Sorry about that.:sad:Drop the install CD in the tray and do:```
sudo apt-cdrom add
sudo apt-get update
```It will complain when it can't find the on-line repositories, but it will index the CD contents as a source.```
sudo apt-get install bcmwl-kernel-source
```Reboot and enjoy.

---

### Post by bkratz on 2010-04-02
> **Speedcuber said:**
> Yes, my card is identical (Broadcom Corporation BCM4312 802.11b/g [[COLOR=Red]14e4:4315[/COLOR]]).

That is what I meant--the card is the same, but the rest of the computer is similar. Sorry about that.:sad:

Here is the original STA driver for your card

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Read the readme first and you will see yours listed with directions.


Sorry, slow typing follow Dr. Chili's suggestion first.

---

### Post by pirlo89 on 2010-04-03
Thanks for your help chili555, problem solved :p.

---

### Post by Speedcuber on 2010-04-03
> **bkratz said:**
> Here is the original STA driver for your card

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Read the readme first and you will see yours listed with directions.


Sorry, slow typing follow Dr. Chili's suggestion first.


Thanks! By following those instructions, I got my wireless network to work.

I have one problem, however: every time I reboot the computer, I have to "rmmod b43" and "rmmod ssb", then "modprobe lib80211" followed by "insmod wl.ko" before it will work. Although this is only a minor nuisance, is there a way to stop "ssb" and "b43" from loading on each reboot?  --according to the instructions, these files intefere with the new driver, but the way it said to prevent them from reloading by using blacklist does not work. Thanks!

---

### Post by bkratz on 2010-04-03
> **Speedcuber said:**
> Thanks! By following those instructions, I got my wireless network to work.

I have one problem, however: every time I reboot the computer, I have to "rmmod b43" and "rmmod ssb", then "modprobe lib80211" followed by "insmod wl.ko" before it will work. Although this is only a minor nuisance, is there a way to stop "ssb" and "b43" from loading on each reboot?  --according to the instructions, these files intefere with the new driver, but the way it said to prevent them from reloading by using blacklist does not work. Thanks!

This will probably take care of the issues.

[http://www.uluga.ubuntuforums.org/showpost.php?p=8289810&postcount=14](http://www.uluga.ubuntuforums.org/showpost.php?p=8289810&postcount=14)

and congratulations!


Here is another

[http://swiss.ubuntuforums.org/showthread.php?t=1432657](http://swiss.ubuntuforums.org/showthread.php?t=1432657)

---

### Post by ritendragoel on 2010-04-05
Last week I purchased Dell inspiron 1564 core i3,I installed 9.04 ubuntu 32 bit on my 64 bit intel processor. I am not upgrading it to 9.10 as once it will upgrade to 9.10 it starts hanging even in small application. I tried installing 9.10 32 bit and 64 bit both desktop for AMD processor but after installing successfully even. The kernel image is not loading .
So i kept my system to 9.04, but I am surprised to see that no gcc and g++ compiler is working on my laptop.. I checked the gcc and g++ version they are latest one. I installed build-essential too. After searching for suitable solution, I came to know that I should installed intel 64 bit gcc and g++ compiler for ubuntu (1GB). (it will take couple of days to download) :(

still R &D is going on. My minimum requirement is that atleast ubuntu must work on on my 64 bit intel processor with gcc and g++ compiler.
Please help me in this matter.

---

