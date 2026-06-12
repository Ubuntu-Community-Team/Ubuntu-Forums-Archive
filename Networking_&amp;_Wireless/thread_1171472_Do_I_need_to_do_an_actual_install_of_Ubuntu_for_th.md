---
title: "Do I need to do an actual install of Ubuntu for the network to work?"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by zeedood on 2009-05-27
I wanted to run Ubuntu off of the CD before I do a dual install with Vista. I have tried to get the networking process working numerous times, both by using the dhcp fix to the dhclient.conf file and trying to set a static ip for the nic. 
Should I be able to at least ping my router (192.168.1.xxx)? This is all for a wired setup.
When I try doing a ping right off the bat from a boot up from CD, it says "Connect: network is unreachable". If I do an lspci, both of my nics show up as bridge devices:
00.11.0 Bridge: Nvidia Corporation MCP55 Ethernet (rev a2)
00.12.0 Bridge: Nvidia Corporation MCP55 Ethernet (rev a2)
 
if I do an lshw -C network I get:
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
capabilities : ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 
I've also set the ip,netmask and gateway in the /etc/network/interface file, and restarted the network but still can't get anywhere.
If I go a step further and set up a static ip via netman, my little network icon on the upper right corner shows a connection, and I can ping the static ip I set, but nothing else. 
 
If I need to do an actual install for this to work, then I can do that. But was trying to make sure it all worked before allocating the disk space.
 
Thanks

---

### Post by Iowan on 2009-05-27
It *should* work from the LiveCD (though I haven't tried it lately).  **lshw -C network ** kinda makes it appear to be a driver issue - since neither NIC appears.  What happens if you try ```
dhclient eth0
```

---

### Post by zeedood on 2009-05-27
thanks for answering...I use the nic that corresponds to eth1 (based on the mac address)...other nic is disabled...
 
sudo dhclient eth1 gives the listening/sending on LPF/eth1/mac address, then a bunch of DHCPDISCOVER on eth1 to 255.255.255.0 port 67 interval xx
then No DHCPOFFERS recieved
No working leases in persistent database - sleeping.

---

### Post by superprash2003 on 2009-05-28
post output of ifconfig from the terminal

---

### Post by zeedood on 2009-05-28
Here's a few of the commands I've used to show what I see...the nic with the eth1 mac address is the one I have connected to my router (and is used by vista).
 
[FONT=Arial][EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:66:19:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:245 [/FONT][FONT=Times New Roman][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman] [/FONT][/SIZE][/FONT]
[FONT=Arial]eth1      Link encap:Ethernet  HWaddr 00:1a:92:66:27:d1  
          inet6 addr: fe80::21a:92ff:fe66:27d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1876 (1.8 KB)
          Interrupt:246 Base address:0x6000 [/FONT][FONT=Times New Roman][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman] [/FONT][/SIZE][/FONT]
[FONT=Arial][EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][FONT=Times New Roman][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman] [/FONT][/SIZE][/FONT]
[FONT=Arial][EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:28:7b:e8:f9:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/FONT][FONT=Times New Roman][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman] [/FONT][/SIZE][/FONT]
[FONT=Arial][EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)[/FONT][FONT=Times New Roman][/FONT]

---

### Post by zeedood on 2009-05-28
For those that replied to help me, thanks! 
 
I was goo-gl'n based on my MB and symptom and found this entry: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836)
 
Tried the rmmod and modprobe commands and viola! I'm on!! The entry also states how to make the change more permanent.
 
Thanks again!

---

