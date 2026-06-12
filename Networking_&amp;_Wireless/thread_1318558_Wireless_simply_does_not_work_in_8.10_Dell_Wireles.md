---
title: "Wireless simply does not work in 8.10 Dell Wireless 1395 WLAN card"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by greatn on 2009-11-07
****** I've fixed my initial problem, but please go to my third post*****

I have used 8.03 in the past with no problems and recently did a clean install of 8.10 because my upgraded 8.10(which also had no wireless problems) was having other issues.

Wireless simply disappears in this version though. I checked troubleshooting, and the first thing it tells me to do "sudo lshw -C network" does not bring any of the expected results of "CLAIMED, UNCLAIMED, ENABLED or DISABLED", just a big wall of text with those words nowhere to be found.

Clicking on the network icon in the upper right "Enable Wireless" is not even an option.

I can't really post any outputs here, because I am using windows for the internet. I don't have a wired internet connection, only wireless, so it is impossible for me to copy and paste anything going wrong.

Perhaps I need the Windows Wireless Driver from NDISWrapper section of troubleshooting, I have no idea where I would obtain it. I'm not awfully patient with all this troubleshooting because it is supposed to "just work".

---

### Post by greatn on 2009-11-07
Looked around some more and found at least two other threads of people with the same problems who in the end were not able to solve them, along with archaic directions from people which I didn't understand at all. Maybe I should just wait and try 8.11

---

### Post by greatn on 2009-11-08
Alright well after some experimentation I was finally able to get my wireless to show up. I was able to get NDIS wrapper, then borrowed a cable to get myself a wired connection and update my drivers.

Wireless actually shows up now. However, it still isn't really working. I can see several networks, and when I try to connect to mine, nothing happens. It sits and tries to connect for a minute and then says I'm disconnected. I know I'm using the proper encryption (WPA Personal) and the proper key. I enter in my password, it tries for a minute and then nothing happens. Any ideas?

---

### Post by greatn on 2009-11-08
Ok, using my wired connection I can now post the various outputs of things, so maybe some of this might be a clue.

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:23:ae:0b:9f:1e  
          inet addr:68.62.223.11  Bcast:68.62.223.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe0b:9f1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3243012 (3.2 MB)  TX bytes:331821 (331.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:1b:3c:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2674 (2.6 KB)  TX bytes:4090 (4.0 KB)
          Interrupt:17 Memory:fe7fc000-fe800000 
```
sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:0b:9f:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=68.62.223.11 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:1b:3c:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,09/20/2007, 4.170. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:fe7fc000-fe7fffff

```

My current problem is while I can see all networks, I can connect to none of them. If I go to hardware drivers it says my broadcom driver is activated but not currently in use, but my wireless light is on and it is sniffing.

If I go to Windows Wireless Drivers, I get a popup that says "unable to see if hardware is present", but right there in the window it shows my bcmwl5, and says "Hardware Present: yes"

Anyone have any idea?

---

