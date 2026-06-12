---
title: "Bluetooth just stopped working"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by underdog512 on 2010-01-15
When I first installed 9.10 my internal bluetooth worked perfectly.   Its been about a month since I used it.  Last night I was trying to pair my phone with my laptop and I noticed when I hover over the bluetooth icon in the notification area it say "Bluetooth: Disabled" and the only option I have when I click on it is "Turn Bluetooth off" and "Preferences"

I have a Dell Studio 15.

Here is the output from lspci

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

### Post by gradinaruvasile on 2010-01-15
What does

rfkill list

return?

---

### Post by underdog512 on 2010-01-15
> **gradinaruvasile said:**
> What does

rfkill list

return?

```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by gradinaruvasile on 2010-01-15
Hm. It should be ok. Restart the bluetooth service:

sudo service bluetooth restart

And do a soft blocking/unblocking:

sudo rfkill block bluetooth
sudo rfkill unblock bluetooth


Do you use the default kernel?

---

### Post by underdog512 on 2010-01-15
Yea I have already done all of that.  I have even tried booting into older kernels.  It must have been a recent update that broke it.  Updates have a bad habit of breaking things on my laptop it seems.

---

### Post by gradinaruvasile on 2010-01-15
It happened to me something like that when i tried the .32 kernel on my Dell D630. You might try installing blueman, an alternative bluetooth manager...

---

### Post by underdog512 on 2010-01-20
BlueMan is giving me an error 

"Bluez daemon is not running, blueman-manager cannot continue."

I have verified that this daemon is indeed running. 

output from ps -aux

```
root        29  0.0  0.0      0     0 ?        S<   10:22   0:00 [bluetooth]

```

it seems my problem seems to be isolated to this daemon. Any ideas?

---

### Post by underdog512 on 2010-01-25
any ideas on this?

---

### Post by alexfish on 2010-01-25
hi

have you tried 

Code:

sudo /etc/init.d/bluetooth restart

---

### Post by underdog512 on 2010-01-26
> **alexfish said:**
> hi

have you tried 

Code:

sudo /etc/init.d/bluetooth restart


Yes. many times.  Something is screwed up with that daemon. Is there a config file that needs to be reconfigured?

---

### Post by underdog512 on 2010-02-01
bump

---

### Post by clevertomato on 2010-02-26
Do you or did you have Windows on this machine? Mine worked, then I had to boot into Windows 7 briefly for something, and from then on bluetooth didn't work anymore in karmic. I finally got the suspicion, booted into Windows 7, saw that it had automagically turned bluetooth off, so I turned it back on in Windows 7, rebooted into karmic and all was well again.

Just an idea... I don't know if it will help you or not.

---

