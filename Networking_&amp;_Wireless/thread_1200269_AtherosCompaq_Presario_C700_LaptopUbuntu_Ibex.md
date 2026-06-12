---
title: "Atheros/Compaq Presario C700 Laptop/Ubuntu Ibex"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by johnwahl on 2009-06-29
Hello - Can anyone help me get an Atheros AR242x wireless card in my Compaq C700 laptop up and running?  I have a LinkSys Wireless G Router (I can directly connect to my Cable modem via Ethernet).  The biggest problem seems to be getting the driver to be recognized by the OS.  I've included (I hope) extensive info that I've seen requested in other messages.  I've tried native Ibex drivers, the upgrade package and ndiswrapper, all to no affect.  After spending about 20 hours on this I could sure use some help from the experts!

Thanks,

John Wahl

Here's some of the info requested from other posts:

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
Subsystem: Hewlett-Packard Company Device 137a
Flags: fast devsel, IRQ 16
Memory at 51300000 (64-bit, non-prefetchable) [disabled] [size=64K]
Capabilities: <access denied>
Kernel modules: ath_pci

Some blacklisting I've tried:
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

echo -e "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

lshw -C Network
WARNING: you should run this program as super-user.
*-network
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:01:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ndiswrapper latency=0 module=ndiswrapper
*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:02:01.0
logical name: eth0
version: 10
serial: 00:1b:38:ef:ee:17
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: aa:32:e3:b7:c0:90
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

dmesg | grep -e ath -e wlan
[ 12.769258] ndiswrapper (link_pe_images:603): DLL initialize failed for athw.sys
[ 12.769295] ndiswrapper: driver netathw (,03/13/2009,7.7.0.259) loaded
[ 780.641673] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 780.658037] wlan: 0.9.4
[ 780.667343] ath_pci: 0.9.4

uname -rm
2.6.27-7-generic i686

iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

modinfo ath_pci
filename: /lib/modules/2.6.27-7-generic/volatile/ath_pci.ko
srcversion: D3FD3BD11169A96DBCFF8DE
alias: pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias: pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias: pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias: pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias: pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias: pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias: pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias: pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias: pci:v000010B7d00000013sv*sd*bc*sc*i*
alias: pci:v0000A727d00000013sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends: ath_hal,wlan
vermagic: 2.6.27-7-generic SMP mod_unload modversions 586
license: Dual BSD/GPL
version: 0.9.4
description: Support for Atheros 802.11 wireless LAN cards.
author: Errno Consulting, Sam Leffler
parm: countrycode:Override default country code (int)
parm: maxvaps:Maximum VAPs (int)
parm: outdoor:Enable/disable outdoor use (int)
parm: xchanmode:Enable/disable extended channel mode (int)
parm: rfkill:Enable/disable RFKILL capability (int)
parm: autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm: ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm: ath_debug:Load-time debug output enable (int)

---

### Post by johnwahl on 2009-06-29
Can anyone else see this thread? I'm wondering what's wrong with my question that I'm not getting any replies. Is this the wrong forum?
 
Thanks,
 
John Wahl
 
Thanks to those of you that wised me up and told me I'm in the right place and to be PATIENT!  Some of us don't use forums very much....

---

### Post by johnwahl on 2009-06-29
What determines which message gets answered here?  I see that messages posted AFTER mine get replies.  Is there something wrong with my message?

Thanks,

John Wahl

---

### Post by Blood//Stain//Child on 2009-06-29
I would suggest Fedora 11 if you have an Atheros wireless card. It works much better than Ubuntu with this chipset.

---

### Post by johnwahl on 2009-06-29
Thanks very much for the reply.  I've seen others say that Ubuntu Ibex works well with a Netgear WG511T card.  Would it be worthwhile to just get a plug in card?

John Wahl

---

### Post by Blood//Stain//Child on 2009-06-29
I use a TP-Link WN321G USB wireless dongle, and it has worked flawlessly since 8.04 Hardy Heron. As such, I would recommend that solution to your issue.

---

### Post by johnwahl on 2009-06-29
Thanks a lot.  It seems like it should be an inexpensive solution.  I'll check it out!  You've been a great help.

John Wahl

---

### Post by Blood//Stain//Child on 2009-06-29
Good luck.

---

### Post by t0mppa on 2009-06-30
Some tips for the future.

Not getting an instant reply to your thread doesn't mean you're getting ignored, it simply means no one who knows what's up is currently browsing the forums. No one here gets paid to help, so we don't spend 24/7 monitoring for new posts. And there are people from all over the world here, so time zones come to play and the people who can help you could for instance be at work or sleeping at the time of your posting.

That someone posted in a thread that was created later than yours simply means that person knew how to help in the other issue and not with yours, we're all humans here and thus not omniscient. Rule of the thumb is, if you don't get a reply in 24 or 36 hours, then it's time to start bumping your thread.

All three of the options you listed should work on their own, but having 2 different drivers working simultaneously rarely, if ever, works. And looks like you're having both ath_pci and ndiswrapper there, so it wouldn't be a big surprise if they were creating a conflict, where neither one work.

Ndiswrapper isn't giving your interface a logical name and dmesg shows the DLL initialize failed, so it isn't functioning correctly, could be you're just using the wrong Windows drivers for it.

Bcm43xx, b43, b43legacy & ssb are modules used for Broadcom chips, so if they were active in the first place, something was seriously wrong and if not, just randomly blacklisting modules isn't a good idea as it can cause you to run into trouble with other things in the long run.

---

### Post by hambos22 on 2009-06-30
i have the same laptop. Just put the cd on drive and make those commands

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

Then find the latest madwifi snapshot **madwifi-hal-0.10.5.6-r3835-20080801.tar.gz**
download it, put it on your home folder and make those commands

```
tar xvzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
```

reboot and enjoy wifi
BUT! After kernel change you must reload ath modules.. I don't know how!

---

### Post by johnwahl on 2009-06-30
> **t0mppa said:**
> Some tips for the future.
 
Not getting an instant reply to your thread doesn't mean you're getting ignored, it simply means no one who knows what's up is currently browsing the forums. No one here gets paid to help, so we don't spend 24/7 monitoring for new posts. And there are people from all over the world here, so time zones come to play and the people who can help you could for instance be at work or sleeping at the time of your posting.
 
That someone posted in a thread that was created later than yours simply means that person knew how to help in the other issue and not with yours, we're all humans here and thus not omniscient. Rule of the thumb is, if you don't get a reply in 24 or 36 hours, then it's time to start bumping your thread.
 
=============
Thanks very much for the reply, and I understand that I've stepped on some toes here.  May I suggest that your suggestions be sticky or part of the FAQ?  I found it difficult (because I don't use forums much) to figure out how to use this one.  I also had no idea how long it should take to get a response since I waited 24 hours before reposting mine.  I now know that I should have waited 24 hours and then "bumped" my original thread (I'll have to figure out how to do that).  Anyone, sorry if I've offended anyone and I really appreciate this help and advice.
 
John Wahl
 
 
All three of the options you listed should work on their own, but having 2 different drivers working simultaneously rarely, if ever, works. And looks like you're having both ath_pci and ndiswrapper there, so it wouldn't be a big surprise if they were creating a conflict, where neither one work.
 
Ndiswrapper isn't giving your interface a logical name and dmesg shows the DLL initialize failed, so it isn't functioning correctly, could be you're just using the wrong Windows drivers for it.
 
================
 
In reading another thread I found that the AR5416 driver is supposed to work, but the link provided results in a netathw.sys driver.  (Sorry, working from memory here).
 
================
 
Bcm43xx, b43, b43legacy & ssb are modules used for Broadcom chips, so if they were active in the first place, something was seriously wrong and if not, just randomly blacklisting modules isn't a good idea as it can cause you to run into trouble with other things in the long run.
 
================
 
Again, this is advice from other postings.  I'm doing the best I can, but I'm thinking the advice to get the dongle is probably going to be the easiest method at this point.  On the other hand, if people out there think this is doable and can point me to step by step directions, I'll keep hammering away at it.  I guess the first question is AR242x.  Is there a driver that should work with this?  Is it provided in Ibex or will I need to install it with ndiswrapper?  If so, where can I get the driver?
 
Thanks,
 
John Wahl

---

### Post by johnwahl on 2009-06-30
Thank you!  I will try this tonight.
 
John Wahl

---

### Post by johnwahl on 2009-06-30
reboot and enjoy wifi
BUT! After kernel change you must reload ath modules.. I don't know how![/quote]
 
===========
 
Thanks!  I'll give this a try tonight.
 
John Wahl

---

### Post by johnwahl on 2009-06-30
> **hambos22 said:**
> i have the same laptop. Just put the cd on drive and make those commands

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```Then find the latest madwifi snapshot **madwifi-hal-0.10.5.6-r3835-20080801.tar.gz**
download it, put it on your home folder and make those commands

```
tar xvzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
```reboot and enjoy wifi
BUT! After kernel change you must reload ath modules.. I don't know how!

====================

Thanks!  I keep trying to reply to this, but it seems to keep failing.  I hope this one works.  I'm going to try this tonight.

John Wahl

---

### Post by t0mppa on 2009-07-01
[QUOTE=johnwahl]Thanks very much for the reply, and I understand that I've stepped on some toes here. May I suggest that your suggestions be sticky or part of the FAQ? I found it difficult (because I don't use forums much) to figure out how to use this one. I also had no idea how long it should take to get a response since I waited 24 hours before reposting mine. I now know that I should have waited 24 hours and then "bumped" my original thread (I'll have to figure out how to do that). Anyone, sorry if I've offended anyone and I really appreciate this help and advice.[/QUOTE]

No harm done, just saying that there's quite a bit of difference between asking for help and demanding answers and that response times on a forum are quite different from call centers for instance. Oh and bumping just means writing a post without any real content towards solving the issue to push your thread to the top of the forum to catch attention, like your 2nd & 3rd post.

[QUOTE=johnwahl]Again, this is advice from other postings. I'm doing the best I can, but I'm thinking the advice to get the dongle is probably going to be the easiest method at this point. On the other hand, if people out there think this is doable and can point me to step by step directions, I'll keep hammering away at it. I guess the first question is AR242x. Is there a driver that should work with this? Is it provided in Ibex or will I need to install it with ndiswrapper? If so, where can I get the driver?[/QUOTE]

The thing is, are you going to go and buy a new component every time you run into trouble with an old one? Not saying it happens often, but in the long run, you might end up accumulating quite a pile of stuff. I have an AR242x on my laptop as well and both ath_pci & ath5k_pci (haven't tried ndiswrapper yet) work with it.

What you will need to do is get rid of ndiswrapper first, if you're going to try what hambos22 suggested. Like I said before, having two drivers for the same interface active at the same time is never a good idea. First run **ndiswrapper -l** to see what the exact name of the driver you have is and then **ndiswrapper -r <driver_name>** and **sudo modprobe -r ndiswrapper**. Then if you used Synaptic to install it, you can follow the same steps to uninstall it and if you compiled it manually, you have to go into the directory where you unpacked it and run **sudo make uninstall**.

[QUOTE=hambos22]Then find the latest madwifi snapshot madwifi-hal-0.10.5.6-r3835-20080801.tar.gz, download it ...[/QUOTE]

That's actually just the snapshot for 01/08/2008, where the latest snapshot was released on 29/05/2009. Just use [this link]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz"), as it gets updated to always point at the latest release.

---

