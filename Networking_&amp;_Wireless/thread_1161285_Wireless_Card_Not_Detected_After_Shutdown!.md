---
title: "Wireless Card Not Detected After Shutdown!"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by smithwaysecurity on 2009-05-16
Hello everyone
and little new to Linux but i have a small issue i can't seem to figure out.

Just Last night i shutdown my laptop for the night today i went to turn it on and i got no wifi i tryed everything from ifconfig  and wlan0 which should show their is now not. Also the network manger only showing me connected from a wire connection eth0 so i print u the resluts of what I got here:

james@CIA-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:4e:d9:06  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe4e:d906/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1290494 (1.2 MB)  TX bytes:320535 (320.5 KB)
          Interrupt:253 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

james@CIA-laptop:~$ ifconfig wlan0  up
wlan0: ERROR while getting interface flags: No such device
james@CIA-laptop:~$ 


james@CIA-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

james@CIA-laptop:~$ 

james@CIA-laptop:~$ lspci
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
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I am able to see the Wifi Card in the lspci comand but for some werd reason it's like ubuntu  can't pick it up again or let me config it hmmm I running a Hp G60 with ubuntu9.04

Could some one plze help me fix this problem I sure i not the only one that this has happend to.
Thanks everyone James

---

### Post by nothingspecial on 2009-05-16
Same thing here.

```
sudo nano /etc/modules
```

type ath5k at the bottom of the file

Ctrl O (that`s a capital o), Enter, Ctrl X

Reboot

That fixed it for me hope it does for you.

---

### Post by smithwaysecurity on 2009-05-17
[B]Issue solved re installed the madwifi drivers and configure it differently.
Thanks guys for your help I wish I seen the post sooner tho hours of work it took to get things working.
[/B]

---

