---
title: "Wireless Network detected - can't connect Linksys WMP54G"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by oogyboogawa on 2012-05-04
I'm fairly noobish with Linux, at least as far as using the terminal goes as well as troubleshooting.  But I just put a wireless card in my decktop and can detect the network but cannot connect.  I know I"m not too far away because the computer and router are almost touching lol.

Connection works hardwired and I know that the wireless signal on the router works because I can use it on my laptop.

I'm not sure what information you guys need, but here are some common commands I saw people asking for when I was looking through other threads on this forum:
```

warren@Warren-Desk:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

```
warren@Warren-Desk:~$ sudo iwlist scan
[sudo] password for warren:
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:BA:B5:0E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"tags"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000cde7be64
                    Extra: Last beacon: 772ms ago
                    IE: Unknown: 000474616773
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0712465220010D14010D1401071408060A010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010910400

eth0      Interface doesn't support scanning.
```


```
warren@Warren-Desk:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
warren@Warren-Desk:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:fd:26:d2  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fefd:26d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:176947298 (176.9 MB)  TX bytes:7153942 (7.1 MB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1568491 (1.5 MB)  TX bytes:1568491 (1.5 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:fe:cc:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
warren@Warren-Desk:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:06.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
```


Let me know if you need anything else!

---

### Post by oogyboogawa on 2012-05-05
Anyone?  If I didn't provide the right information just let me know and I'll try to get it for you! Thanks!

---

### Post by chili555 on 2012-05-05
I notice your ethernet is connected and has an IP address. Network Manager will default to wired if it's available and not use wireless. Please detach the ethernet cable, wait a minute or two for NM to notice the change in state and click the NM icon and try to connect. Are you challenged for your (very insecure) WEP password? Does it try? What messages are here?```
dmesg | grep -e rt6 -e rt2
```

---

### Post by oogyboogawa on 2012-05-05
Yeah, that is one thing I tried last night - but doing it again just incase :)

It waits for a while trying to connect and eventually asks for the WEP key, after entering it it never connects.  I have also tried disabling WEP in the router and connecting (after unplugging the ethernet cable) and had no luck with that either.

As for the insecure WEP key - the irony there is that my ISP actually set that one up.  I was a bit surprised myself to find out that is how they do it.  I live in such a rural area (literally no houses within wifi distance and if any car or foot traffic was trying to get on our wifi it would be painfully obvious) that I'm not too worried about it and figured I'd just leave it the way they had it...

Was typing all that out while waiting for the wireless to try to connect with the cable unplugged - can now confirm it does challenge for the WEP key (though it waits a while before it does) but never connects.

Here's the response from that command while the cable was unplugged:

```
warren@Warren-Desk:~$ dmesg | grep -e rt6 -e rt2
[    9.158155] rt61pci 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    9.383418] Registered led device: rt61pci-phy0::radio
[    9.383438] Registered led device: rt61pci-phy0::assoc
[ 2781.688876] rt61pci 0000:01:06.0: PCI INT A disabled
[ 2782.812006] rt61pci 0000:01:06.0: BAR 0: set to [mem 0xfdff8000-0xfdffffff] (PCI address [0xfdff8000-0xfdffffff])
[ 2782.812023] rt61pci 0000:01:06.0: restoring config space at offset 0x1 (was 0x4100012, writing 0x4100016)
[ 2782.812687] rt61pci 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
```

---

### Post by chili555 on 2012-05-05
> the irony there is that my ISP actually set that one up. I was a bit surprised myself to find out that is how they do it. Mine, too. But that didn't mean I have to stick with it. I switched to WPA2-AES as soon as the truck was out of the driveway. That, of course, is not the only surprising, and by surprising I mean stupid, thing that many ISPs do.> no houses within wifi distanceThat's better, but you might look around in the router's settings and see if there isn't a better encryption method available. 

You might try a driver parameter:```
sudo modprobe -r rt61pci
sudo modprobe rt61pci nohwcrypt=1
```If it helps, we can make it persistent.

---

### Post by oogyboogawa on 2012-05-05
> **chili555 said:**
> Mine, too. But that didn't mean I have to stick with it. I switched to WPA2-AES as soon as the truck was out of the driveway. That, of course, is not the only surprising, and by surprising I mean stupid, thing that many ISPs do.That's better, but you might look around in the router's settings and see if there isn't a better encryption method available. 

Hehe - I used to do tech support for Verizon DSL business lines, so I'm familiar with some of the stupid things ISPs do.  I've considered changing it(and realize it is very easy), but I'm really not that concerned about it.


> 
You might try a driver parameter:```
sudo modprobe -r rt61pci
sudo modprobe rt61pci nohwcrypt=1
```If it helps, we can make it persistent.

I can't tell that it did anything.  Didn't give any errors, but also didn't give any confirmation that the command made any changes.  Tried disconnecting the ethernet and connecting to wifi - same as before, it eventually prompts for the wep key and then never connects.

I appreciate you helping me out with this :)  I just installed Ubuntu on our main computer a couple of months ago and haven't really learned much about the commands in the terminal.

---

### Post by chili555 on 2012-05-05
> Didn't give any errors, but also didn't give any confirmation that the command made any changes.That's expected. In almost every case, a command that's entered and returns to the command prompt means, roughly, 'command accepted and executed and I have no errors or warnings to report.' That's exactly what you want to see. 

There are few if any manipulable parameters in the rt61pci suite. You might check:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```If it's not minstrel_ht, we can adjust that. You can also try the compat-wireless suite which may be newer and may be better. You can find the appropriate version of linux-backports-modules-**cw** in Synaptic package manager.

We could also try, I am ashamed to say it, ndiswrapper.

---

### Post by oogyboogawa on 2012-05-06
The result returned was minstrel_ht, so I assume that's all good?

Don't have time to test the compat-wireless suite at the moment, but I'll try to get that figured out later and let you know the results.

---

### Post by chili555 on 2012-05-06
> The result returned was minstrel_ht, so I assume that's all good?Yes, indeed. I will look forward to your report.

---

### Post by oogyboogawa on 2012-05-06
> **chili555 said:**
> 
You can also try the compat-wireless suite which may be newer and may be better. You can find the appropriate version of linux-backports-modules-**cw** in Synaptic package manager.

We could also try, I am ashamed to say it, ndiswrapper.

Thanks Chili!  I downloaded the Synaptic package manager and installed the linux-backports-module and it works now.  It connected smoothly and I'm posting this with the ethernet cable unplugged.

Appreciate your help figuring this out!


(Will edit the original post to mark it solved)

---

### Post by chili555 on 2012-05-06
Awesome! Glad it's working.

---

