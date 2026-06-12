---
title: "Wireless Drops every few minutes"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by glantela on 2009-03-25
Hi Everyone, 

My wireless internet works, but the problem is, it drops randomly every couple of minutes, without the network manager showing any change.  All i need to do to fix it is to click on my wireless network to reconnect, but it always seems to drop and it's pretty annoying... does anyone have a fix for this?

My lspci:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

My iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"tmak"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:91:F6:C7:61   
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-74 dBm  Noise level=-94 dBm
          Rx invalid nwid:12888  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


I'm wondering if it's something to do with that invalid nwid: 12888 thing....  It keeps going up everytime I type in iwconfig...

Thanks

---

### Post by alimahmoudy on 2009-03-25
Well i don't know about you, but i used to have this when i installed my atheros drivers from the cd that came with the usb wireless card. 
I deleted these drivers and used the ones provided by ubuntu, works great !

---

### Post by glantela on 2009-03-25
Yea, i'm using the same one though...

---

### Post by BkkBonanza on 2009-03-26
-74 db is a fairly weak signal. Move closer or improve the antenna and see if you get better stability. Signals can often go up and down by 10db or so and if this one drops down like that you'd likely disconnect.

---

### Post by glantela on 2009-03-26
Yes it's true, i do have a weak signal (15-30%) but shouldnt it show up on the network manager that it has dropped/disconnected?

---

### Post by superprash2003 on 2009-03-27
when you experience the wireless drop, try pinging your router and post output..

---

### Post by lisati on 2009-03-27
Another possibility: Anyone else in the area using wifi on the same channel? I was getting seemingly random disconnections, and spotted a neighbour's access point broadcasting on the same channel as I was using when checking out some semi-retired gear. Since changing the cannel on my router things seem to have come right.

---

### Post by glantela on 2009-03-29
This is pinging the router gives me... 

ari@lobo:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.199 icmp_seq=9 Destination Host Unreachable

Another time i left it pinging while i was connected...

64 bytes from 192.168.0.1: icmp_seq=300 ttl=64 time=1.19 ms
64 bytes from 192.168.0.1: icmp_seq=301 ttl=64 time=1.29 ms
64 bytes from 192.168.0.1: icmp_seq=302 ttl=64 time=0.711 ms
64 bytes from 192.168.0.1: icmp_seq=303 ttl=64 time=0.765 ms
From 192.168.0.199 icmp_seq=363 Destination Host Unreachable
From 192.168.0.199 icmp_seq=364 Destination Host Unreachable

I'll try the channel thing later and see what happens...

---

### Post by glantela on 2009-03-29
Changing the wireless channel seemed to work pretty well- i am satisfied.

Thanks for everyone's help :)

---

