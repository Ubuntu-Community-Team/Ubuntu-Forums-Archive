---
title: "Wireless Keeps Dropping"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by r7069c on 2011-02-08
I installed ubuntu 10.10 on my gateway laptop two weeks ago. I can boot into ubuntu, winxp or win7. Everything was working perfectly until yesterday. I made no system changes but my wireless connection to the internet is failing only in Ubuntu. I am connecting to the router. But after a couple minutes I lose internet. This happens every time I reboot. It will connect for about a minute or two then all of the sudden no internet. The connection says it remains but i cant connect to the internet or router after a couple minutes. Ive tried rebooting. Ive tried wicd.
When I boot into win xp on the same laptop I dont have any issues. I'm thinking I may need to reinstall the drivers for the wireless card buy I am new to linux and have no idea how to.
Any Ideas or suggestions would be appreciated
thanks

---

### Post by P4man on 2011-02-08
Can you open a terminal and provide the output of 

```
sudo rfkill list
```

If you see anything blocked there, try

```
sudo rfkill unblock all
```

If that doesnt help, please post the output of

```
ifconfig

```and
```
lshw -C network
```

---

### Post by r7069c on 2011-02-08
Here it is. Thanks
[B]sryan@ryan-MT6705:~$ sudo rfkill list
[sudo] password for ryan: 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ryan@ryan-MT6705:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:c6:ce:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2384 (2.3 KB)  TX bytes:2384 (2.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:e2:53:87  
          inet addr:192.168.5.100  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fee2:5387/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10714631 (10.7 MB)  TX bytes:1766679 (1.7 MB)

ryan@ryan-MT6705:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c6:ce:3d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes
       resources: irq:41 memory:d2000000-d2003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:c0:a8:e2:53:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.35-25-generic firmware=N/A ip=192.168.5.100 multicast=yes wireless=IEEE 802.11bg
ryan@ryan-MT6705:~$ [/B]




> **P4man said:**
> Can you open a terminal and provide the output of 

```
sudo rfkill list
```

If you see anything blocked there, try

```
sudo rfkill unblock all
```

If that doesnt help, please post the output of

```
ifconfig

```and
```
lshw -C network
```

---

### Post by P4man on 2011-02-08
That all looks pretty normal. 
Is this an internal card or an USB stick?

Either way, can you also post the output of:

```
lspci

```

```
lsusb
```

(and please use [ CODE ] tags around the output)

Also, can you connect an ethernet cable temporarily, and update your ubuntu?

---

### Post by r7069c on 2011-02-08
When I ran those commands I was on the internet. It stopped working right after I POSTED.
Here are the other commands. It's like I got a virus. 
Should I repost the earlier commands while its stopped working?

ryan@ryan-MT6705:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
ryan@ryan-MT6705:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 003: ID 059b:0370 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ryan@ryan-MT6705:~$


> **P4man said:**
> That all looks pretty normal. 
Is this an internal card or an USB stick?

Either way, can you also post the output of:

```
lspci

```

```
lsusb
```

(and please use [ CODE ] tags around the output)

Also, can you connect an ethernet cable temporarily, and update your ubuntu?

---

### Post by r7069c on 2011-02-08
I am on internal wireless card

---

### Post by r7069c on 2011-02-08
[code]teha;lsj
;sdfkldfjm
;dsf;kjdf
;dsf;smfd;jmflds[code]

---

### Post by r7069c on 2011-02-08
lol let me try that again. ```
testing code quotes
```

---

### Post by r7069c on 2011-02-08
```
yan@ryan-MT6705:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```


```
yan@ryan-MT6705:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 003: ID 059b:0370 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ryan@ryan-MT6705:~$
```

---

### Post by r7069c on 2011-02-08
When I tried to update ubuntu thru System>Administration>Update Manager I got an error message that said I had no internet connection even though I was on the internet. This thing is screwy. I rebooted with just the ethernet connection and I was not able to connect to the internet. I switched back to wireless and it gets on but then goes down again.

---

### Post by P4man on 2011-02-09
If neither wired nor wireless is working, I wonder if the problem is not somewhere else.

Can you ping your router?
If you lose wireless, then turn wireless off and on, does it appear to connect again, and do you get an IP address?

If the answer to the above is twice yes, then I would suggest trying to use different DNS server, like google's DNS (8.8.8.8 and 8.8.4.4). You can also try disabling IPv6:
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

