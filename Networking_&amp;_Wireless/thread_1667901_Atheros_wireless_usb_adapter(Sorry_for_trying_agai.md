---
title: "Atheros wireless usb adapter(Sorry for trying again )"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by raac on 2011-01-15
I can't post messages, I think something is wring with my internet.

Anyway, I'm gonna copy paste what I've been trying to say...

Hi guys, I just bought the TP-LINK Model No. TL-WN821N. It's an atheros. And I was wondering where can I find the drivers for Linux. It only includes drivers for Windows.

I don't have much experience with networks, but I would appreciate your help guys


I found this website, if someone think I'm looking at the wrong website let me know. 

[http://en.gentoo-wiki.com/wiki/TL-WN821N#Introduction](http://en.gentoo-wiki.com/wiki/TL-WN821N#Introduction)

I got stuck in the patch section, I don't know what they are trying to say. 

They are using 

diff -urp compat-wireless-2009-02-22_AR9170_230209/drivers/net/b44.c compat-wireless-2009-02-22_AR9170_230209/drivers/net/b44.c

They are comparing the same file, there is some code they are showing but I don't know what they want me to do.

Please help

---

### Post by solar george on 2011-01-15
The page you link to looks rather outdated since it refers to kernel 2.6.30 (maverick is on .35) and tbh you're not going to have much luck following a gentoo howto on ubuntu. Gentoo is compiled from source whereas ubuntu provides precompiled packages which is less work for you but makes most gentoo howto's almost entirely useless for us.
I take it you've tried just plugging the adapter into your computer? You might be supprised how many drivers are included by default.

If not you can try installing some updated drivers using then [linux-backports-modules-wireless-maverick-generic]("apt://linux-backports-modules-wireless-maverick-generic") package.

btw. the forums seem to be a little overloaded these past few days which may be why you're having trouble posting.

---

### Post by raac on 2011-01-15
Well, if I have one chip already working on my laptop, how can I know if it works or not. It did came with a CD, but it only contains drivers for Windows7,Vista, XP, and 2000. But not for linux.

---

### Post by solar george on 2011-01-15
If if works clicking on the network manager applet in the panel will show two lists of available wireless networks (one from the internal chip and one from the usb adapter).

In my previous post I wasn't refering any drivers on the cd the adapter came with, I was refering to drivers installed by default. 

If the adapter doesn't work straight away try clicking the package name link in my previous post to install and package which provides updated wireless drivers (its an official package from the official repos btw.)

---

### Post by raac on 2011-01-15
I installed it, but I clicked on the panel where all the routers are displayed and it only shows one list. So, I guessed it did not work

---

### Post by solar george on 2011-01-15
In that case could you open a terminal and copy and past here the output from;
```
dmesg|tail
lsusb
```
immediately after you've plugged the adapter in.

---

### Post by raac on 2011-01-15
>dmesg|tail


[ 9656.575700] usb 2-4: ath9k_htc: Firmware - ar7010_1_1.fw not found
[ 9656.575714] ath9k_hif_usb: probe of 2-4:1.0 failed with error -22
[ 9656.576371] usbcore: registered new interface driver ath9k_hif_usb
[ 9656.608530] cfg80211: World regulatory domain updated:
[ 9656.608534]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 9656.608538]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9656.608541]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9656.608544]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9656.608547]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9656.608550]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


> lsusb

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0cf3:7015 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by solar george on 2011-01-15
I think all you need to do is run the hardware drivers / restricted drivers manager from the system menu and activate any wireless driver you see (which tbh I should've thought of several posts ago).

---

### Post by raac on 2011-01-15
I'm attaching some screenshots. I do want to mention that the chipset my laptop has is a Broadcom. These are the two options drivers manager gives me

---

### Post by solar george on 2011-01-15
Hmm seems to be no firmware package for it right now. . .
Try downloading [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar7010_1_1.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar7010_1_1.fw;hb=HEAD) (save as ar7010_1_1.fw) and copying it into /lib/firmware rebooting and then reinserting the adapter.

---

### Post by raac on 2011-01-15
IT WORKED THANK YOU!!!

do you know if this same procedure would work with a mandriva distribution??

---

### Post by raac on 2011-01-15
Wow, apparently it is not the same procedure for mandriva. I redid everything  and did not work....
I thought every linux distribution will follow the same procedure...Today I learned two things today, lol.

---

### Post by solar george on 2011-01-16
It depends if mandriva has an up to date version of the ath9k_htc wireless driver and it may install its firmware in a different place. You can see if there is a firmware package in the mandriva repos and see where it installs the .fw files to and copy the one I linked to into that directory also check and see if mandriva has some kind of additional drivers package (i've not used mandriva since it was mandrake linux so I'm not sure how it manages its kernel drivers).

---

### Post by raac on 2011-01-16
I found the driver ath9k_htc and place the firmware. It works (in a way). It detects the wireless and I'm able to connect and everything. BUT, the internet does not work, I opened firefox and it does not load any pages I tried ssh and does not work either.

It's weird because I am connected. The other weird thing is that, now the ethernet does not work either (it used to before). Does this have to do something related with a driver??

---

### Post by solar george on 2011-01-16
No that sounds like a config issue, if this is still mandriva we're talking about I can't help as they use a completly different config layout to debian/ubuntu.

---

### Post by DJArty on 2011-02-06
What H/W version of TL-WN821N you have?   3.. 3.1 ?
Its work finally in 802.11n speeds? more then 54M
Tnx.

---

### Post by hebetude on 2011-02-21
> **solar george said:**
> Hmm seems to be no firmware package for it right now. . .
Try downloading [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar7010_1_1.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar7010_1_1.fw;hb=HEAD) (save as ar7010_1_1.fw) and copying it into /lib/firmware rebooting and then reinserting the adapter.

My hero, this seems to be a bug eh?

---

### Post by solar george on 2011-02-21
> **hebetude said:**
> this seems to be a bug eh?
I suppose so although I don't think that the maintainers do backports of the linux-firmware package (which is where it should go).
If you want to follow it up, first check if the card is working in natty (the next release - don't install this over your main system but try running as a live cd/usb) out of the box, if not try adding the firmware file again - if that fixes it then file a bug against linux-firmware in natty about inclusion of the file.
Once that is fixed or if natty works with your wireless card straight-away you'll need to file a bug asking for the fix to be added to whichever release you're using (see [https://bugs.launchpad.net/intel/+bug/716832](https://bugs.launchpad.net/intel/+bug/716832) as an example, don't report a new bug in the same package since that is an intel one).

---

