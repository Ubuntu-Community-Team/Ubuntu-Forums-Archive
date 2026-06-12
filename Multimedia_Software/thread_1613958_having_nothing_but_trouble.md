---
title: "having nothing but trouble"
date: 2010-11-05
forum: Multimedia Software
---

### Post by h4x0l2 on 2010-11-05
Ok... the install of 10.4 was fine. up and running a day and a half. I couldn't get my wireless to work even after 8 hours of trouble shooting. No internet on this pc is a no go. So I decided to download and try mandriva. Cd burned, restarted and put the cd in. The computer goes through the initial boot, and before it gets to the ubuntu studio or mandriva install screen, the monitor loses signal and I am left with no display. So I ctrl+alt+del to reboot, pull the mandriva cd out, and it still shuts off the screen.

My questions: how do I fix the screen problem
How am I supposed to get the zonet zew2500p to work (I already have tried every thread of advice from the forum that I could find)
And is this operating system my only option for pro audio on linux? 

If I can get it to work properly, id keep it. This has been the most frusterating thing since vista.

Thanks in advance.



I reinstalled Ubuntu Studio 9.1

---

### Post by sikander3786 on 2010-11-05
For question regarding Mandriva, it would be better to try their forums as you'll find more experience there.

Regarding your zonet zew2500p, it is based on RT73 and this thread might help you.

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Sometimes the wireless drivers can simply be installed from Hardware Drivers under System > Administration menu. All you need to do is to connect your system via ethernet cable to the internet and the drivers pop in there. Don't know if zew2500p is presented there (??).

---

### Post by h4x0l2 on 2010-11-05
Thanks for the reply.i tried that forum step by step with no luck. 

I might have to just call a buddy of mine to help out with this thing.

---

### Post by cchhrriiss121212 on 2010-11-05
> And is this operating system my only option for pro audio on linux? 
To put it simply: no. You can download just about any linux OS and use it for pro audio, as all the programs included on Studio are available everywhere else. The programs you find in studio are each developed from individual teams of programmers and are all open source so you can install them anywhere you like. 

This is both the benefit and the downside of linux, you have freedom to make your own system exactly the way you like it, but you also have to spend the time learning just how to do it. What Studio (and regular Ubuntu) does is gather the best of these packages together into an OS that is aimed at pleasing new users so they don't have to learn.

To address your main point, Studio does not come with any network manager installed though one is included on the disk:
 [http://ubuntuforums.org/showthread.php?t=1610307]("http://ubuntuforums.org/showthread.php?t=1610307")

---

### Post by h4x0l2 on 2010-11-05
lspci

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
03:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

```

```
ndiswrapper -l
rt2500 : driver installed

```


ifconfig 


```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:01:9e:b4  
          inet addr:(edit)  Bcast:(edit)  Mask:255.255.255.0
          inet6 addr:(edit) Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9014242 (9.0 MB)  TX bytes:654583 (654.5 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:c0:75:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-A1-B0-C0-75-5C-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



thats all the outputs...

---

