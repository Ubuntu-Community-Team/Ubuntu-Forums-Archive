---
title: "Strange network behaviour"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by Nonno Bassotto on 2006-06-15
I'm using a pcmcia card wih ndiswrapper and windows drivers. Everything works well, except for one thing: I must plug my card only after boot. If I leave it inserted at boot time, my laptop will freeze. According to
[http://www.ubuntuforums.org/showthread.php?p=938949&highlight=mapping+hotplug#post938949](http://www.ubuntuforums.org/showthread.php?p=938949&highlight=mapping+hotplug#post938949)
this is caused by the line
```

auto wlan0

```
in /etc/network/interfaces: one shouldn't use this instruction since auto wlan0 will be executed before pcmcia is ready and cause the disaster. Following that thread and the guide linked there I modified /etc/network/interfaces to look like
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
mapping hotplug # I added this lines
    script grep    # I added this lines
    map wlan0    # I added this lines

iface wlan0 inet dhcp
wireless-essid CASA

# auto wlan0     # I commented out this line

```
I thought that everything should work this way, and instead the card refuses to work: the led lights up but nothing more. iwconfig doesn't show wlan0 anymore, but rather
```

sid0             no wireless extensions

```
:confused: What could be happening?

---

### Post by noname101 on 2006-06-15
I think if you get rid of auto wlan0 then you have to specify the ip address and stuff.
So make it look something like:
```
iface wlan0 inet static
wireless-essid CASA
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
```

---

