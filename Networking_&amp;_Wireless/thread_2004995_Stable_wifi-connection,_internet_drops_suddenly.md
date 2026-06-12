---
title: "Stable wifi-connection, internet drops suddenly"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by dannyvanderzande on 2012-06-16
Im running a ubuntu 12.04 box with a wireless card in it. I have 2 wired ethernet connections. eth0 is used for regular network access (downloads/sharing etc) while eth1 is connected to bridge with wifi.

I managed to set up a wireless network with wpa2 security using hostapd. Everything seems fine, connecting takes just a few seconds. Everything seems to work great and the connection is stable. However after a few minutes of usage I can't seem to recieve any data on my devices any more even though I have a great wifi signal and I'm still connected...

Here are my config files

```
/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.125
    netmask 255.255.255.0
    gateway 192.168.1.1

# The secondary interface --> wifi-accesspoint
auto eth1
    iface eth1 inet static
    address 192.168.1.126
    netmask 255.255.255.0


# The wireless interface --> wifi-accesspoint
#auto wlan0
#iface wlan0 inet static
#    adress 192.168.1.127
#    netmask 255.255.255.0
#    gateway 192.168.1.1

# The bridge interface for "wiring" eth1 and wlan0 together
auto br0
iface br0 inet static
     address 192.168.1.128
     netmask 255.255.255.0
     bridge_ports eth1

```

/etc/hostapd/hostapd.conf
```

interface=wlan0
driver=nl80211
bridge=br0
hw_mode=g
channel=9
#country code=NL
ssid=Not Important
# 1=open auth, 2=shared key, 3=both
auth_algs=3
# # Static WPA2 key configuration
# #1=wpa1, 2=wpa2, 3=both
wpa=2
wpa_passphrase=***********
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
# #this can create problem with Windows clients, just leave it commented
# rsn_pairwise=CCMP

logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2

```

Does anyone have a suggestion/pointer on how to fix this?

---

### Post by gmh on 2012-06-19
I had the same issue. Wireless on 12.04 has been a real pain in the @^!# for me. First up it would not connect to a wireless N network (which I seemingly fixed with a Kernel upgrade by accident while fixing a hardlock problem) but now I have this dropout bug. After a bunch of trial and error, I uninstalled network manager and installed Wicd which seems to have fixed the issue for me for the time being. Easy to do through Synaptic. Would be curious to see if it works for you.

*This fix failed as well*

---

