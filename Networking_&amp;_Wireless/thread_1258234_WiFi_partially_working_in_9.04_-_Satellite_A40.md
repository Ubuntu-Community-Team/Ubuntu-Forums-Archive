---
title: "WiFi partially working in 9.04 - Satellite A40"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by Devon788 on 2009-09-04
Hi all, I have spent all week trying to troubleshoot this issue and I give up, I'm asking for help.....

Here's my hardware:

WLAN Card: PA3171U-1MPC

Laptop Model:  Toshiba Satellite PSA40C-004E4


The issue:

I recently wiped XP off the machine, and installed Jaunty. I am very familiar with linux, so it was an easy transition except for one problem...the WiFi card. It can see all networks in range, it can connect to my network (sometimes), it can get an IP from the router's DHCP pool(which has a limited range due to a few static addresses). I have tried several modules as well as several windows drivers through ndiswrapper.

I will post the results of lspci, lsmod, ifconfig and iwconfig as soon as I can.

FYI, I am using Wicd as my network manager, as with network-manager I couldn't connect at all!

Cheers!

---

### Post by Devon788 on 2009-09-04
The results:

devon@devon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"343_Divison_Apt_2"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:3
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



devon@devon-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:0d:46:9d:ca  
          inet addr:192.168.2.69  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe46:9dca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3929 (3.9 KB)  TX bytes:1746 (1.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:bb:96:1a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xc100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)


devon@devon-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

---

### Post by Devon788 on 2009-09-05
Anyone?

---

### Post by Devon788 on 2009-09-06
can anyone give me some sort of guidance with this issue?

---

