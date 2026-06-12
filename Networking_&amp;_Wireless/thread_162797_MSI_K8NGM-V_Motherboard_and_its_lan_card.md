---
title: "MSI K8NGM-V Motherboard and its lan card"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by yoramfr on 2006-04-19
Mother board:
MSI K8NGM-V
GEFORCE 6100
NFORCE MCP51
NFORCE 410

AMD-64

The lan card is on board by Nvidia.
I can't get the lan work.

What can I do?

I tried the Nvidia driver and it replied:

[IMG]http://forums.ort.org.il/files/30/2356484/2780027.png[/IMG]



Here is the lan card on XP:

[IMG]http://forums.ort.org.il/files/30/2356626/7752576.PNG[/IMG]


```


avi@avi:~$ sudo lspci
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 02f1 (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation: Unknown device 02fa (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation: Unknown device 02fe (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 02f8 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation: Unknown device 02f9 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation: Unknown device 02ff (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation: Unknown device 027f (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation: Unknown device 027e (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation: Unknown device 02fc (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation: Unknown device 02fd (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 02fb (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation: Unknown device 0242 (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation: Unknown device 0270 (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation: Unknown device 0261 (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation: Unknown device 0264 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation: Unknown device 026d (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation: Unknown device 026e (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation: Unknown device 0265 (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation: Unknown device 0266 (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation: Unknown device 026f (rev a2)
0000:00:10.2 Multimedia audio controller: nVidia Corporation: Unknown device 026 b (rev a2)
0000:00:14.0 Bridge: nVidia Corporation: Unknown device 0269 (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:04:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadca st Decoder (rev 01)
avi@avi:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:17:13:85:59
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x2000

avi@avi:~$ 


```

---

### Post by xtra on 2006-04-21
The network card is supported in 5.10.  Are you using dhcp?

Try shutdown the computer, unplug the powercable and then start it against.  if you are still not getting the dhcp setting, try run "sudo dhclient" in command line.

---

