---
title: "RTL8187b Internal USB Wireless Adapter Problem"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by Midnightsun on 2009-01-12
Hi guys,

I have the troublesome RTL8187b card which has in the past been a real pain in the behind to work with.

Recently I was forced to install Windows on a separate partition and dual boot for unrelated reasons.  The adapter works fine in XP.  When I rebooted my computer back into Ubuntu I ran "lsusb" and noticed that my adapter was appearing!  It hadn't been previously.  Excitedly I clicked the network manager and lo and behold - there was a list of wireless networks.  I attempted to connect to my WPA protected router and amazingly it connected without a hitch.  

Couple of days testing and it's been great.  No connection drops, no deterioration in speed.  I've been a happy chappy.

However I have one nagging problem that is a real nuisance.  

To activate my wireless adapter in Windows I have to press the "Fn + F8" keys.  I hear the "usb device plugged in" sound and away we go.  No worries.

However in Ubuntu this functionality is lacking.  Fn+F8 will turn the card OFF but not ON.  For me to activate the wireless card I have to actually boot into Windows first, turn it on, reboot again into Ubuntu!  The device remains active through a reboot but NOT a shutdown.    

I'm not sure exactly how to get around this problem.  I'll list my system specs below and hopefully someone can give some advice!  My system seems to have been designed by someone who's girl cheated on him with a Linux geek as getting most things to work has been a nightmare.  I have to boot the kernel with the "acpi=off and noapic" flags as well as having to make do with only 2D graphics. (no compiz or openGL)

Advent 9315 Laptop
Ubuntu 8.04
lspci output:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

```

lsusb output: 

```
Bus 003 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 003 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```


Thanks in advance for any help on this issue!

---

### Post by julioipn on 2009-01-18
It is so weird that you have to boot windows first, you could try to install realtek rtl8187b linux driver to get rid of your problems, I sent an email to [email]wlanfae@realtek.com[/email] and they sent me back the driver,  I think this could be helpful since it comes with a radio power script which makes it possible to turn on and off the wireless card, It works for me, if I don't turn on the card ( function + F3 on my netbook) I can't join my wireless network

---

### Post by xbarranco on 2009-07-12
I have a laptop with almost exactly the same architecture as yours except for the Wireless card. In my case is an internal Ralink RT2501USB but I experienced the same issues you say: WLAN always OFF after booting and the weird need of going to Windows activate the card.

After some days I found the answer: updating the BIOS. Now the Wireless card is ON by default.

This link works only for model U50SIx (where x=number) laptops, so don’t try to flash this BIOS unless your laptop model matches the requirements or you could be exposed to a much more serious problem than that of the wireless. Look for an appropiate update of your BIOS

[http://forum.novatech.co.uk/showthread.php?t=4230](http://forum.novatech.co.uk/showthread.php?t=4230)

Mine is a U50SI1 INNOBO box.

Good luck!

---

### Post by xbarranco on 2009-07-12
Opps!  Looking around I've just found this:

> "Advent 9315 === ECS U50SI 1 (Gericom Phantom A4 Superlight)"

at:

[http://www.w00tw00t.co.uk/support/viewtopic.php?f=1&t=4736](http://www.w00tw00t.co.uk/support/viewtopic.php?f=1&t=4736)

In other words, the BIOS flashing will also work for you, suffering Advent 9315 users... ;-)

---

