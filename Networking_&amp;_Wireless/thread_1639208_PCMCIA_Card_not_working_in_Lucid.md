---
title: "PCMCIA Card not working in Lucid"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by AZBiker on 2010-12-06
Here's the dealy-o.  Card is a Netgear, computer says it's a BCM43XG REV01.

Card is functional but not working on my fresh Lucid install.

Here's what it says:

  	 	 	 	p { margin-bottom: 0.08in; }  derek@derek-laptop:~$ lspcmcia -v  
 Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0)  
 	Configuration:	state: on	ready: unknown  
 			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V  
   CardBus card -- see "lspci" for more information

---

### Post by chili555 on 2010-12-06
Well, that's strangely silent. Let's follow its recommendation. Please post:```
lspci -nn
```Thanks.

---

### Post by AZBiker on 2010-12-06
derek@derek-laptop:~$ lspci -nn  
 00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 650/M650 Host [1039:0650] (rev 80)  
 00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) [1039:0001]  
 00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] [1039:0962] (rev 25)  
 00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]  
 00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]  
 00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)  
 00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)  
 00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)  
 00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)  
 00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]  
 00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)  
 00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]  
 01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter [1039:6325]  
 02:00.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

---

### Post by AZBiker on 2010-12-06
p { margin-bottom: 0.08in; }  Here's the results of if and ipconfig, but they probably won't help much.



derek@derek-laptop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:0f:1f:b4:c9:ed   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:19 Base address:0x1800  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:244 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:244 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:19128 (19.1 KB)  TX bytes:19128 (19.1 KB)  
 

 derek@derek-laptop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.

---

### Post by chili555 on 2010-12-06
> Broadcom Corporation BCM43XG [14e4:4329] (rev 01)This device works with the driver modules b43 and ssb. It also requires firmware that is proprietary and therefor doesn't ship with the default install of Ubuntu. Is it possible to walk your laptop over to the router for just a few moments and get an ethernet connection? If so, go to System > Administration > Hardware Drivers (it may be Additional Drivers) and install the firmware. After you disconnect the ethernet, your wireless should be working.

---

### Post by AZBiker on 2010-12-06
I'll get an ethernet cable when I'm out then.  Thanks for your help!!!!

Derek

---

### Post by AZBiker on 2010-12-06
Made my first straight-through ethernet cable and got the necessary files. 

Thanks chili555!!!!!

If you're ever out my way, drop me a line and we'll go play with some tannerite.  ;)

Derek

---

### Post by chili555 on 2010-12-06
Awesome! Glad it's working.

Shall I bring a BMG 50?

---

### Post by AZBiker on 2010-12-09
Giggity giggity goo...oh yeah.:D

> **chili555 said:**
> Awesome! Glad it's working.

Shall I bring a BMG 50?

---

