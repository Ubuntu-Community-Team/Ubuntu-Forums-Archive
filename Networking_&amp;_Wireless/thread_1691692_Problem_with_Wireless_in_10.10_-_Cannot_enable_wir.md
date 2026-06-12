---
title: "Problem with Wireless in 10.10 - Cannot enable wireless"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by funnysnoot on 2011-02-20
I've a Lenovo V560 that seems to be running 10.10 just fine with the exception of my wireless card.

When I first installed 10.10, by default wireless was not enabled, and at every start up I had to manually enable wireless so it could connect to my home network.

I tried updating my interfaces config to no avail. Here's what I currently have:

```

auto lo
iface lo inet loopback

```

Well, I was fine having to enable the wireless manually (albeit kind of a strange quirk), but not it seems I cannot enable wireless at all. From the NetworkManager applet in the menu bar, the "Enable Wireless" is greyed out. What has happened and how can I troubleshoot this?

I tried looking to see if the system was missing a proprietary driver for my card, but nothing turns up when I run the Additional Drivers administration tool.

So, I would like to get my wireless re-enabled, and then, if at all possible, have it enable itself on startup.

Thanks.

---

### Post by thefasterblueone on 2011-02-20
Please post the results of this command.

```
sudo lshw -C network
```

---

### Post by funnysnoot on 2011-02-20
Thanks for the reply. Here's what I have (I've x'd out serial numbers):

```

 *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: xx:xx:xx:xx:xx:xx
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:47 memory:f2400000-f243ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 5f
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-25-generic firmware=9.201.4.1 build 24255 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:f2500000-f2501fff
  *-network
       description: Ethernet interface
       physical id: 4
       bus info: usb@2:1.4
       logical name: wmx0
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no

```

---

### Post by thefasterblueone on 2011-02-20
Lets see what this says.

```
rfkill list
```

---

### Post by funnysnoot on 2011-02-20
It says:

```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: i2400m: WiMAX
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

---

### Post by thefasterblueone on 2011-02-20
Run this.

```
sudo iwconfig

```

---

### Post by funnysnoot on 2011-02-20
This is the output:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmx0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

---

### Post by thefasterblueone on 2011-02-20
Check your "switch" on your laptop to enable wireless.
It might be a button or a combination of keys.

example:  * Hardware switch at the side or front of laptop.
          * Button around the keyboard area.
          * Various key combinations utilizing Fn, Ctrl, Alt in conjunction with specialized function keys ranging from F1 to F12.

---

### Post by funnysnoot on 2011-02-20
Brilliant. That solved the enabled issue. There's a wee switch on front of the laptop that I never noticed before and must have inadvertently hit. I can now use my wireless card. Thank you.

But, it does not default at startup. Is that where editing my interfaces config comes in?

Thanks again.

---

### Post by funnysnoot on 2011-02-20
Ah, nevermind. I found this message:

[http://ubuntuforums.org/showpost.php?p=10429506&postcount=6](http://ubuntuforums.org/showpost.php?p=10429506&postcount=6)

Editing the rc.local file solved it.

Many thanks, thefasterblueone, for helping with the other issue. I appreciate it.

---

