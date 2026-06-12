---
title: "Does this component work with Ubuntu?"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by Matthew24 on 2011-02-11
Hello,

I posted this thread and received no help and tried ndiswrapper and it did not work.
[http://ubuntuforums.org/showthread.php?t=1683947](http://ubuntuforums.org/showthread.php?t=1683947)

I am now considering just buying a new PCI wireless adapter that works out of the box
and is fast with Linux.

I found this card on Amazon, will this work??
[http://www.amazon.com/802-11g-Wireless-WIFI-Adapter-Desktop/dp/B003OBHE60](http://www.amazon.com/802-11g-Wireless-WIFI-Adapter-Desktop/dp/B003OBHE60)

It says it works with Linux, should I believe it??

Thank you!
[U]
Note: [/U]right now I have Ubuntu 10.10 installed on his machine but I wish to install the latest
XUbuntu on it once I get a wireless card that actually works, the XFCE UI is great for his
needs.

---

### Post by DanneStrat on 2011-02-11
> **Matthew24 said:**
> Hello,

I posted this thread and received no help and tried ndiswrapper and it did not work.
[http://ubuntuforums.org/showthread.php?t=1683947](http://ubuntuforums.org/showthread.php?t=1683947)

I am now considering just buying a new PCI wireless adapter that works out of the box
and is fast with Linux.

I found this card on Amazon, will this work??
[http://www.amazon.com/802-11g-Wireless-WIFI-Adapter-Desktop/dp/B003OBHE60](http://www.amazon.com/802-11g-Wireless-WIFI-Adapter-Desktop/dp/B003OBHE60)

It says it works with Linux, should I believe it??

Thank you!
[U]
Note: [/U]right now I have Ubuntu 10.10 installed on his machine but I wish to install the latest
XUbuntu on it once I get a wireless card that actually works, the XFCE UI is great for his
needs.

Hi!

The card you have on that link

has a "rt2561" chipset which seems to be a little

tricky to get working.

We can start with trying to get the card you have working

by doing a little troubleshooting.

Make sure you have the card connected.

Open a terminal and do the following:

```
lspci
```

Post the full output.

---

### Post by Matthew24 on 2011-02-12
> **DanneStrat said:**
> Hi!

The card you have on that link

has a "rt2561" chipset which seems to be a little

tricky to get working.

We can start with trying to get the card you have working

by doing a little troubleshooting.

Make sure you have the card connected.

Open a terminal and do the following:

```
lspci
```

Post the full output.

```
mike@mike-T5274:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:03.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
mike@mike-T5274:~$ 

```
Hi thanks for your help! I won't buy that card then since it's hard to get going... I actually tried ndiswrapper on my Linksys WMP54G... I used the xp and vista drivers, no go.

---

### Post by DanneStrat on 2011-02-12
> **Matthew24 said:**
> ```
mike@mike-T5274:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:03.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
mike@mike-T5274:~$ 

```
Hi thanks for your help! I won't buy that card then since it's hard to get going... I actually tried ndiswrapper on my Linksys WMP54G... I used the xp and vista drivers, no go.

[COLOR="Red"]See next reply. I forgot you were using ndiswrapper![/COLOR]


I noticed that you have the same chipset in your

current card!:)

No problem though as a think I know how to get it

working.

Start by opening a terminal and do this:

```
lsmod | grep rt
```

Post the output.

I need this info to know if you have

any loaded modules for your card or else we

will load another one at startup.

---

### Post by DanneStrat on 2011-02-12
You have to remove any drivers you installed

with ndiswrapper prior to doing what I described above.

Go to your "administration menu"

Now go into "wireless card drivers"

or something similar.

Remove any drivers listed.

Reboot your computer.

Now you can continue in the

previous reply.

---

### Post by Matthew24 on 2011-02-12
```
[CODE]mike@mike-T5274:~$ lsmod | grep rt
rt61pci                18996  0 
crc_itu_t               1383  1 rt61pci
rt2x00pci               6029  1 rt61pci
rt2x00lib              27275  2 rt61pci,rt2x00pci
mac80211              231541  2 rt2x00pci,rt2x00lib
parport_pc             26058  1 
led_class               2633  1 rt2x00lib
cfg80211              144470  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt61pci
agpgart                32011  2 drm,intel_agp
parport                31492  3 ppdev,parport_pc,lp
mike@mike-T5274:~$ ^C
mike@mike-T5274:~$ 

```[/CODE]

Okay, thanks for the help.

There are no wireless drivers in the ndiswrapper box... like I said I tried both the vista and xp drivers in ndis and no luck.

I haven't found any support sites on google either.

Thank you and take care.

---

### Post by DanneStrat on 2011-02-13
Removed this reply.

---

### Post by chili555 on 2011-02-13
> here should only be one.(rt61pci)

We will begin by blacklisting rt2x00pci and rt2x00lib.
What about this?```
$ modinfo rt61pci 
filename:       /lib/modules/2.6.35-25-generic/updates/compat-wireless-2.6.36/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9ABF57432729A3A69DC0919
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
[COLOR="Red"]depends:        rt2x00lib,rt2x00pci[/COLOR],crc-itu-t,eeprom_93cx6
vermagic:       2.6.35-25-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

---

### Post by DanneStrat on 2011-02-13
> **chili555 said:**
> What about this?```
$ modinfo rt61pci 
filename:       /lib/modules/2.6.35-25-generic/updates/compat-wireless-2.6.36/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9ABF57432729A3A69DC0919
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
[COLOR="Red"]depends:        rt2x00lib,rt2x00pci[/COLOR],crc-itu-t,eeprom_93cx6
vermagic:       2.6.35-25-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

Thanks for pointing that out!

I didn't know that it depended on those two.

Then there must be something else

preventing his card from working.

---

### Post by chili555 on 2011-02-13
> Then there must be something else preventing his card from working.Yes, indeed. I'd suggest we look at kernel messages on the subject:```
dmesg | grep rt6
```If he is missing firmware, it can be installed:```
sudo apt-get install linux-firmware
```I'll monitor your progress and throw in any suggestions, if I'm not stepping on toes.

---

### Post by DanneStrat on 2011-02-13
> I'll monitor your progress and throw in any suggestions, if I'm not stepping on toes.

No problem at all!

I also say we start by doing what you said.

Matthew, in a terminal do:

```
dmesg | grep rt6
```

Post the output.

---

