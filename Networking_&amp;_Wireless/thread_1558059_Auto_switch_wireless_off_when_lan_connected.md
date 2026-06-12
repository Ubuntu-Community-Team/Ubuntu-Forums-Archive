---
title: "Auto switch wireless off when lan connected"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by mikeglover on 2010-08-21
Hi,

I currently have a command line Ubuntu 9.10 installation.

I wish to be able to have either both wireless and wired connection working 

For example: when LAN is connection the wireless is switched off, when LAN is disconnected the wireless comes up (WPA2)

I know that the Network Manager in Gnome does this auto switching for you but I need to know how to do this in command line only.

Any help would be appreciated

---

### Post by LightningCrash on 2010-08-21
in the file  /etc/network/interfaces you could add the following two lines under eth0:
post-up ifdown wlan0
post-down ifup wlan0

that is of course assuming that your ethernet is eth0 and your WiFi is wlan0. they might not be, in some cases.


but for instance, mine would look like:
```

auto lo eth0
iface lo inet loopback
iface eth0 inet static
        address 10.0.0.2
        netmask 255.255.255.0
        gateway 10.0.0.1
        pre-up iptables-restore < /etc/iptables.rules
        post-up ifdown wlan0
        post-down ifup wlan0

```

If you need some more information on the /etc/network/interfaces file you can always type "man interfaces" at a console.

-LC

---

### Post by mikeglover on 2010-08-22
Doesn't seem to be working.

Here is the contents of my inferfaces file, can't see what's wrong.


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# Wired
auto eth0
iface eth0 inet static
address 192.168.0.173
netmask 255.255.255.0
gateway 192.168.0.1
post-up ifdown wlan0
post-down ifup wlan0

# The secondary network interface
# Wireless
 iface wlan0 inet static
 address 192.168.0.110
 netmask 255.255.255.0
 gateway 192.168.0.1
 wpa-ssid         */ my SSID goes here /*
 wpa-ap-scan      1
 wpa-proto        RSN WPA
 wpa-pairwise     CCMP TKIP
 wpa-group        CCMP TKIP
 wpa-key-mgmt     WPA-PSK
 wpa-psk          */my key goes here/*
 wireless-channel 12
 wireless-mode    managed

```

---

