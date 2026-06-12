---
title: "Cannot connect to ethernet modem"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by Lacho on 2010-03-16
I just nuked windows on a PC, but with my luck the ethernet card in the motherboard turned out to be an Attansic L2, which according to many threads is incompatible with Ubuntu.

So I bought another card, an Encore ENL832-TX-ENwhich supposedly can connect, installed it in one of the empty slots, and nothing.

Now I run the lspci command and the only ethernet controller mentioned is the attansic card. The new one is not recognized.

I have tried cycling the modem, checking/unchecking the Enable Networking option in Network Manager, running sudo ifconfig eth0 thru 5, and getting "Error while getting interface flags: no such device" message, but nothing happens.

It is as if the new card is invisible; can anybody help me, please...

---

### Post by Iowan on 2010-03-16
Post **sudo lshw -C network** - that should provide a starting point for interfaces.

---

### Post by Lacho on 2010-03-17
Sorry for the delay, 

sudo /etc/lshw -C network came out as command not found.

I just connected a Belkin USB WiFi antenna, which is a loaner, so I have to return it.

ifconfig came out as:

eth0      Link encap:Ethernet  HWaddr 00:25:11:cd:87:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:febc0000-fec00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:1c:5e:17  
          inet addr:192.168.1.74  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fe1c:5e17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2481177 (2.4 MB)  TX bytes:333087 (333.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-DF-1C-5E-17-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lspci comes out as:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

---

### Post by Iowan on 2010-03-17
Sorry - dunno where the /etc came form - guess I was brain-locked on */etc/network/interfaces* or */etc/resolv.conf*. Try it as simply:
```
sudo lshw -C network
```

---

