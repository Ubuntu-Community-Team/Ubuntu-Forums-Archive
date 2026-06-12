---
title: "ndiswrapper vs native Linux driver...?"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by AdamShumpisxXx on 2009-05-03
I have a RT2860STA based PCI Wireless-N card for my desktop. I have the newest driver installed for it found here:

[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

I get kicked off my wireless network when I use more than 2 programs that use bandwidth (Firefox, Deluge, Pidgin usually). I can't reconnect to ANY wireless network after this happens until I restart my computer as it seems Ubuntu can no longer detect my wireless card.

Let me provide some back story. This started to become an issue after I reverted back to Intrepid after trying Jaunty and it failing horribly for me. Basically I wasn't going to settle for open source ATI drivers. Initially when I installed my wireless card driver for Intrepid (pre-Distro hopping) the driver was labeled as being a 2008 release instead of the one they give out now which is a 2009 release. With the 2008 release I was using WICD with absolutely NO PROBLEMS. Now with this new 2009 driver WICD doesn't even let me connect at all and just infinite loops every time I choose my network and I'm forced to use the default manager.

What I'm asking is...should I switch up to using ndiswrapper or is there something I can do with what I have? Is there perhaps a way to downgrade back to the 2008 driver (I can't find it).

I should let everyone know that the only source of the internet I have is my wireless network and I do not have the option to connect directly into my router using a cable. Thank you very much in advance!!! PLEASE HELP!

---

### Post by AdamShumpisxXx on 2009-05-03
Adding information:

```
adam@ADAMXXX-INTREPID:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]
01:00.1 Display controller: ATI Technologies Inc Device 7264
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:01.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
03:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

```
adam@ADAMXXX-INTREPID:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:25:a2:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:676 (676.0 B)  TX bytes:676 (676.0 B)

ra0       Link encap:Ethernet  HWaddr 00:02:6f:54:f7:5b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe54:f75b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2058443 errors:233 dropped:0 overruns:0 frame:0
          TX packets:655121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1469996515 (1.4 GB)  TX bytes:74273365 (74.2 MB)
          Interrupt:21
```

```
adam@ADAMXXX-INTREPID:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"XXX"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:BF:16:E7:48   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-56 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

I hope that's everything you guys would need. If you need anything else let me know. Thank you again!

---

### Post by AdamShumpisxXx on 2009-05-04
Bump before bed. Hahaha!

---

### Post by AdamShumpisxXx on 2009-05-04
Bump.

---

### Post by AdamShumpisxXx on 2009-05-06
Who do I have to beg? I'll do it. Hahahaha.

This problem really sucks.

---

