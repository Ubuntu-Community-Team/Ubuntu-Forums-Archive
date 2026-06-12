---
title: "wireless not working in 10.04"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by G. Rodrigues on 2010-05-17
In the wake of a spate of posts complaining that wireless is not working in 10.04 here is mine. I'm on a (relatively old) AMD Duron 1.5Ghz, 1.5G memory with a VIA KM-266 motherboard. Wireless worked fine in 9.10. With a fresh install of the new 10.04, the usb wireless adapter is not detected, the tab to add a new wireless connection is grayed out, starting the KNetworkManager (did I got the name right?) does nothing (that is, no application starts), etc.

note: if you are wondering how I am accessing the internet, I just fired up the 9.10 live CD, which as you can imagine is not the most practical thing in the world.

Here is the info. The commands lsusb and lspci spit the following:

```
grodrigues@grodrigues-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0baf:0118 U.S. Robotics U5 802.11g Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

grodrigues@grodrigues-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]                                                                          
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)                                                    
00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)                                
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)                                                      
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)                                                      
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

```Note that the lsusb command returns the *correct* usb wireless adaptor, so it seems not everything is wrong.

Next, the interfaces:

```
grodrigues@grodrigues-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:3c:73:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4800 (4.8 KB)  TX bytes:4800 (4.8 KB)

grodrigues@grodrigues-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```As you can see, there is no wlan0 interface. So something has gone wrong. For the sake of completion here is what network config spits:

```
grodrigues@grodrigues-desktop:~$ sudo lshw -C network
[sudo] password for grodrigues: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:30:1b:3c:73:ee
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:d000(size=256) memory:e4100000-e41000ff

```Finally, network scanning returns (as one would image):

```

grodrigues@grodrigues-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```I have left out the ouput of lsmod and dmesg as they return a *lot* of text. But here is an interesting piece of info. If I run dmesg on Kubuntu 10.04 we find the following snippet

```

[    9.917692] usb 1-2: firmware: requesting isl3887usb
[    9.935674] usb 1-2: (p54usb) cannot load firmware isl3887usb (-2)!
[    9.935732] usb 1-2: firmware: requesting isl3887usb_bare
[    9.959242] p54usb: probe of 1-2:1.0 failed with error -2
[    9.959285] usbcore: registered new interface driver p54usb

```While in the Ubuntu 9.10 live CD, we have:

```

[  120.172905] usb 1-2: firmware: requesting isl3887usb
[  121.463596] cfg80211: World regulatory domain updated:
[  121.463607]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  121.463613]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  121.463617]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  121.463622]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  121.463626]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  121.463630]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  121.976344] phy0: p54 detected a LM87 firmware
[  121.976351] p54: rx_mtu reduced from 3240 to 2384
[  121.976355] phy0: FW rev 2.13.24.0 - Softmac protocol 5.9
[  121.976360] phy0: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[  123.060966] phy0: hwaddr 00:c0:49:5c:74:66, MAC:isl3887 RF:Frisbee
[  124.774243] phy0: Selected rate control algorithm 'minstrel'
[  124.775405] Registered led device: p54-phy0::assoc
[  124.775435] Registered led device: p54-phy0::tx
[  124.775465] Registered led device: p54-phy0::rx
[  124.775490] Registered led device: p54-phy0::radio
[  124.775513] usb 1-2: is registered as 'phy0'
[  124.775587] usbcore: registered new interface driver p54usb

```So in going from 9.10 to 10.04, the cpability of loading the firmware isl3887usb was lost. Anymore info needed, just ask. Anyway, has anyone has any ideas on how to proceed?

Regards, thanks in advance,
G. Rodrigues

---

### Post by G. Rodrigues on 2010-05-18
Replying to myself, but it is ok as the problem is solved. By following the hint provided by my dmesg snippet and googling for "firmware isl3887usb", I was directed to the following page:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383")

Then I just pointed to the lucid ubuntu package, saved the deb package in my usb drive, installed it (just click in it in the file manager) and reboot. And voila, internet is on again.

Ever since, I switched to linux from windows a month ago it has been a constant stream of problems. On the upside, I am starting to get a knack for fixing problems...

Note: tagging the question as solved.

---

