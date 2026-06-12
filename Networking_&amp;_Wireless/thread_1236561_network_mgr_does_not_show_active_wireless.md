---
title: "network mgr does not show active wireless"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by vbdanl on 2009-08-10
hi. i am wondering what i need to do to get the network manager applet to display my wireless card and strength ?  i have 2 computers loaded with ubuntu 9.04.  on the first pc, the nm applet shows the wireless device, and signal strength.  i took the same usb dlink wireless modem and put it on the 2nd computer.  it does not show any active device, even though i am able to access the internet (so its really just an annoyance more than anything).
on the 2nd pc, i had to enter the essid, key, etc in the interfaces file and enter a default gw route to get the internet working (didn't have to do any of that on the first pc.. it just worked).  the 2 pc's are different (one is sony, one compaq), but they both have 9.04 loaded the same, and i was using the same wireless device on each of them.
maybe the solution is to remove the applet from the taskbar, so it doesn't display what appears to be a down network..
any ideas?

---

### Post by The Toxic Mite on 2009-08-10
Hey!

Can you go to Applications > Accessories > Terminal, and post the output of the following commands please?

```

sudo lshw -c network
iwconfig
ifconfig
lspci

```

Thanks :)

---

### Post by vbdanl on 2009-08-10
> **The Toxic Mite said:**
> Hey!

Can you go to Applications > Accessories > Terminal, and post the output of the following commands please?

```

sudo lshw -c network
iwconfig
ifconfig
lspci

```

Thanks :)

```
:~$ sudo lshw -c network
[sudo] password for dan: 
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:88:e0:6f:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=172.16.1.35 multicast=yes wireless=IEEE 802.11-b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:f3:8c:99:be:8c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"2WIRE529"  Nickname:"2WIRE529"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:72:1D:4B:D1   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=-23 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:47:5d:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:88:e0:6f:b7  
          inet addr:172.16.1.35  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20d:88ff:fee0:6fb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:623278 (623.2 KB)  TX bytes:106574 (106.5 KB)

:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
:~$ lspci
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
03:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
:~$
```
i also gave lsusb output, since that is the type of wireless device i use. i don't have a wireless card, just use the wireless usb dongle.

---

### Post by The Toxic Mite on 2009-08-11
> **vbdanl said:**
> 
[snip]
i also gave lsusb output, since that is the type of wireless device i use. i don't have a wireless card, just use the wireless usb dongle.
 
Right, I thought it would give the type of chip inside the dongle and not the name of the device itself. :-k

---

### Post by vbdanl on 2009-08-11
> **The Toxic Mite said:**
> Right, I thought it would give the type of chip inside the dongle and not the name of the device itself. :-k
i don't know much about chipsets, firmware rev, and all that..
here is some info that might apply if i have the A1 rev:
Device Info

    * Manufacturer: D-Link
    * Model #: DWL-122
    * Revision: A1
    * Device Type: USB
    * Chipset:

      ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b
      nic h/w: id=0x8026 1.0.0

    * Vendor/Device #: 2001:3700
    *

      Vendor Link: [ftp://ftp.dlink.com/Wireless/dwl122/](ftp://ftp.dlink.com/Wireless/dwl122/)


i thought prism 2.5 was the chipset, but i don't really know much about that level of detail.  i will look at the dongle tonight and see if it lists the rev level.. i think it is A1.
do you think dmesg would show anything useful?

---

