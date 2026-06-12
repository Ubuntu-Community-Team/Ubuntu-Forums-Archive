---
title: "Linksys Issues"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Zahne on 2009-09-02
Hi,

I think this has come up a number of times but I'm having trouble with my Linksys Wireless - B PCI adapter. Ubuntu did not recognize it automatically. I couldn't find an answer upon googling. Perhaps I'm not asking the right question. Any input would be much appreciated.

---

### Post by Crafty Kisses on 2009-09-03
What are the results of the following commands?
```
lspci
lsusb
lshw -C network
```

---

### Post by Zahne on 2009-09-03
Here are the results. I replaced the name with "undisclosed."


```
undisclosed@undisclosed-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
02:09.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
02:0a.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
02:0b.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0d.0 Communication controller: Agere Systems LT WinModem
undisclosed@undisclosed-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
undisclosed@undisclosed-desktop:~$ lshu -C network
bash: lshu: command not found

```

---

### Post by Zahne on 2009-09-05
Did I miss type the last command?

---

### Post by cariboo on 2009-09-05
Yes you did  the correct command is:

```
sudo lshw -C network
```

You can copy the command and paste it directly in a terminal.

---

### Post by Zahne on 2009-09-05
Okay here's the result:

```
undisclosed@undisclosed-desktop:~$ sudo lshw -C network
[sudo] password for undisclosed: 
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 86
       serial: 00:15:e9:81:2f:df
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:af:63:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
```

Any further input on how to correct this would be appreciated.

---

### Post by Zahne on 2009-09-06
*BUMP*

I'd really appreciate some help with this issue.

---

### Post by Zahne on 2009-09-07
any input?

---

### Post by Zahne on 2009-09-13
*BUMP* any ideas? Does anybody use a Linsys Wifi PCI card that had this issue?

---

### Post by Ayuthia on 2009-09-13
You can first check and see if you can find a Broadcom b43 option in System->Administration->Hardware Drivers.  If it does not show up, you can try the following from the Terminal:
```
sudo apt-get install b43-fwcutter
```This command does require a working internet connection because it needs to download a firmware file.  The b43-fwcutter application takes some of the data from the firmware file to help make your wireless card work.

The 4303 card should be using the b43legacy module and seems to be rare in the Ubuntu community.  I don't recall seeing any using Jaunty so I am not for sure what your results will be.  If it still does not work, please come back again and post the results of:
```
lshw -C network
dmesg|grep b43
```
I am requesting the lshw -C network command again because after installing b43-fwcutter, you should have a different set of results from that command.  The dmesg command will help let us know if the b43legacy module is having problems getting loaded into Ubuntu.

Hopefully installing b43-fwcutter will help solve your problem.

---

### Post by Zahne on 2009-09-18
hmm i can't seem to get past the first step. Here's what I got:
```

E: Couldn't find package b43-fwcutter
```

---

