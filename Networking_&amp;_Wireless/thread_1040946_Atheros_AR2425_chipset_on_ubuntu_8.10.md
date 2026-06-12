---
title: "Atheros AR2425 chipset on ubuntu 8.10"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by gabriel.pelmus on 2009-01-16
Hello,
I am having some problems with my wireless card for1 month now.
At home I have set up a wireless network encrypted with a wpa2 key.I have installed kubuntu 8.10 on my notebook(Asus x51h) and my sister has windows xp on hers.I followed any tutorial on any forum I could find on how to get my card working.one of the tutorials is this one: [http://ubuntuforums.org/showthread.php?t=886082.The](http://ubuntuforums.org/showthread.php?t=886082.The) problem I'm having is the following one: I installed the madwifi driver and wicd.Wicd is the only one that can see the wireless network,but this is only if I have my network cable plugged in,otherwise it doesn't detect it.When I'm trying to connect to the network,it shows Putting up interface message in the status bar, and than Not connected.After this, if I hit the connect button,nothing happens.If I hit refresh, the network will disappear from the list, and shows the message No wireless network found.If I want to see the network again,I have to restart my computer.The thing with hitting refresh happens also if I don't try to connect to the network.Here are some configuration details in the hope that someone will know what the problem is.I would be the happiest man if I get this thing working.I hate Windows!
 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:50:e1:3f  
          inet addr:192.168.0.124  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe50:e13f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360646 (360.6 KB)  TX bytes:97540 (97.5 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3348 (3.3 KB)  TX bytes:3348 (3.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:3f:38:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-3F-38-8E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
05:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thanks a lot! I hope someone will save me[-o<

I changed the madwifi driver from wicd to wext.now I have the following issues: when my wireless network is encrypted and i hit connect, it remains stuck to validating authenticity.when the network is unsecured it remains stuck to obtaining ip.if I set th dns and ip to static, it shows me connected to WLAN(my network) with 0 dbM and keeps showing putting down interface every 30 sec. I had a look in the interfaces file from /etc/networks and it looks a bit strange to me.I could only find this:

auto lo
iface lo inet loopback

could this be a part of the problem?please help me!

---

### Post by gabriel.pelmus on 2009-02-14
I think i figured out what might be the problem.this morning when i woke up ant started my laptop,my wireless started working.i don't know why,it just worked.until i pressed the button that enables/disables the wireless card.now I can't make it work again
sudo lshw -c network
[sudo] password for gabriel: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:3f:38:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:60:50:e1:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.124 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:82:b0:c8:88:47
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

i can start my wireless network card only when the laptop is waking from hibernate.during this stage,if i press the button that enables the card,the wireless card will work ok.this doesn't happen when i start the laptop after shutdown.does anyone have any idea how can i make this work?

---

