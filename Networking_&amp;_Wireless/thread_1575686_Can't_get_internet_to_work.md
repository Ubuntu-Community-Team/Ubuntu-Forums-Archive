---
title: "Can't get internet to work"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by karro on 2010-09-16
It seems like ubuntu can't find mye wireless network card. I have ubuntu 10.04

when I type ifconfig the output is this

eth0          Link encap: Ethernet HWaddr 20:cf:30:01:9d:d2
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                            TX  packets:0 errors:0 dropped:0 overruns:0 carrier:0
                            collisions:0 txqueuelen:1000
                            RX bytes:0 (0.0B)  TX bytes:0 (0.0B)
            Interrupt:29

lo                     Link encap: Local Loopback
                            inet addr: 127.0.0.1  Mask:255.0.0.0
            inet6 addr:  : :1/128  Scope: Host
                            UP LOOPBACK RUNNING MTU:16436 METRIC:1
                            RX packets:172 errors:0 dropped:0 overruns:0 frame:0
                            TX  packets:172 errors:0 dropped:0 overruns:0 carrier0
                            collisions:0 txqueuelen:0
                            RX bytes:13312 (13.3 KB)  TX bytes:13312(13.3KB)


Please help me!!

---

### Post by dineshs on 2010-09-16
Please post the result of```
sudo lshw -C network
```

---

### Post by karro on 2010-09-16
PCI (sysfs)  

  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:01:9b:d2
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

---

### Post by Iowan on 2010-09-16
Any idea what chipset is in the machine? Looks like Ubuntu couldn't tell.

---

### Post by karro on 2010-09-17
No. I'm not sure. It's an asus Eee 1001px.



systemtypeNetbook 
 
  Prosessor 
  
  64-bits databehandling 
 Ja 
 
  Prosessor 
 Intel Atom N450 / 1.66 GHz 
 
  RAM 
  
  Installed size 
 1 GB / 2 GB (maks.) 
 
  Tecnology
 DDR2 SDRAM - 667 MHz 
 
  Lager 
  
  Harddrive 
 160 GB - Serial ATA-150 
 
  **Internet connection**
 
  wireless LAN-support 
 yes
 
 
  

 Ethernet, Fast Ethernet, IEEE 802.11b, IEEE 802.11g 
 
  adapted standards

 IEEE 802.11b, IEEE 802.11g 
 


 Serielt ATA-grensesnitt 
 Serial ATA-150 
 
  Type 
 Serial ATA 
 
  Video 
  
  Graphical prosessor

 Intel GMA 3150 Dynamic Video Memory Technology 4.0 
 




Memory 
 
interface2 x Hi-Speed USB - 4 pin USB Type A 
1 x skjerm/video - VGA - 15-pin HD D-Sub (HD-15) 
1 x hodetelefoner - utgang - stereo minijack 3,5 mm 
1 x mikrofon - inngang - minijack 3,5 mm 
1 x internet - Ethernet 10Base-T/100Base-TX - RJ-45





[SIZE=4]I[SIZE=2] hope this will help[/SIZE][/SIZE]

---

### Post by MaindotC on 2010-09-17
For future reference please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) as it has a flow of several commands to help you determine what to do.  However, this does look like it may require some extra help.  I know dineshs had you use the lshw command so I'm not certain this will be any better, but please show:```
lspci 
``` Please be sure to browse the man page of every command we ask you enter so you know what it is we are asking you to do, and also so you can help others in the future :D

I browsed the manual on ASUS's site.  Doesn't seem to be a whole lot of support for Linux but there is a utility and BIOS updates you can use.  Be sure to check those out.

---

### Post by karro on 2010-09-17
Tanks=D

I will try the trubleshooting guide as well! 



Her's the putput from lspci.


00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)

---

### Post by MaindotC on 2010-09-17
> **karro said:**
> 02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)

Please post your shell output in [code] tags from now on.  That's definitely your wireless adapter, and what lspci does is look in a file called libpci where all of the possible hardware attributes are defined.  Apparently there is no entry for this one, or it's giving lspci output that it can't narrow any further than identifying it as Atheros.

[This is what you want to research](http://is.gd/fffHB) and if you go through some of the results you'll see some solutions - the first one I see using ndiswrapper.

---

### Post by bkratz on 2010-09-17
This seems to be the same one ( I say that because the indication seems to be the same ) 168c:002c just more complete yours didn't say 168c so not positive, but most likely. Anyway look at the whole thread, pay particular attention to post 9 and see if it helps.

[http://ubuntuforums.org/showthread.php?t=1369304](http://ubuntuforums.org/showthread.php?t=1369304)

---

