---
title: "Need help connecting PC to Wireless"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by ChinoCharles on 2009-09-06
Hey everyone.  I'll preface this by saying I'm a total Linux noob, which is why I installed Ubuntu on my home PC.  I'm a web designer in a Mac/Linux environment and I need to learn.  I was disappointed to see that my wireless connection didn't work, though.  After 2 days of reading, apparently I'm not the only one that runs into this.  I was hoping some of you guys with a lot more knowledge could help me fix this today.  Its an HP Media PC w/ a Phenom processor.

I did install wicd.  My card is picking up all three available networks.  The one I need to connect to uses WPA2.  Connection attempts hang at obtaining the IP address.

```


Version:1.0 StartHTML:0000000167 EndHTML:0000007672 StartFragment:0000000457 EndFragment:0000007656                                   

 chinocharles@chinocharles-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"  
           Mode:Auto  Frequency=2.462 GHz  Access Point: 00:1F:F3:C2:23:0C    
           Bit Rate=1 Mb/s    
           RTS thr:off   Fragment thr:off  
           Link Quality=10/100  Signal level:-82 dBm  Noise level:-87 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 pan0      no wireless extensions.  
 

 chinocharles@chinocharles-desktop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:1f:c6:89:e7:7b   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:250 Base address:0x4000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:44 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:44 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:3424 (3.4 KB)  TX bytes:3424 (3.4 KB)  
 

 ra0       Link encap:Ethernet  HWaddr 00:16:44:cf:0e:24   
           inet6 addr: fe80::216:44ff:fecf:e24/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:42190 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:14740 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:9465275 (9.4 MB)  TX bytes:0 (0.0 B)  
           Interrupt:16  
 

 ra0:avahi Link encap:Ethernet  HWaddr 00:16:44:cf:0e:24   
           inet addr:169.254.3.248  Bcast:169.254.255.255  Mask:255.255.0.0  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           Interrupt:16  
 

 chinocharles@chinocharles-desktop:~$ lspci  
 00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)  
 00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)  
 00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)  
 00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)  
 00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)  
 00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)  
 00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)  
 00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)  
 00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)  
 00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)  
 00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)  
 00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)  
 00:09.0 RAID bus controller: nVidia Corporation Device 0ad8 (rev a2)  
 00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)  
 00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)  
 00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)  
 00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)  
 00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller 
 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control  
 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control  
 01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)  
 02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT 512 (rev a2)  
 04:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)  
 05:00.0 Network controller: RaLink RT2860  
 


```

---

### Post by yeats on 2009-09-06
Sounds like all is well on your computer's end.  I have this problem on one of my computers at my in-laws' house.  In Windows, the wifi works fine, but when I reboot into Ubuntu (same machine), I can't get an IP.  It could be that the router is blocking your computer because of a hostname change?  Just a thought... It *does* sound like the issue is on the router's end.

---

### Post by ChinoCharles on 2009-09-06
OK, I'll look into that soon and report back.  Thanks for the reply.

---

### Post by azahari on 2009-09-07
yeahh. i have the same problem.
anyone has idea how to get connected??

---

### Post by jward3010 on 2009-09-07
Can you set a manual IP for that particular wireless network and see if you have connectivity?

If you're not sure about this, let me know.

---

### Post by ChinoCharles on 2009-09-09
Well, after a little more searching today I found the answer to my issue.  Its so simple it makes me want to rack my head against the wall.  I needed the Linux driver for my wireless card.  It didn't occur to me that that could be the issue because it was seeing the networks and attempting to connect, but I saw another thread that outlined installing the driver for my card and tried that and voila, im downloading system updates now.

Thanks for the help everyone.

---

