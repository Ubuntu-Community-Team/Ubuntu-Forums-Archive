---
title: "no internet after eth0 was deleted (by mistake)"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by nanoblue on 2009-09-30
hi
i deleted my eth0 connection by mistake the got disconnected from the network although a new network automatically was formed(Auto Ethernet) i am connected to home network through a router. i ran the lshw -C network and got

*-network               
       
description: Ethernet interface
       
product: RTL-8139/8139C/8139C+
       
vendor: Realtek Semiconductor Co., Ltd.
       
physical id: 2
       
bus info: pci@0000:02:02.0
       
logical name: eth0
       
version: 10
       
serial: 00:0a:cd:0a:18:ba
       
width: 32 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list ethernet physical
       
configuration: broadcast=yes 
driver=8139too 
driverversion=0.9.28 
latency=32 
maxlatency=64 
mingnt=32 
module=8139too 
multicast=yes
  
*-network DISABLED
   (ALTHOUGH ENABLED ON THE PANEL)    
description: Ethernet interface
       
physical id: 1
       
logical name: pan0
       
serial: da:28:0c:98:55:a8
       
capabilities: ethernet physical
       
configuration: broadcast=yes 
driver=bridge 
driverversion=2.3 
firmware=N/A 
multicast=yes

thanks a lot for ur help

---

### Post by chili555 on 2009-09-30
eth0 was not deleted, or if it was, it came back automagically. Here it is:> logical name: eth0This:> *-network DISABLED
(ALTHOUGH ENABLED ON THE PANEL)
description: Ethernet interfaceRefers to pan0 which, I believe, is a bluetooth interface. At least at this time, we don't need or care about it. Please do these terminal commands and post the result. In some cases, the result may be nothing:```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 up
sudo dhclient eth0
sudo ethtool eth0
```Thanks.

---

### Post by nanoblue on 2009-10-01
hi chilli thanks for the reply

here is wat i got


kh@kh-desktop:~$ sudo /etc/init.d/NetworkManager stop
 
* Stopping network connection manager NetworkManager                    [ OK ] 


kh@kh-desktop:~$ sudo ifconfig eth0 up


kh@kh-desktop:~$ sudo dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 3245
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0a:cd:0a:18:ba
Sending on   LPF/eth0/00:0a:cd:0a:18:ba
Sending on   Socket/fallback
DHCPDISCOVER on 
eth0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

No DHCPOFFERS received.
No working leases in persistent database - sleeping.


kh@kh-desktop:~$ sudo ethtool eth0
Settings for eth0:
    
Supported ports: [ TP MII ]
    
Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    
Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    
Speed: 100Mb/s
    
Duplex: Full
    
Port: MII
    
PHYAD: 32
    
Transceiver: internal
    A
uto-negotiation: on
    
Supports Wake-on: pumbg
    Wake-on: d
    
Current message level: 0x00000007 (7)
    Link detected: yes

---

### Post by chili555 on 2009-10-01
Everything looks entirely normal until it doesn't connect. This is my favorite kind of problem: everything is perfect, except it just doesn't work!

Let's see if the kernel has anything to say. Please do:```
sudo cat /var/log/messages | grep eth0
sudo cat /var/log/messages | grep 8139too
```Thanks.

---

### Post by nanoblue on 2009-10-01
hi again 
don't wanna sound stupid but i did 8103 with too and without


	 	 kh@kh-desktop:~$ sudo cat /var/log/messages | grep eth0  
 [sudo] password for kh:  
 Oct  1 14:50:16 kh-desktop kernel: [  613.000061] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:50:28 kh-desktop kernel: [  625.000058] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:50:40 kh-desktop kernel: [  637.000059] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:50:52 kh-desktop kernel: [  649.000056] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:51:04 kh-desktop kernel: [  661.000055] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:51:28 kh-desktop kernel: [  685.664048] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:51:44 kh-desktop kernel: [  701.000054] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:52:20 kh-desktop kernel: [  737.000057] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:53:08 kh-desktop kernel: [  785.000166] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:53:20 kh-desktop kernel: [  797.000054] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:53:32 kh-desktop kernel: [  809.000055] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:53:44 kh-desktop kernel: [  821.000054] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:53:56 kh-desktop kernel: [  833.000060] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 14:56:50 kh-desktop kernel: [ 1007.000055] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 15:03:14 kh-desktop kernel: [ 1391.000058] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:14:45 kh-desktop kernel: [    2.602458] eth0: RealTek RTL8139 at 0xb800, 00:0a:cd:0a:18:ba, IRQ 17  
 Oct  1 19:14:52 kh-desktop kernel: [   20.771904] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:15:16 kh-desktop kernel: [   44.816024] NETDEV WATCHDOG: eth0 (8139too): transmit timed out  
 Oct  1 19:15:19 kh-desktop kernel: [   47.816061] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:15:31 kh-desktop kernel: [   59.816084] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:15:43 kh-desktop kernel: [   71.816063] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:16:13 kh-desktop kernel: [  101.816058] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:16:25 kh-desktop kernel: [  113.816062] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:16:37 kh-desktop kernel: [  125.816064] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:17:31 kh-desktop kernel: [  179.816080] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:17:43 kh-desktop kernel: [  191.816060] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:17:55 kh-desktop kernel: [  203.816060] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:19:55 kh-desktop kernel: [  324.000061] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:20:07 kh-desktop kernel: [  336.000063] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 Oct  1 19:20:19 kh-desktop kernel: [  348.000059] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1  
 

kh@kh-desktop:~$ sudo cat /var/log/messages | grep 8139  
 Oct  1 19:14:45 kh-desktop kernel: [    2.591403] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)  
 Oct  1 19:14:45 kh-desktop kernel: [    2.591471] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too  
 Oct  1 19:14:45 kh-desktop kernel: [    2.600756] 8139too Fast Ethernet driver 0.9.28  
 Oct  1 19:14:45 kh-desktop kernel: [    2.600818] 8139too 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 Oct  1 19:14:45 kh-desktop kernel: [    2.602458] eth0: RealTek RTL8139 at 0xb800, 00:0a:cd:0a:18:ba, IRQ 17  
 Oct  1 19:15:16 kh-desktop kernel: [   44.816024] NETDEV WATCHDOG: eth0 (8139too): transmit timed out  
 Oct  1 19:15:16 kh-desktop kernel: [   44.816026] Modules linked in: binfmt_misc bridge stp bnep input_polldev video output lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event bttv snd_seq snd_timer snd_seq_device videodev v4l1_compat ir_common compat_ioctl32 i2c_algo_bit v4l2_common videobuf_dma_sg iTCO_wdt videobuf_core btcx_risc snd iTCO_vendor_support psmouse tveeprom nvidia(P) soundcore ppdev intel_agp pcspkr serio_raw snd_page_alloc agpgart parport_pc parport shpchp 8139too floppy 8139cp mii fbcon tileblit font bitblit softcursor  
 

kh@kh-desktop:~$ sudo cat /var/log/messages | grep 8139too  
 Oct  1 19:14:45 kh-desktop kernel: [    2.591471] 8139cp 0000:02:02.0: This (id 

10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too  
 Oct  1 19:14:45 kh-desktop kernel: [    2.600756] 8139too Fast Ethernet driver 0.9.28  
 Oct  1 19:14:45 kh-desktop kernel: [    2.600818] 8139too 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 Oct  1 19:15:16 kh-desktop kernel: [   44.816024] NETDEV WATCHDOG: eth0 (8139too): transmit timed out  
 Oct  1 19:15:16 kh-desktop kernel: [   44.816026] Modules linked in: binfmt_misc bridge stp bnep input_polldev video output lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event bttv snd_seq snd_timer snd_seq_device videodev v4l1_compat ir_common compat_ioctl32 i2c_algo_bit v4l2_common videobuf_dma_sg iTCO_wdt videobuf_core btcx_risc snd iTCO_vendor_support psmouse tveeprom nvidia(P) soundcore ppdev intel_agp pcspkr serio_raw snd_page_alloc agpgart parport_pc parport shpchp 8139too floppy 8139cp mii fbcon tileblit font bitblit softcursor

---

### Post by chili555 on 2009-10-01
This bothers me a bit:> [ 2.591471] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too Yet the module is loaded up anyway:> [ 44.816026] Modules linked in: ...8139cp ...I wonder if they are fighting each other. Let's try an experiment by unloading 8139cp and see if we have a different result:```
sudo rmmod -f 8139cp
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 up
sudo dhclient eth0

```> 8103 with too and withoutPrecision is crucial, as you have discovered. Don't worry, we have all made this mistake; mistyping a command and being shocked at the lack of a meaningful result. I have, even...today!

---

### Post by nanoblue on 2009-10-01
donno but i think this looks better now didnt do anything else sould i restart or enable the network manager  

	 	 kh@kh-desktop:~$ sudo rmmod -f 8139cp  
 [sudo] password for kh:  
 

 kh@kh-desktop:~$ sudo /etc/init.d/NetworkManager stop  
  * Stopping network connection manager NetworkManager                    [ OK ]  
 kh@kh-desktop:~$ sudo ifconfig eth0 up  
 kh@kh-desktop:~$ sudo dhclient eth0  
 Internet Systems Consortium DHCP Client V3.1.1  
 Copyright 2004-2008 Internet Systems Consortium.  
 All rights reserved.  
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)  
 

 Listening on LPF/eth0/00:0a:cd:0a:18:ba 
 Sending on   LPF/eth0/00:0a:cd:0a:18:ba 
 Sending on   Socket/fallback  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5  
 DHCPOFFER of 192.168.0.172 from 192.168.0.1  
 DHCPREQUEST of 192.168.0.172 on eth0 to 255.255.255.255 port 67  
 DHCPACK of 192.168.0.172 from 192.168.0.1  
 bound to 192.168.0.172 -- renewal in 517741 seconds.

---

### Post by chili555 on 2009-10-01
Looks better? It looks terrific! You connected. Before you reboot, let's kick 8139cp out of school permanently. Please do:```
sudo gedit /etc/modprobe.d/blacklist
```If it shows as a new file, close *gedit*. Then do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```This may be a new file, but please go ahead with the edit. Add a single new line:```
blacklist 8139cp
```Proofread carefully, save and close *gedit*. 

Now reboot and go to Network Manager and see if you connect properly.

---

### Post by nanoblue on 2009-10-01
hi sorry but it didn't seem to work,although "connected" i still cant see other computers on the network nor am i connected to the internet...tried pinging but nothing worked.

---

### Post by chili555 on 2009-10-01
> although "connected"I don't quite understand. What tells you that you are connected? Please try:```
ping -c3 74.125.65.147
```Thanks.

---

### Post by nanoblue on 2009-10-01
the net manager icon on the upper panel states that i have an active wired network i'm sorry if this differs from actually being connected. regarding the pinging i got network unreachable for your address

thanks for ur time i deeply appreciate that

---

