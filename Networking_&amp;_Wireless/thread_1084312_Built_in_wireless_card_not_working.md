---
title: "Built in wireless card not working"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by theb@ssm@n on 2009-03-01
I can't get my laptop connected to my wireless network.  It has a built in wireless card.  It might not even be an ubuntu problem, because when I booted from a live cd of fedora I couldn't connect there either.

Anybody have any ideas?

---

### Post by Atrophy on 2009-03-01
Try this: First, find a wired connection. Connect to that, and then run your package manager and install all updates and program fixes and whatnot. Then open terminal and run 'sudo apt-get install linux-backports-modules-intrepid-generic' and reboot.

---

### Post by theb@ssm@n on 2009-03-02
> **Atrophy said:**
> Try this: First, find a wired connection. Connect to that, and then run your package manager and install all updates and program fixes and whatnot. Then open terminal and run 'sudo apt-get install linux-backports-modules-intrepid-generic' and reboot.

It didn't work.  Still can't connect

---

### Post by 5BallJuggler on 2009-03-02
open a terminal and type

lspci

post the output here.

---

### Post by theb@ssm@n on 2009-03-02
> **5BallJuggler said:**
> open a terminal and type

lspci

post the output here.

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
j

---

### Post by 5BallJuggler on 2009-03-02
> **theb@ssm@n said:**
> 
[B]
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/B]


this looks like your wireless card.

open the terminal again and type 

iwconfig

&

ifconfig

post the outputs here

---

### Post by Flyingjester on 2009-03-02
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177) here is a guide for your card.

---

### Post by theb@ssm@n on 2009-03-02
> **5BallJuggler said:**
> this looks like your wireless card.

open the terminal again and type 

iwconfig

&

ifconfig

post the outputs here

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ifconfig: 

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:8f:a2:8c  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe8f:a28c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13322855 (13.3 MB)  TX bytes:1198005 (1.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30172 (30.1 KB)  TX bytes:30172 (30.1 KB

---

### Post by 5BallJuggler on 2009-03-02
try to follow the link flyingjester has posted, if that does not work, add another post

---

### Post by theb@ssm@n on 2009-03-02
> **5BallJuggler said:**
> try to follow the link flyingjester has posted, if that does not work, add another post

I tried the link and it still does not work jordan@jordan-laptop:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.27-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko): Operation not permitted


If it helps my driver is working

jordan@jordan-laptop:~$ sudo ndiswrapper -l
[sudo] password for jordan: 
bcmwl5 : driver installed
	device (14E4:4318 ) present (alternate driver: ssb)

---

### Post by Ben Crisford on 2009-03-02
I've had the same problem as him.

Please help :S.

---

### Post by theb@ssm@n on 2009-03-02
> **Ben Crisford said:**
> I've had the same problem as him.

Please help :S.

It sucks doesn't it.

I don't know if this matters but I am running Intrepid Ibex

---

