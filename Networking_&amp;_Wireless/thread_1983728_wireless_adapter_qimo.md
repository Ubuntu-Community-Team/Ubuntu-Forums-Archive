---
title: "wireless adapter qimo"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by willardx on 2012-05-20
hi there, i am brand new to ubuntu and am trying to set up an old pc for my kids with qimo. i love the look and feel of the os but cant get connected to my wireless network. i have tried 2 wireless adapters- edimax ew-7811un and tp link tl-wn722n and cant get either to work. its tricky to link using a wired connection due to location  and i have tried to grab the edimax linux driver to my usb drive but that isnt recognized. i cant use a cd copy of the driver cos im runnin from iso until i can sort networking. Any help would be gladly received. Thanks

---

### Post by chili555 on 2012-05-20
I believe the TPlink TL-WN722N is the best bet. I think the correct driver is built in to the latest Ubuntu version 12.04. Is that what Qimo uses? Please insert the TPlink and open a terminal and run and post:```
lsb_release -a
lsusb
```Thanks.


EDIT: Downloading Qimo now...oh what a price I pay...

---

### Post by willardx on 2012-05-20
i think qimo 2 runs on *Ubuntu* 10.04. do you think that's too old to have built in driver?

---

### Post by chili555 on 2012-05-20
> **willardx said:**
> i think qimo 2 runs on *Ubuntu* 10.04. do you think that's too old to have built in driver?According to bit-torrent, I'll know in 7 minutes, but it's helpful to find the exact identity of your USB device. How about those commands?

---

### Post by willardx on 2012-05-20
no lsb modules available. it is 10.04. the lsusb command has brought up a list but i see no tp-link

---

### Post by chili555 on 2012-05-20
> lsusb command has brought up a list but i see no tp-linkIt may be listed under an OEM name, rather than TPlink. Other than Linux hub, what else do you see? Atheros???

---

### Post by willardx on 2012-05-20
holtek semiconductor inc
an unnamed device with just id
atheros comms, inc
realtek semiconducter card reader

---

### Post by willardx on 2012-05-20
i am runnin a usb mouse/keyboard tho

---

### Post by willardx on 2012-05-20
must be the atheros then
id 0cf3:9271

---

### Post by chili555 on 2012-05-20
As I suspected, the correct driver is ath9k_htc. I'm booting into Qimo now. brb.

---

### Post by willardx on 2012-05-20
cheers very much for this

---

### Post by willardx on 2012-05-20
hi there.
i gotta get some sleep cos i got a big day at work tomorrow. please continue to look into this if you would and i'll pick it up later in the week. many thanks again.

---

### Post by chili555 on 2012-05-20
For the benefit of you and the searchers:> qimo@qimo-live:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
[COLOR="Red"]Description:	Ubuntu 10.04 LTS[/COLOR]
Release:	10.04
Codename:	lucidAlso:> qimo@qimo-live:~$ modinfo ath9k_htc
ERROR: modinfo: [COLOR="Red"]could not find module ath9k_htc[/COLOR]I suggest you look for a supported USB adapter here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

We could turn ourselves inside out trying to locate and install ath9k_htc or you could sell the two you have and get one that works out of the box.

The same situation is true of your other device which needs the twitchy rtl8192cu, if I'm not mistaken.

Qimo looks pretty fun so I'd encourage you to get it going.

---

### Post by willardx on 2012-05-20
is there another way round as im a bit reluctant to spend out £40 for an adapter? If i did an full install and burnt a cd with this linux driver from my windows system, would that work?
[http://www.edimax.co.uk/en/support_detail.php?pd_id=328&pl1_id=1&pl2_id=44](http://www.edimax.co.uk/en/support_detail.php?pd_id=328&pl1_id=1&pl2_id=44)

---

### Post by chili555 on 2012-05-20
You'd also need linux-headers matching the running kernel; 2.6.32-something as well as build-essential which is actually a meta-package of about 6-7 other things. Can it be done? Sure. Is it easy? Not at all. Will you know the meaning of "turn ourselves inside out?" Certainly. 

You'd probably have better luck with ndiswrapper and the Windows XP driver on the same page. First, boot into Qimo and open a terminal and do:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```It ought to use the CD as a software source and install them. Then move the Windows XP file you downloaded from a USB key or similar to the desktop of Qimo. Right-click and select *Extract Here*. Back in the terminal, do:```
cd Desktop/20101210_v1.08_windows/88_92CU_Driver/WinXP
sudo ndiswrapper -i net8192cu.inf
ndiswrapper -l
```It ought to report that the driver is installed and the device is present. If not, stop and post back. Now do:```
sudo modprobe ndiswrapper
iwconfig
```Is the wireless working?

EDIT: Please insert the Edimax and verify with lsusb that this is your device:> [EDIMAX150.NTx86]
%EDIMAX150.DeviceDesc% = RTL8192cu.ndi, USB\VID_[COLOR="Red"]7392[/COLOR]&PID_[COLOR="Red"]7811[/COLOR]

---

### Post by willardx on 2012-05-21
thanks very much. i will have a go at this and get back to the forum later in the week. cheers
will

---

### Post by chili555 on 2012-05-21
We'll look forward to your report. Let us know if we can help or if you get stuck.

---

### Post by neoman4426 on 2012-06-23
For anyone else planning on doing something similar, might be easier to get the latest Xubuntu (so you'll have the XFCE packages already as that is the base. will save a little bit of downloading) install the qimo-session package and setting it to auto login to that session should give pretty much the same experience with updated versions of the software and such, including the newer kernel with drivers which would have solved the OP's problem

---

