---
title: "Very slow wireless in 12.04"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by kinkdxm on 2012-07-31
I have very slow wireless internet on my laptop (Dell XPS M1330) running Xubuntu 12.04.
When I'm booted into Windows 7 everything works great.
I've spent the last few days reading and trying different solutions found on the forums and AskUbuntu. None of them have worked for me. Any help would be greatly appreciated.

**SOLUTION:**
When laptop is running on AC internet speeds are normal.
Disable power management should resolve everything.

---

### Post by Matt12334 on 2012-07-31
> **kinkdxm said:**
> I have very slow wireless internet on my laptop (Dell XPS M1330) running Xubuntu 12.04.
When I'm booted into Windows 7 everything works great.
I've spent the last few days reading and trying different solutions found on the forums and AskUbuntu. None of them have worked for me. Any help would be greatly appreciated.
I've tried many things as well.  One solution that may work would be to write (gasp!) a small shell script that tells the computer to disable the wlan0 power management.  Do you know if the command
```
 sudo iwconfig wlan0 power off 
``` fixes your problem?

---

### Post by kinkdxm on 2012-07-31
When I run that I get an error

```
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.

```

Thanks for your reply!

---

### Post by madvinegar on 2012-07-31
Hi.

Please post the results of

```
lspci
sudo lshw -c network
sudo rfkill list all
```

---

### Post by kinkdxm on 2012-07-31
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```


sudo lshw -c network
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:c9:8a:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.43.162 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:80:db:a8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f1bf0000-f1bfffff

```

sudo rfkill list all
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by Matt12334 on 2012-07-31
> **kinkdxm said:**
> When I run that I get an error

```
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.

```Thanks for your reply!
Ya know, I guess I shouldn't assume that everybody's system is exactly like mine. So I guess you should post the output of 
```

sudo iwconfig

```so we can figure out what you need to type in.

By the way, I'm new to the whole linux thing, so I'm kinda figuring things out as I go. :D

---

### Post by kinkdxm on 2012-07-31
> **Matt12334 said:**
> Ya know, I guess I shouldn't assume that everybody's system is exactly like mine. So I guess you should post the output of 
```

sudo iwconfig

```so we can figure out what you need to type in.

By the way, I'm new to the whole linux thing, so I'm kinda figuring things out as I go. :D


sudo iwconfig
```
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"SHHHHHH"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=-53 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

I ***** out my mac address ;)

---

### Post by Matt12334 on 2012-07-31
> **kinkdxm said:**
> sudo iwconfig
```
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"SHHHHHH"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=-53 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```I ***** out my mac address ;)
It's probably not necessary to do so.  I honestly wouldn't know what to do with it even if I knew it. 
Back on-topic, are you connected with ethernet right now?

---

### Post by kinkdxm on 2012-07-31
> **Matt12334 said:**
> It's probably not necessary to do so.  I honestly wouldn't know what to do with it even if I knew it. 
Back on-topic, are you connected with ethernet right now?
HA! Neither would I ;)

Weirdly I only have access to WiFi at my house.

---

### Post by Matt12334 on 2012-07-31
> **kinkdxm said:**
> HA! Neither would I ;)

Weirdly I only have access to WiFi at my house.

Ah, okay.  The eth0 and eth1 thing kinda threw me off.  Well it looks like you already know how to disable your power management, so why don't you try turning it on, and then back off?  Sometimes random crap like that works. ;D

---

### Post by kinkdxm on 2012-07-31
> **Matt12334 said:**
> Ah, okay.  The eth0 and eth1 thing kinda threw me off.  Well it looks like you already know how to disable your power management, so why don't you try turning it on, and then back off?  Sometimes random crap like that works. ;D

I think that solved it.

I just installed SABnzbd from the PPA. Took forever due to my slow network speeds. My battery started getting low so I plugged my laptop in. I fired up SABnzbd to see how slow it would run. I was surprised to see that it was maxing out my internet connection.

So unless SABnzbd's dependencies magically fixed something having the laptop NOT on battery power resolved it. Come to think of it I think I've only been in front of my laptop on the couch running on battery. When It gets low I normally charge it on my desk.

Thanks for your help!

---

