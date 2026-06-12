---
title: "Bluetooth Networking on ChrUbuntu 12.04"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by chuckmoney on 2013-01-14
I recently got an Acer C7 Chromebook (a Christmas present) and of course, put Linux on it.  As ChrUbuntu was all that would install correctly, that's what it is running.  The system is a standard x86-64 Intel system, not an ARM like most of the other Chromebooks, and runs the current stock kernel from plain old Ubuntu 12.04.  I'm using MATE rather than Unity, both out of personal preference and because the system is rather low-end and MATE is considerably lighter on the resources.  As a result, and also because the default Gnome2/MATE Bluetooth Settings panel just won't work no matter what I do, I'm using Blueman to try to configure the various Bluetooth stuff.

In addition, while the system does have a built-in Bluetooth adapter, depending on which source you trust, it either has no antenna or no radio at all.  Either way, it fails to detect my phone when sitting directly on top of it, so it's useless.  As my main system has no Bluetooth at all, I ordered a pair of Atheros USB Bluetooth adapters.

I have spent the last two weeks getting almost everything working flawlessly,  with one glaring exception.  Bluetooth Networking doesn't work on the Chromebook.  This would be fine, except that 85% of the time I'm using it to sit beside my main system and run Quassel (IRC Client) so the keyboard, aside from being rather small for extended typing anyway, is off to the side and very hard to reach.  Accordingly, I want to run Synergy and to do that, I need a NIC I can dedicate to it.  I had it working via Ethernet before but I take both systems home with me every single weekend, and rather than fumbling around with yet another cable twice every week, I'd really like to run Synergy via Bluetooth Networking.

Now, this is the problem.  The USB Adapter is working.  It plays audio to a stereo bluetooth speaker, headset audio to a Jawbone earpiece, and also runs my Bluetooth mouse without fail.  According to Blueman, it has support for networking.  It can even send AND recieve files via OBEX to and from the exact same computer I'm trying to network with.  However, the output of an "ifconfig -a" gives me only eth0, wlan0, and lo.  It IS listed in lsusb, however attempting "modprobe bnep" (as suggested in a blog post I found) gives me a dreaded "FATAL: Module bnep not found."  Further checking of every single file within /etc/modprobe.d/ tells me the module is NOT blacklisted.

Thus, my issue.  Best I can tell, ChrUbuntu uses the stock Ubuntu 12.04 current kernel.  However, assuming this is true, why does it not include this module?  I tried changing to the realtime kernel and again, Module bnep not found.  Maybe it's NOT using the kernel installed or specified in APT?  I know ChrUbuntu doesn't use GRUB (the BIOS on the Chromebooks are all heavily locked down...) and may not use any bootloader at all, though I know not what else it would use.

Any thoughts?  Is there, perhaps, a way to install the bnep module separately from the kernel itself?

---

### Post by Joespower on 2013-01-18
chuckmoney, I'm running chrUbuntu on the C7 also.  I'm curious, how much did you try to get the onboard BT to work?  I can't say I've done a lot of research, but I could swear I saw somewhere that someone had gotten it to work (they just didn't post any details)...

Also, you say you've gotten everything else to work "flawlessly".  Any chance you could elaborate?  I only have a few gripes, like I'm unable to hibernate and the trackpad is completely random, etc.  If I could fix those I'd be a seriously happy camper!

I'll keep looking for how to get the internal BT to work, and I'll post here if I find something...

---

### Post by fjs on 2013-01-20
Bluetooth does not work for you on the Acer C7 because the model does not have Bluetooth. You have not read the product description, nor run lspci.

I have swapped out the half-height pci card for one with Bluetooth and radio.

---

### Post by chuckmoney on 2013-02-10
```
Term:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation Panther Point Thermal Management Controller (rev 04)
01:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)

Term:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04ca:3006 Lite-On Technology Corp. 
Bus 001 Device 004: ID 064e:d251 Suyin Corp. 
Bus 002 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
```

As to fjs, the last device on lsusb is indeed my USB controller, whilst no PCI controller is listed.  However, this is more because the device that DOES exist on the board is non-functional and not because there is no device.  It simply lacks a working radio.  Not that any of this matters.  That said, yes, I read the "product description" and it does indeed state that there isn't any bluetooth device.  Considering as how there clearly is such a device, just a non-functional one, the description is CLEARLY wrong.  Add to that the fact that the entire device is a near-identical clone of an Aspire One, which has a working version of the SAME CARD in the SAME SPOT on the same motherboard.  So no, the "product description" with all due respect means about as much as a warm cup of jack squat.

Joespower, what I meant by "everything else is working flawlessly" is exactly that.  The video card, screen, audio, touchpad, and even the power management system all works exactly as intended.  I didn't really do anything to make it work.  That is, everything that's working now was working "out of the box" and required nothing from me.

Bluetooth Networking remains non-existent, but my mouse, headset, and stereo speaker all work just fine.  For now, I'm using a retractable network cable for Synergy, etc, but I'd still rather cut another cord and get Bluetooth Networking working.

So back to my original question: anyone know where I can find a copy of bnep.ko already compiled and compatible with ChrUbuntu 12.04?

---

### Post by thetechguy911 on 2013-03-31
Hi chuckmonkey, the acer c7 doesn't even ship with bluetooth.

---

### Post by Dig It on 2013-04-29
I can absolutely confirm that my C7 does actually have bluetooth.  I was able to pair and use a Logitech BT mouse with it under Chrubuntu 12.04.  It is a 2GB 4 cell model manufactured 2013/03/25 and purchased at Best Buy Canada last week.

---

### Post by b2yb on 2013-09-19
> **Dig It said:**
> I can absolutely confirm that my C7 does actually have bluetooth.  I was able to pair and use a Logitech BT mouse with it under Chrubuntu 12.04.  It is a 2GB 4 cell model manufactured 2013/03/25 and purchased at Best Buy Canada last week.

I can confirm the Bluetooth module exists, though it fails to pair with my Microsoft Wedge Keyboard via the GUI tool and newer tools.  I had to install bluez-compat, then use **sudo hidd --connect MA:CA:AD:RE:SS** in order to connect.  This may be a device issue though with the keyboard as I have to take similar steps on another laptop running 13.04.

---

