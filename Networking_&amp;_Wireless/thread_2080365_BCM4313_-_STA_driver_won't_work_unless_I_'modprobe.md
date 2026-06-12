---
title: "BCM4313 - STA driver won't work unless I 'modprobe wl' after each boot"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by dekaru01 on 2012-11-03
A strange one this (then again, I'm obviously missing something obvious here).

I've been using brcmsmac for months, but in 12.10 (with latest kernel) it's buggy for me - disconnecting every few minutes, while network-manager still thinks it's connected. A manual disconnect and then reconnect through network-manager fixes things, but just for a few minutes.

So I switched to the STA driver. Took a few hours of trial and error to get it to work, but now it's working. That is, only if I

```
sudo modprobe wl
```

after each boot. Otherwise, nothing. network-manager doesn't even think it has a wireless card available. "Enable Wireless" is missing, and "Enable Networking" is checked.

After I run the modprobe command above, it immediately automagically sees the card, and uses it to connect.

I've added the command to /etc/rc.local, but this feels hacky. Is there a way to make the card become 'alive' on each boot without modprobe? Needless to say, this never happened to me while using brcmsmac.

Any details I can give to help - ask away, naturally.

Ubuntu 12.10, Dell Inspiron 13R (N3010), BCM4313 [14e4:4727].

---

### Post by Hadaka on 2012-11-03
Hi, this should fix ya up..

```
sudo echo 'wl' >> /etc/modules 
```

---

### Post by Hadaka on 2012-11-03
.....and since you changed drivers, you might want to throw some
of the leftovers into the blacklist can. Please post..

```
lspci -nnk | grep -iA5 net 
```

thanks

---

### Post by dekaru01 on 2012-11-05
> **Hadaka said:**
> .....and since you changed drivers, you might want to throw some
of the leftovers into the blacklist can. Please post..

```
lspci -nnk | grep -iA5 net 
```

thanks

```
lspci -nnk | grep -iA5 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: wl
	Kernel modules: wl, bcma
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Dell Device [1028:0455]
	Kernel driver in use: atl1c
	Kernel modules: atl1c
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Intel Corporation Device [8086:8086]
```

I've added brcmsmac, bcma, b43, and brcm80211 to /etc/modprobe.d/blacklist.conf.

---

### Post by dekaru01 on 2012-11-05
> **Hadaka said:**
> Hi, this should fix ya up..

```
sudo echo 'wl' >> /etc/modules 
```

Unfortunately I get this:

```
sudo echo 'wl' >> /etc/modules
bash: /etc/modules: Permission denied
```

I've added "wl" (without the quotation marks) to /etc/modules via gedit. Isn't that basically the exact same thing you told me to do? I ask because it seems to have worked. The wireless network is now alive on each boot without the need for modprobe wl.

---

### Post by Hadaka on 2012-11-05
yes it is...

out of habit..i usually suggest .. to test.. the modeprobe command
then the modules command.

sorry bout that, please mark this thread solved by using ..thread tools

thanks

---

### Post by dekaru01 on 2012-11-05
Marking as solved now. Thank you very much for your help.

I do have a couple of questions if you don't mind. First, is this (adding 'wl' to /etc/modules) the 'normal' thing to do when switching to the STA driver for Broadcom wireless stuff? 

I ask because if that's so, it isn't apparent in any way. I assumed that by just selecting the STA driver in jockey - it would work. And it didn't, unless I modprobe-d it.

And second, was the output of lspci you asked for above 'okay'? Or do I need to do anything else? I wouldn't want remnants of the open source driver to conflict with the STA driver in any way.

Thanks again.

---

### Post by Hadaka on 2012-11-05
Hi,    /etc/modules loads the wireless module at boot..its what is for...

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

```
cat /etc/modules 
```this will show you that and all if any modules within it.

and...per chili555, who is MUCH more knowledgable than I, says there is hidden magic,
smoke and mirrors that blacklists the stuff you dont want when you load the sta driver.

you can see your blacklist file with..

```
grep 'blacklist' /etc/modprobe.d/blacklist.conf
```Have FUN !!

---

### Post by doudou4978 on 2013-01-10
The free wifi driver is unstable (same problems described by dekaru04 at the beginning of the thread).

1) I try to activate the proprietary driver (Software Updater>Settings>Additional Drivers>Using Broadcom 802.11 Linux STA wireless driver source form bcmwl-kernel-source (proprietary).

2) After reboot, there is no more menu of wl network in Menu Bar>Network Menu.

3) I added wl in /etc/modules:

[I]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
**wl**
[/I]
4) But lspci -nnk | grep -iA5 net returns:

[I]00:19.0 Ethernet controller [0200]: Intel Corporation 82577LC Gigabit Network Connection [8086:10eb] (rev 06)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
--
[B]02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel modules: bcma[/B]
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Intel Corporation Device [8086:8086]
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)[/I]

THE KERNEL DRIVER DOESN'T APPEAR FOR BCM4313.

5) And if I "sudo modprobe wl", it returns:

*FATAL: Module wl not found.*

6) Last: "grep 'blacklist' /etc/modprobe.d/blacklist.conf" returns:

[I]blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
**blacklist bcm43xx**
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
[/I]
7) and a file "blacklist-bcm43.conf" appears in /etc/modprobe.d/
which contains:

[I]# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
[/I]
Where am I wrong?

---

