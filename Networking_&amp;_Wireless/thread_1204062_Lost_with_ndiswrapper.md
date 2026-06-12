---
title: "Lost with ndiswrapper"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by ramibotros on 2009-07-04
[LIST][*]Kubuntu 9.04 Jaunty[*]Dell Inspiron E1505/6400 (Broadcom 1390 WLAN) [*] Followed [this guide]("http://ubuntuforums.org/showthread.php?t=297092").
[*] Things to admit:
[LIST][*]I had installed b43-fwcutter (but by now I have removed the package and blacklisted 'bcm43xx' and 'b43' and 'b43-pci-bridge'[*]I am using the ndiswrapper-1.9 package, did **not** install from the source (because 'make' gave me errors)

[/LIST]


[/LIST]

```
sudo lshw -C Network
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=**b43-pci-bridge** latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8b:49:03
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.3 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:26:2c:d2:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: a6:3d:42:60:b1:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Why is it using b43-pci-bridge when I want it to use ndiswrapper?
Or is that a non-issue?
ifup wlan0 gives me:
```
sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```

Tell me if you need any additional info.
Thanks!

---

### Post by spd106 on 2009-07-04
That guide is ancient!

Please don't bother with Ndiswrapper any more, b43 is much better nowadays.


If you have a wired connection then it should have been a simple matter of starting the Hardware Drivers application (not sure what the alternative is on Kubuntu), then activating the wireless card.

If that fails then follow the instructions on this web page.
[http://linuxwireless.org/en/users/Drivers/b43#firmware_installation](http://linuxwireless.org/en/users/Drivers/b43#firmware_installation)

All you need to do is fetch the firmware and extract it into the /lib/firmware folder. There are lots of scripts to do this for you.

Don't forget to un-blacklist the drivers.

---

### Post by ramibotros on 2009-07-04
Thanks for the quick reply!
Through jockey-gtk I was able to use what seems to have my card working well now.
```
_jockey-gtk -l_
No protocol specified
/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
firmware:b43 - Broadcom B43 wireless driver (Free, Disabled, Not in use)
**kmod:wl - Broadcom STA wireless driver (Proprietary, Enabled, In use)**

```

'iwlist scan' is working well. But now 'iwconfig' gives me this:
```
_iwconfig_
lo        no wireless extensions.

pan0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Before I start playing around with iwconfig itself, do you recommend any GUI front-ends that will make my life easier? Btw,I won't ask for me than a WEP encryption.

---

### Post by spd106 on 2009-07-07
Sorry for the delay.

I recommend using the default Network Manager tool if you can. I'm not a KDE user so I can't say whether it's gui tool is any good, but it's fine in Gnome.

Otherwise, if you're only going to use WEP, then you could probably get away with just editing the /etc/network/interfaces file. See *man interfaces* for a guide and I've posted an example stanza below.


```
auto wlan0
iface wlan0 inet dhcp
wireless-essid Tiscali123456
wireless-key 1234567890

```

---

### Post by AlexDudko on 2009-07-08
You don't need any drivers for your wireless (802.11bg). It should work just out of box in Jaunty. Just configure your wireless connection properly. Unfortunately, I can't help with configuration - a don't use kubuntu (a xubuntu user with working wireless and the same wireless device).

---

### Post by ramibotros on 2009-07-21
Through editing the /etc/network/interfaces file, I got the connection to work fine. 

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
#address 127.0.0.1
#netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp
wireless-essid Ramibotros
wireless-key ########################

```

Now each time I log in to my kubuntu, I need to run:
```
sudo ifdown eth1
sudo ifup eth1
```

Besides, if I need to connect to any other wireless network, I need to edit /etc/network/interfaces again.
Is there any front-end that would solve both these problems for me? I've tried Wicd Manager, but it doesn't seem to be able to connect to my wireless network. Is there a way I could debug around that and make it work?

---

