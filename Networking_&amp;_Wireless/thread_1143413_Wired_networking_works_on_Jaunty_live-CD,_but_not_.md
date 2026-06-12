---
title: "Wired networking works on Jaunty live-CD, but not after install"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by fireman biff on 2009-04-29
When using the live CD for 32-bit Jaunty the wired networking works fine and I can get online. Once I installed from the same CD I cannot get online. The network manager keeps trying to connect but is unable to do so - it keeps popping up a message saying its disconnected.

Also, everytime I restart the name of the interface changes - the number increments, so it goes from eth1 to eth2 to eth3 etc.

Info:

lspci
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
**00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)**
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

lshw
```
...
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth4
          version: a2
          serial: 00:00:6c:9e:d5:86
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
...
...
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:69:43:4b:dc:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
...
```

ethtool -i eth5
```
driver: forcedeth
version: 0.61
firmware-version: 
bus-info: 0000:00:07.0
```

ethtool -t eth5
```
The test result is PASS
The test extra info:
link      (online/offline)	 0
register  (offline)       	 0
interrupt (offline)       	 0
loopback  (offline)       	 0
```

I also tried the following based on bug filed at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836) but it did not make a difference.
```
# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                       [ OK ] 
```

Any ideas?

---

### Post by FallFromINFINITY on 2009-04-29
I had the same problem, except with a wireless card instead of ethernet.
```
sudo dhclient
```
^^ solved it for me.

After I got that done, everything went online.

---

### Post by fireman biff on 2009-04-29
> **FallFromINFINITY said:**
> I had the same problem, except with a wireless card instead of ethernet.
```
sudo dhclient
```
^^ solved it for me.

After I got that done, everything went online.

Hi, sorry I forgot to mention that I tried that already and didn't get any dhcp offers.

---

### Post by wgscott on 2009-04-30
Do you normally have a static IP address?  If so, I found using **ifconfig** and **route** worked.

This is pretty buggy behavior for a long-term release.

---

### Post by fireman biff on 2009-04-30
> **wgscott said:**
> Do you normally have a static IP address?  If so, I found using **ifconfig** and **route** worked.

This is pretty buggy behavior for a long-term release.

There is no "normal" for this particular system yet, its never had Linux on it before. With Windows XP and the live CD it used dynamic addresses though. I guess I'll try using a static, although I'd prefer not to.

By the way, Jaunty is not a long-term support release.

---

### Post by Iowan on 2009-04-30
Not sure about Jaunty, but check */etc/udev/rules.d/70-persistent-net.rules* You may be able to "edit away" the extraneous ethX's.

Next LTS will *probably* be 10.04. (LL?)

---

