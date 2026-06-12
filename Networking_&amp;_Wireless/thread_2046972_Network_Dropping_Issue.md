---
title: "Network Dropping Issue"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by serious7 on 2012-08-23
I'm using the latest LTS on my desktop and I'm running into a wierd network dropping issue on my system. 

Basically one of the following situations occurs:
1. I get disconected from all accounts on Pidgin (This occurs randomly like twice per hour)
2. I will lose internet connection completely. I will not be able to ping my router but my network manager says I am still connected to my access point. (This happens every few hours or so). The only solution I found was to restart the computer. However, when I try to restart, the computer gets stuck at the "shutting down screen" with the ubuntu logo and I would have to hard boot my computer at that point.
3. When I am using Transmission Torrent Client, I notice my download speed is going up and down like a roller coaster. Like it will download and it will stop downloading for a second and then download again. 

This has never occured with any previous version of Ubuntu. I am using a wireless card that has worked flawlessly before. What's going on?

---

### Post by serious7 on 2012-08-24
Bump.

---

### Post by Kirk Schnable on 2012-08-25
I suppose we can look and see what card you have, and find out if anyone else is having issues with it...  

Can you supply the output of:

```
sudo lshw -C network
``````
sudo lspci
```And we can look at the power level\signal quality with your AP.  Please supply the output of this command at two times (when it's working well, and when it's not).

```
sudo iwconfig
```Kirk

---

### Post by serious7 on 2012-08-26
When not working

```
harnek@harnek-OEM:~$ sudo iwconfig
[sudo] password for harnek: 
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:91:D1:9E:5F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:62  Invalid misc:1155   Missed beacon:0

eth0      no wireless extensions.
```

When working

```
harnek@harnek-OEM:~$ sudo iwconfig
[sudo] password for harnek: 
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:91:D1:9E:5F   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:170   Missed beacon:0

eth0      no wireless extensions.
```

sudo lshw -C network

```
harnek@harnek-OEM:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 03
       serial: 00:1f:bc:08:1e:98
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:9e00(size=256) memory:f39ff000-f39fffff memory:f39f8000-f39fbfff memory:f3ae0000-f3afffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:11:50:c2:07:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.2.0-29-generic firmware=1.7 ip=192.168.0.101 link=yes multicast=yes wireless=IEEE 802.11bg

```


sudo lspci

```
harnek@harnek-OEM:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
02:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
03:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 570] (rev a1)
03:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
08:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)

```

---

### Post by serious7 on 2012-08-27
Bump.

---

### Post by Kirk Schnable on 2012-08-27
It doesn't look like you're disassociating with your access point (which was what I expected to see happening...)

However it does appear that you're retransmitting a lot of packets.

Seen here:
```
Tx excessive retries:62  Invalid misc:1155
```

You might have a radio going bad somewhere.  Since you're having difficulties transmitting, rather than receiving, I suspect if there is a bad radio or antenna it's on your access point.

Do you have other wireless clients using this network?

Kirk

---

### Post by serious7 on 2012-08-29
> **Kirk Schnable said:**
> It doesn't look like you're disassociating with your access point (which was what I expected to see happening...)

However it does appear that you're retransmitting a lot of packets.

Seen here:
```
Tx excessive retries:62  Invalid misc:1155
```

You might have a radio going bad somewhere.  Since you're having difficulties transmitting, rather than receiving, I suspect if there is a bad radio or antenna it's on your access point.

Do you have other wireless clients using this network?

Kirk

I've had this router for years now. I have at least 5-6 clients connected to it. This issue has only started after I upgraded Ubuntu to the latest LTS.

---

