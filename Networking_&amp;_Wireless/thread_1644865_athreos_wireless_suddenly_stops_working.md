---
title: "athreos wireless suddenly stops working"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by adityadeva on 2010-12-13
Hi all, 

I'm using a compaq CQ50 AU 106 laptop with AMD athlon X2(1.9 GHz)and 3 gb ram. 

I was running an Ubuntu only installation of 10.04 and 10.10 (both 32bit) and a Kubuntu 10.04 (64 bit).

My wireless card - Athreos 5007 card was working very satisfactorily, till one day the laptop shutdown/hibernated automatically due to low battery. after this issue, on the next boot I got my wireless card not getting up. I tried to enable it from /var/lib/Networking/networking.state file. I could make 'wireless=false' to 'wireless=true' but the value would go back to false. finally I had to install a copy of win7 :confused: to check whether the card is working or not. It is working in win7 but I have to manually push the wireless button after I boot into the win7 desktop. However this option is not working in linux. Pls help. pls find my linux command outputs/diagnostics

solar@Compaq-Presario-CQ50-Notebook-PC:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

===================================================



solar@Compaq-Presario-CQ50-Notebook-PC:~$ ifconfig -a
eth6      Link encap:Ethernet  HWaddr 00:1d:72:66:2f:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1776 (1.7 KB)  TX bytes:1776 (1.7 KB)

wlan1     Link encap:Ethernet  HWaddr 00:22:68:92:cd:a2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
============================================================================
solar@Compaq-Presario-CQ50-Notebook-PC:~$ sudo ifconfig wlan1 up
[sudo] password for solar: 
SIOCSIFFLAGS: Operation not possible due to RF-kill

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

I never wanted to Run M$ product but I am forced to now. I donot want any other linux distro either so Ubuntu Brothers pls help

---

### Post by adityadeva on 2010-12-13
$sudo rfkill unblock wifi

has solved the problem temporarily.

I've added the line in /etc/rc.local in case the problem persist.

Now wifi is running fine like a thoroughbred race horse

---

