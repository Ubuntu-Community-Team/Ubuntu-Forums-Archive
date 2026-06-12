---
title: "Wifi: Gutsy - Yes, Jaunty - No!"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Lutin on 2009-08-11
Cannot get my head around this one, so I'll see if anyone else can help.

Dell Latitude D400, running Gutsy Gibbon and the Wifi is working fine.

Install Jaunty alongside Gutsy (just in case) and I cannot get the Wifi to connect to my router! It can see it alright, but simply refuses to connect!

I have tried Network Manager and Wicd, and I simply cannot get a connection. Both NM and Wicd can see my network, and a few others too, but neither will connect.

Any suggestions anyone?

---

### Post by The Toxic Mite on 2009-08-11
Hey! Can you post the results of the following Terminal commands please?:
 
```

sudo lshw -c network
lspci
iwconfig
ifconfig

```Thanks :D

EDIT: If it's a USB dongle, type in the following command:

```

lsusb

```

... instead of:

```

lspci

```

---

### Post by Lutin on 2009-08-11
Okay here goes -

Output from **sudo lshw -c network** -

########:~$ sudo lshw -c network
[sudo] password for ######: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:5b:bd:2e
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.11 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:2c:f4:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 86:50:ef:5e:eb:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
########:~$ 



Output for **lspci** -

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
01:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
01:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
01:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)


Output for **iwconfig** -

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"#################"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:E3:D1:01:8F   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=81/100  Signal level:-45 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Finally, output for **ifconfig** -

eth0      Link encap:Ethernet  HWaddr 00:0b:db:5b:bd:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:2c:f4:e1  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe2c:f4e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1101 (1.1 KB)  TX bytes:4738 (4.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-2C-F4-E1-34-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



So, as far as I can work out, the driver is loading properly and everything here seems to be okay.

As I said, running Gutsy Gibbon, wireless connects no problem, but on Jaunty - no dice. And my own and the neighbours networks are detected, but just cannot connect.

I'm going to do the above on Gutsy, just to see if there is a glaringly obvious difference.

Thanks for the interest in my problem, by the way. :-)

---

### Post by overdrank on 2009-08-11
Hi and I have a similar card BCM4306 and I enabled the backports in Jaunty then reinstalled the wireless drivers from hardware manager and it worked better. :)

---

### Post by The Toxic Mite on 2009-08-11
> **overdrank said:**
> Hi and I have a similar card BCM4306 and I enabled the backports in Jaunty then reinstalled the wireless drivers from hardware manager and it worked better. :)

My wireless card is a BCM4306 too, and it does show wireless networks but I can't connect for some reason.

I will post this in a thread of it's own and will put the link here :)

EDIT: Link to my new thread: [http://ubuntuforums.org/showthread.php?p=7768003#post7768003](http://ubuntuforums.org/showthread.php?p=7768003#post7768003)

:D

---

### Post by Lutin on 2009-08-12
Success! Followed the instructions in this thread -

[http://ubuntuforums.org/showthread.php?t=1156441&highlight=wifi](http://ubuntuforums.org/showthread.php?t=1156441&highlight=wifi)

and can now connect using WifiRadar. :-)

---

