---
title: "No audio from speakers"
date: 2011-02-10
forum: Multimedia Software
---

### Post by MtnDew on 2011-02-10
Hello,

I recently installed Ubuntu 10.10. The audio did not work prior to updating the system & software so it wasn't the updates. I have Bose Companion 2 Series 2 (Multimedia Speaker System) plugged in. When I was on Windows (I installed Ubuntu on top of it) they worked just fine. My headset (Microsoft LifeChat) work just fine. It is not muted nor are they on low volume. 

If Bose Companion 2 require a proprietary driver how would I go about finding an alternative? I checked their website and all the software requires Windows NT+. I have tried reloading ALSA. I have installed Ubuntu Restricted Extras. 

Running *cat /proc/asound/version *returns:> Advanced Linux Sound Architecture Driver Version 1.0.23.[CENTER]** LSPCI:**
[/CENTER]
 > 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
[CENTER]**LSMOD:**
[/CENTER]

> 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
> Ubuntu Release: 10.10 (Maverick)
Linux Kernal Version: 2.6.35-25-generic-pae
Gnome: 2.32.0

---

### Post by gordintoronto on 2011-02-10
The speakers are just regular PC speakers, they don't need software of any kind. The real question is about this:
Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

Where did you plug the speakers in?

If you open Preferences/Sound and select the output tab, you will see a drop-down labelled "Connector." I suggest you play around with the options there to see if your speakers will work.

---

### Post by MtnDew on 2011-02-10
> **gordintoronto said:**
> The speakers are just regular PC speakers, they don't need software of any kind. The real question is about this:
Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

Where did you plug the speakers in?

If you open Preferences/Sound and select the output tab, you will see a drop-down labelled "Connector." I suggest you play around with the options there to see if your speakers will work.

Nope...Now neither work, despite putting it back onto my previous configuration...

---

### Post by MtnDew on 2011-02-10
This is ******* ridiculous. I thought this was an operating system for humans, not computer scientist who get off to mapping an audio output system. Not that I don't love spending six hours researching why both of my soundcards won't work...or that once I get it to work after three ******* days it breaks at the sound of a ******* mouse fart... or even that it  doesn't even include a "reset default settings"... but don't ******** the community and tell me it's an o.s for humans. 

I'm done with this ******* sucking time vampire o.s

---

