---
title: "how to get do i get my belkin card to work"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by hazman on 2010-03-05
Hi
I have a belkin wireless G notebook card and wonder how to go about getting it up and running

---

### Post by bkratz on 2010-03-05
> **hazman said:**
> Hi
I have a belkin wireless G notebook card and wonder how to go about getting it up and running

A bit more information is needed. If you go to the terminal and copy/paste (back here)  the output of

lspci
(LSPCI in lowercase)

at least we should have an idea of the wireless card involved.

---

### Post by mark bower on 2010-03-05
According to the link below, you may have some trouble with a Belkin PCMIA card.  You need to post which card you have?  You need to describe what you have done for others to help?  If you have problems you cannot lick, then as always, I recommend considering the USB Belkin F5D7050 wireless adapter for which there is a very high success of working out of the box.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

mark

---

### Post by hazman on 2010-03-05
this is what i got using lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
03:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)

the card is a belkin f5d7010 ver.7000uk

---

### Post by chili555 on 2010-03-05
Please try:```
sudo modprobe rtl8180
iwconfig
```Is your device now working?

---

### Post by hazman on 2010-03-05
no i have the drivers rtl 8185 that worked before just unable to work out how to implement them

---

### Post by chili555 on 2010-03-05
Please post:```
dmesg | grep -e 818 -e 03:00
```Thanks.

---

### Post by hazman on 2010-03-05
it came up with
[ 3653.11682]ndiswrapper (load_sys driver:210): couldn't prepare driver 'net8185'
[ 3653.116862]ndiswrapper (load_wrap_driver:112): couldn't load driver 'net8185'check system log for messages from 'loadndiswrapper'
[ 4021.874959]ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8185'
[ 4021.881068]ndiswrapper (load_wrap_driver:112): couldn't load driver 'net8185'check system log for messages from 'loadndiswrapper'

---

### Post by chili555 on 2010-03-05
Let's see what ndiswrapper says:```
ndiswrapper -l
```Maybe you have the wrong .inf and/or .sys file.

---

### Post by hazman on 2010-03-05
that gives the message

net8185 : driver installed
        device (1799:701f)present

---

### Post by chili555 on 2010-03-05
Please let me see:```
sudo cat /var/log/messages | grep -e ndis -e wlan
rfkill list
```Thanks.

---

