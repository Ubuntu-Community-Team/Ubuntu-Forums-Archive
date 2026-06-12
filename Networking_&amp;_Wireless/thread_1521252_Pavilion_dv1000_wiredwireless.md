---
title: "Pavilion dv1000 wired/wireless"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by raphytaffy on 2010-06-30
Hi all, just installed Ubuntu 10.04 LTS onto this laptop and I can't get the wired or wireless to work. Networking is enabled as is wireless. I don't really know any Linux tricks, so I was hoping just having those two enabled would get it working. Any help is greatly appreciated. Thanks!

---

### Post by ajgreeny on 2010-06-30
Lets see the output of ```
lspci
``` in terminal, please.  That will tell us what your network card and adapter are, and perhaps give some clues about fixing your problem.

---

### Post by raphytaffy on 2010-06-30
Here's the output I get in terminal:

```
$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
```

---

### Post by ajgreeny on 2010-06-30
Most Intel wireless cards work OK, so I'm surprised your machine does not connect, but accept that is no help.

I am even more surprised that you wired connection is not working as that really is very unusual.

Can you now post the output of ```
ifconfig
```which may give more clues.

Did networking work OK in the live CD or did you not try that first?

---

### Post by raphytaffy on 2010-06-30
Scratch that, wired network works. Ran Update Manager and afterwards wireless is still not working. Here is the output from ifconfig:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:8c:50:08  
          inet addr:192.168.1.90  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe8c:5008/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:776713 (776.7 KB)  TX bytes:174871 (174.8 KB)
          Interrupt:16 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:4e:83:51  
          inet6 addr: fe80::212:f0ff:fe4e:8351/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6204 (6.2 KB)  TX bytes:3652 (3.6 KB)
          Interrupt:18 Base address:0x6000 Memory:e0206000-e0206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5680 (5.6 KB)  TX bytes:5680 (5.6 KB)
```

---

### Post by raphytaffy on 2010-07-01
Bump.

---

### Post by raphytaffy on 2010-07-02
Bump.

---

### Post by raphytaffy on 2010-07-06
Bump. Still looking for a solution.

---

