---
title: "Wired connection only on Ubuntu 10.04 LTS"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by ghost25 on 2013-05-18
Hey all, got a rather in-depth challenge for y'all.

My wife has a Compaq Presario CQ62 that I just installed a dual-boot of Win7 and Ubuntu 10.04 LTS. I've been Googling, Ubuntuforums-ing, the whole nine yards, and it seems like everything is turning into a wild goose chase. I know she has either a 8101 or 8102 Realtek WiFi chip (not sure which one, somehow I'm interpreting system output as reading both of them...) and I've searched for the appropriate drivers, however I haven't been able to find anything thus far.

I've tried doing the update to version 12 but I keep getting something about broken packages. I believe this has something to do with why her WiFi won't work.

When I have it unplugged, it will locate and display every WiFi network in our area, except our own. I have to plug it in manually to do anything. I've tried setting up the wireless manually, adding the SSID, changing IPv4 to 8.8.8.8 8.8.4.4, but it's still not recognized. Funny enough, my own laptop is able to connect just fine, running a similar setup except that it's an Acer. The Compaq is the only computer that will only connect via Ethernet.

When I put in iwconfig, I get the following:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And when I put in ifconfig, this shows up:
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:a8:11:3d  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12427763 (12.4 MB)  TX bytes:992286 (992.2 KB)
          Interrupt:26 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:7f:d7:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f80e8000-f80e8100 

**lspci** displays:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

**sudo lshw -C network** shows:
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:7f:d7:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=63 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:93500000-93503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:a8:11:3d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:2000(size=256) memory:91410000-91410fff(prefetchable) memory:91400000-9140ffff(prefetchable) memory:91420000-9142ffff(prefetchable)

And **ifconfig -a** shows:
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:a8:11:3d  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13919590 (13.9 MB)  TX bytes:1153028 (1.1 MB)
          Interrupt:26 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:7f:d7:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f80e8000-f80e8100 





This is a brand new install of Ubuntu, I haven't had the time to really go in and monkey with it at all. Care to help at all?

---

### Post by ghost25 on 2013-05-18
Just as a quick "side note," I also put in the commands listed in <a href="http://ubuntuforums.org/showthread.php?t=1548660&p=9695830#post9695830">this post</a> to attempt to clean things up... I'm in the process of downloading updated files so I'll keep yall informed as to if it works or not.

---

### Post by praseodym on 2013-05-18
Hi,

please check the outputs of
```

lspci -nnk | grep -iA2 net
lsmod
```

---

