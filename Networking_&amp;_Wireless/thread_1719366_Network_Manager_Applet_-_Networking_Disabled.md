---
title: "Network Manager Applet - Networking Disabled"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by jaguare22 on 2011-04-01
Okay so I have been working on this for a couple of days.  I have wired network only.  My Network Manager Applet says Network Disabled and enable is grayed out.  I know that interfaces is setup correctly.  I have tried a number of things, most recently uninstalling network-manager-gnome and reinstalling.  Any help is appreciated at this point.
 dmesg - 

  [  123.185252] eth0: link down
[  123.677741] lib80211_crypt: registered algorithm 'CCMP'
[  123.778779] padlock: VIA PadLock not detected.
[  123.793070] lib80211_crypt: registered algorithm 'TKIP'
[  126.434652] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  142.413119] eth0: link down
[  148.507184] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  176.753261] lo: Disabled Privacy Extensions
[  258.874737] eth0: link down
[  265.148041] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[  265.274124] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  266.815818] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  277.280074] eth1: no IPv6 routers present
[  293.577614] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  425.801844] eth0: link down
[  433.101183] usb 1-2: USB disconnect, address 3
[  442.764054] ipw2200: Failed to send RSN_CAPABILITIES: Command timed out.
[  443.261758] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  443.772093] ipw2200: Failed to send SSID: Command timed out.
[  747.640108] usb 2-1: USB disconnect, address 2

lshw -c network

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:d3:5e:89
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.6 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:3000(size=256) memory:b0106000-b01060ff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth1
       version: 05
       serial: 00:15:00:1a:7b:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:b0107000-b0107fff

ifconfig - 

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:d3:5e:89  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fed3:5e89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4175306 (4.1 MB)  TX bytes:825593 (825.5 KB)
          Interrupt:16 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:1a:7b:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:671 errors:1 dropped:1 overruns:0 frame:0
          TX packets:1079 errors:0 dropped:19 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:335838 (335.8 KB)  TX bytes:197707 (197.7 KB)
          Interrupt:18 Base address:0xc000 Memory:b0107000-b0107fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25967 (25.9 KB)  TX bytes:25967 (25.9 KB)

---

### Post by jaguare22 on 2011-04-01
Just thought I would include my lsusb too.  Anybody?

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 047d:101f Kensington PocketMouse Pro
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3303 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by dineshs on 2011-04-02
Is your wireless switch ON?
See if post #4 [here]("http://ubuntuforums.org/showthread.php?t=1452464&highlight=hard+blocked") helps

---

### Post by jaguare22 on 2011-04-02
Yeah, it sure is.  I removed Connman and all connections failed, including wired.  So I think that Connman is working behind the scenes.  Also, after uninstalling Connman the Network Manager applet icon disappeared.   When I  reinstalled Connman (yes, I  confirmed Net Man still installed) Net Man icon came back (after reboot).  I had connectivity again but still have "Networking disabled" when hovering over icon and icon is gray with red exclamation.  Left clicking on icon shows "No Network Devices Available" grayed out.  Right clicking shows "Enable Networking" grayed out.

---

### Post by matt_symes on 2011-04-02
Hi

```
*-network:1 DISABLED
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 6
bus info: pci@0000:06:06.0
logical name: eth1
version: 05
serial: 00:15:00:1a:7b:a8
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
resources: irq:18 memory:b0107000-b0107fff
```

Are you trying to get wireless enabled or fix network manager. Your wireless interface is disabled.

Are you sure this is the correct driver ? driver=ipw2200

Kind regards

---

### Post by jaguare22 on 2011-04-02
Your right, my mistake.  I had been making many changes and must have run the ls while it was off (my system has a bright light on the lcd for wireless state).  

I am trying to get Network Manager working.  Apologize for the confusion.

---

### Post by matt_symes on 2011-04-02
Hi

Can you post the output of

```
cat /var/lib/NetworkManager/NetworkManager.state
```

Kind regards

---

### Post by jaguare22 on 2011-04-02
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

I had seen this referenced in the forum.  When I looked in /var/lib neither the directory nor the file were there, so I added both the directory and the file myself.  Yes, I am new to this.

---

### Post by matt_symes on 2011-04-02
Hi

> **jaguare22 said:**
> [main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

I had seen this referenced in the forum.  When I looked in /var/lib neither the directory nor the file were there, so I added both the directory and the file myself.  Yes, I am new to this.

...and networking is still disabled ? That file looks fine BTW.

Have you tried stopping and starting network manager ?

```
sudo service network-manager restart
```

Kind regards

---

### Post by jaguare22 on 2011-04-02
$ sudo service network-manager restart
[sudo] password for sysuser: 
restart: Unknown instance: 

Seemed strange so I tried this
$ sudo service network-manager start
network-manager start/running, process 4678

Stranger still right?  BTW, I have the icon on the panel, I can edit connections and I have removed and re-added them many times.  Usually after trying something I read.  

Enable Notifications is not grayed out and it is checked.  I can also see the about - NetworkManager Applet 0.8.1

---

### Post by matt_symes on 2011-04-02
Hi

Please post the output of

```
cat /etc/NetworkManager/nm-system-settings.conf
```

Kind regards

---

### Post by matt_symes on 2011-04-02
Hi

> **jaguare22 said:**
> $ sudo service network-manager restart
[sudo] password for sysuser: 
restart: Unknown instance: 

That sound to me like NM was not running.

> Seemed strange so I tried this
$ sudo service network-manager start
network-manager start/running, process 4678

Stranger still right?  BTW, I have the icon on the panel, I can edit connections and I have removed and re-added them many times.  Usually after trying something I read.  

Enable Notifications is not grayed out and it is checked.  I can also see the about - NetworkManager Applet 0.8.1

But enable networking and other options are disabled ?

Kind regards

---

### Post by jaguare22 on 2011-04-02
> **matt_symes said:**
> Hi

Please post the output of

```
cat /etc/NetworkManager/nm-system-settings.conf
```

Kind regards

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Thank you for your efforts on this....

---

### Post by matt_symes on 2011-04-02
Hi

> **jaguare22 said:**
> [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Thank you for your efforts on this....

Try changing managed to true and reboot.

```
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```

Kind regards

---

### Post by jaguare22 on 2011-04-02
changed as suggested, rebooted, no joy.  

Rechecked file to be sure, it still says managed=true 

Yes, enable networking is not selectable from right click menu (grayed out)

Also, I know that ConnMan is still installed.  Not sure if that matters.  I have tried uninstalling but lost all connectivity.  Maybe I needed to change that line to true instead of reinstalling ConnMan?

---

### Post by matt_symes on 2011-04-02
Hi

You have both conman and network manager installed ? 

I wonder if that's causing the problem. Everything else looks alright to me.

I will do some research on this one.

Kind regards

---

### Post by matt_symes on 2011-04-02
Hi  

Can you post the output of

```
cat /etc/network/interfaces
```

Kind regards

---

### Post by jaguare22 on 2011-04-02
Well unistalling ConnMan fixed it.  NM is working now.  Thanks a whole lot matt!

In case anyone else reads this - It was the combination of uninstalling Connman with the nm-manager line - managed=true.  Not sure how Connman got in there, I had tried uninstalling it before but it did no good with managed=false in NM.

---

