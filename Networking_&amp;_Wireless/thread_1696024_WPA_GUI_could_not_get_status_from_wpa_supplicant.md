---
title: "WPA GUI could not get status from wpa_supplicant"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by RobotGymnast on 2011-02-26
I'm running Ubuntu minimal install on a laptop with a Broadcom 4312 wireless card. To get WPA running, I wrapped my drivers with ndiswrapper and tried using wpa_supplicant.

I'm trying to use wpagui to set up the network, but it's not working, and keeps telling me "Could not get status from wpa_supplicant".

At this point, I'm willing to try either GUI-less or GUI-full, but I just need to get it working. Help anybody?

I've removed NetworkManager and wicd, my network interface shows up fine:

```
me@lappy486:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR="Red"]wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]

```

And my driver's fine:
```
me@lappy486:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:3f:34:46
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="red"]driver=ndiswrapper+bcmwl5[/COLOR] driverversion=1.56+Broadcom,09/20/2007, 4.170. latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:19 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:b1:62:95
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.8 latency=0 multicast=yes
       resources: irq:44 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:f8620000-f862ffff

```

My /etc/wpa_supplicant.conf:

```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="[SSID]"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk="[text psk]"
}

```

My /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

---

### Post by RobotGymnast on 2011-02-27
bump

---

### Post by RobotGymnast on 2011-02-27
bamp

---

