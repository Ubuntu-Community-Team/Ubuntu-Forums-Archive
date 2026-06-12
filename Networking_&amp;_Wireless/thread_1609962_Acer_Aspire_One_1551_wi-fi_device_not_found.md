---
title: "Acer Aspire One 1551: wi-fi device not found"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by gmile on 2010-10-31
I have an Acer Aspire One 1551 netbook. After I installed Ubuntu 10.10 Netbook Remix (my first Ubuntu, though), [s]I discovered that wi-fi device isn't being recognized - ifconfig says that I only have ethernet device present...[/s] Somehow ***rfkill list*** indicates, that acer-wireless is always blocked. How to unblock it? ***rfkill unblock 0*** doesn't resolve the issue - device is still blocked.

Also, if this can help - somehow 'Fn+WiFi' combination on keyboard activates/deactivates Bluetooth instead of WiFi. Can I alter the behavior of the combination to turn on/off wireless networking?

I googled for a while but fruitlessly. Is it a known problem? Is there a workaround for it already? [s]Is there any additional information (clues) I can provide to speedup the process a bit?[/s]

This is what lspci returned:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

This is from lsusb:
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0489:e011 Foxconn / Hon Hai 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a4d Trust International B.V. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 064e:a219 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

rfkill list output:
```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by P4man on 2010-10-31
Let first see what wifi card you have in there. Open a terminal (apps | accessories | terminal) and type

```
lspci
```

and 

```
lsusb
```

Copy paste the output here.

---

### Post by gmile on 2010-10-31
**P4man**, I've updated top post as requested.

---

### Post by P4man on 2010-10-31
That wifi card should be supported out of the box. If you right click the network manager icon top right panel, does it show "enable wireless" (and is it enabled) ? Are you sure you dont have a hardware button to enable/disable wireless that is turned OFF. In a terminal type this


```
sudo rfkill list
```

Copy paste the output again.

---

### Post by gmile on 2010-10-31
P4man, I've updated top post with ***rfkill list*** as requested.

If I right click the network manager icon top right panel, does not it show "enable wireless" :(
Although I have a hardware button (Fn + Wifi button) to activate/deactivate Wi-Fi, changing it's state doesn't seems to change anything really.

---

### Post by P4man on 2010-10-31
Although its no guarantee it will actually work, your wifi card is recognized allright, but blocked. I dont know if your machine has a hardware key or some Fn+function key to unblock it, but this could work as well:

```
sudo rfkill unblock all
```

---

### Post by gmile on 2010-10-31
**P4man**, thanks for giving a clue about rfkill list and *device blocked* state! 

Changed the topic title to reflect recent discoveries.

---

### Post by FitDynamite on 2011-01-03
Just come across this post and like to share my experience here.

Ubuntu sees the wireless card, but for some reason it is disabled during the startup.

you can enable it by typing in the command line #nnmcli nm wifi on

To make it start during the start up, simply put the command in the local startup script. Sorry I don't know the better way - I am not familiar with the network settings on the Ubuntu... What is equivalent to /etc/sysconfig/network-scripts in RHEL?

Anyway here is my rc.local file:

#vi /etc/rc.local

/usr/bin/nmcli nm wifi on
exit 0

---

