---
title: "Network connection dies..."
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by soulbarn on 2006-03-08
Hi - I can get my wireless card to connect as eth0 to both the internet and my local (mac) network through my netgear router...however, within five to ten minutes I lose connectivity - the wireless card still indicates that it is active, but I can't connect to websites or my local servers. If I go into the network settings, reselect the wireless eth0 connection, it comes back - but dies again, within 5-10 minutes.

None of the macs on my network have any connectivity probs with the router.

thanks

dan

---

### Post by thnogueira on 2006-03-08
Are you shure eth0 is the name of your wireless adapter? It's usually used for wired network adapter. Please post the output of
ifconfig and lspci commands.

---

### Post by soulbarn on 2006-03-08
ok, here are the outputs - thanks:

dan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:35:3E:F5:A8
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe3e:f5a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:730 errors:0 dropped:6 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:117722470 (112.2 MiB)  TX bytes:1608518 (1.5 MiB)
          Interrupt:10 Base address:0x8000 Memory:d0200000-d0200fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13873480 (13.2 MiB)  TX bytes:13873480 (13.2 MiB)


AND


dan@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 855GME GMCH Host-to-AGP Bridge (Virtual PCI-to-PCI) (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
0000:02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
0000:02:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)

BTW, eth0, in Network Settings, identifies as wireless.

thanks again,

dan

---

### Post by thnogueira on 2006-03-09
How did you install the wireless adapter, was it recognized by linux? Did you use ndiswrapper? In this case, was there another driver avaiable? 

Just to be sure: Is there any wired connection between the notebook and the router?

---

