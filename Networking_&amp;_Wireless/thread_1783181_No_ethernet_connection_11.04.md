---
title: "No ethernet connection 11.04"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by anthonylane13 on 2011-06-15
Hi all

I've searched the forum and found what I hoped to be a fix, but it hasn't worked.

I picked up a new (old) machine with windows vista (which I sadly need to test web pages) and decided to dual boot with 11.04.

Installation went well, but ubuntu won't connect via ethernet (vista connects no problem)

This is what hp says about my hardware
> Networking
LAN: 10-Base-T

    *
      Interface: Integrated into motherboard
    *
      Technology: Realtek RTL8201N
    *
      Data transfer speeds: up to 10/100 Mb/s
    *
      Transmission standards: 10-Base-T Ethernet

Please can someone shed some light on this. Maybe there's a driver I can download or a config change I can make?

If you need to see some terminal output just let me know what command to use.

Thanks folks :)

---

### Post by anthonylane13 on 2011-06-16
***Update***

I feel slightly stupid, but I still do have a problem.

I'm writing this reply from my new ubuntu installation, but taking my ethernet as a shared connection from my mac.

So, the problem is either my ethernet cable (I doubt it because it works on the same machine in windows) or it's a compatibility issue between ubuntu and my router (BT home hub.)

If anyone has information about router compatibility, please share. I can't believe that it would be the case as ubuntu 10.10 works fine from that router on another machine....

I'm more than a little confused...

Thanks :)

---

### Post by anthonylane13 on 2011-06-25
**another update**

I bought a PCI network card because I thought maybe the built in network module was incompatible... but again, it works in windows but not in Linux.

It seems that ubuntu just refuses to connect on this machine unless the connection is shared from my mac first.

Any help on this matter greatly appreciated. :)

---

### Post by anthonylane13 on 2011-06-25
Here's my lspci output if it helps

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by westie457 on 2011-06-25
Hi, have you tried to edit your network connection to connect using 'Automatic DHCP' under the 'IPv4 Settings' tab?

---

### Post by anthonylane13 on 2011-06-25
Hi Westie

I've checked the settings and the ethernet was already set to connect via automatic DHCP.

I've also tried ```
sudo dhclient
```, but that doesn't help either.

Any other advice greatly appreciated.

---

### Post by dozycat on 2011-06-25
What do you get if give the command ifconfig?

---

### Post by westie457 on 2011-06-25
Just a thought. In the Networks Connection Editor did you tick the box that says "Connect Automatically"?

I have missed that in the past. Went and banged my head against a wall after a silly mistake like that.

Other than that no ideas of my own.

This old thread might give you some ideas and probably a solution. It can be found _[here]("http://ubuntuforums.org/showthread.php?t=1033293")_

---

### Post by anthonylane13 on 2011-06-26
Hi again Westie - thanks for your input. Yes, connect automatically is set by default. Had a look at the other thread, but I don't think that's the same problem.

@dozycat, here's my ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1a:92:87:3f:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:e0:e8:12:4a:5c  
          inet6 addr: fe80::2e0:e8ff:fe12:4a5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4359 (4.3 KB)  TX bytes:7948 (7.9 KB)
          Interrupt:18 Base address:0xbc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

$ ping 192.168.1.254
connect: Network is unreachable

Thanks :)

---

### Post by westie457 on 2011-06-26
Hi Myabe I am missing something here and it bugging me because I do not know what is missing However I am still looking. 

In the meantime here is a couple of old threads that may or may not provide the soluton.


The first one is _[here]("http://ubuntuforums.org/showthread.php?t=367901")_


The second one is _[here]("http://www.linuxforums.org/forum/newbie/33681-linux-internet-networking.html")_

---

### Post by anthonylane13 on 2011-06-26
Westie, thanks again for your suggestion. Sadly no luck with the plug & play OS settings either. I changed from yes to no, and tried the LAN Boot ROM setting to yes, but neither has worked.

---

### Post by westie457 on 2011-06-26
Did you see the edit at the bottom of my last message? The bit that says to disable IPv6 settings.

---

### Post by anthonylane13 on 2011-06-26
No, I didn't see that - thanks again. I'll try that and post back. :)

---

### Post by dozycat on 2011-06-28
did you try to create one network and selected it when you connect the cable?
I do that when dhcp fails me, I just create one wired netwok with the in the ip pool I need.

---

