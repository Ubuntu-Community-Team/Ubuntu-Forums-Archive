---
title: "Flaky wireless and no wired connection Satellite A500-17X"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by Phelimb on 2011-07-19
Hi all,

Since installing 11.04 as a dual boot with windows 7 I've been having problem with constant disconnects from the wireless network and no wired ethernet connection detected. 

Below the output of few popular commands which I'm sure I would be asked to execute.
```


sudo ifconfig -a
[sudo] password for phelimb: 
eth0      Link encap:Ethernet  HWaddr 00:26:22:ec:6b:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:152064 (152.0 KB)  TX bytes:152064 (152.0 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:7e:c8:69  
          inet addr:204.102.227.219  Bcast:204.102.227.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe7e:c869/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5790732 (5.7 MB)  TX bytes:1982536 (1.9 MB)



```

```

lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 230M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
14:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
20:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
20:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
20:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
20:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)

```

```

ifup eth0
Ignoring unknown interface eth0=eth0.


```

```

cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

```

dmesg | grep -e eth0 -e bcm
[    1.749531] r8169 0000:0e:00.0: eth0: RTL8168d/8111d at 0xf8022000, 00:26:22:ec:6b:d5, XID 081000c0 IRQ 46
[   17.331686] r8169 0000:0e:00.0: eth0: link down
[   17.331890] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.399478] r8169 0000:0e:00.0: eth0: link down
[   49.399936] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.703481] r8169 0000:0e:00.0: eth0: link down
[   51.703734] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.019357] r8169 0000:0e:00.0: eth0: link down
[   81.019540] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.182780] r8169 0000:0e:00.0: eth0: link down
[   81.193176] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  313.516850] r8169 0000:0e:00.0: eth0: link down
[  313.517275] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  319.608256] r8169 0000:0e:00.0: eth0: link down
[  319.608595] ADDRCONF(NETDEV_UP): eth0: link is not ready


```

```

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT216 [GeForce GT 230M] [10de:0a28] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be2] (rev a1)
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
14:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
20:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 20)
20:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (rev 20)
20:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383] (rev 20)
20:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384] (rev 20)


```


Laptop specs can be found here: [http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&com.broadvision.session.new=Yes&PRODUCT_ID=1076471](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&com.broadvision.session.new=Yes&PRODUCT_ID=1076471)

I've tried installing the driver from here to no avail:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)


Thanks in advance.

---

