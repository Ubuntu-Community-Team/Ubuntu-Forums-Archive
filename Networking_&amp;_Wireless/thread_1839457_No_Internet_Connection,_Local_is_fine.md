---
title: "No Internet Connection, Local is fine"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by Kikketer on 2011-09-05
I have the Ubuntu minimal installed, it's actually an XBMC box.  I am unable to connect to the internet with this box and was wondering if I am missing something, it appears to be all set up correctly.

Windows machines, and a second Ubuntu (full) machine all work correctly.  Both via wireless and wired (using the same connection).

I am able to ping my router at 192.168.0.1 and ping the other machines on the network.  When I attempt to ping [www.google.com]("http://www.google.com") or [www.yahoo.com]("http://www.yahoo.com") it returns an IP but times out on the ping.  I've tried both the wireless and wired connections.  Both have the same outcome.

Does anyone have an idea what could be causing this issue?

uname -a:
```

Linux xbmc 2.6.35-28-generic-pae #49-Ubuntu SMP Tue Mar 1 14:58:06 UTC 2011 i686 GNU/Linux

```ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:30:18:a2:c7:12
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3468 (3.4 KB)  TX bytes:3468 (3.4 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:2e:4a:f3
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76f0:6dff:fe2e:4af3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1895508 (1.8 MB)  TX bytes:662753 (662.7 KB)

```route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0

```cat /etc/resolv.conf:
```

nameserver 192.168.0.1

```

---

### Post by papibe on 2011-09-05
Welcome!

For what I can see, both your wired (eth0) and wireless (wlan0) are connected to the router (even using different IPs). That is not good.

Which connection are you really using? Try disabling the other one.

Do yo have network-manager or are you using a minimal install?

Regards.

---

### Post by Kikketer on 2011-09-13
Sorry it took so long, I was busy messing with other things.
I'm using the minimal install, and thought that by having both it would pick one (the one that is connected).

I believe I have it set up where it would pick wireless first, if that fails go to wired.  I can't remember now where that bit was.

After a few more trial and errors in a controlled environment, I realized that when the box booted up without a wired connection it worked fine.  It appears that when it boots wired, it gets confused and fails all together.  I also did notice that the wired lights are not blinking either.
So it's almost as if it sees the wire, then shuts everything down.

I am willing to turn off the wireless completely, but would rather it default to wireless only if wired is disconnected.
Is there a way to do this?

Thanks!

---

### Post by papibe on 2011-09-14
You can disable your wireless by customizing /etc/network/interfaces

Could you post the current content of that file?

Regards.

---

### Post by Kikketer on 2011-09-18
/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Wireless
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

# Wired network
auto eth0
iface eth0 inet dhcp

```

I'm attempting to comment out the wireless bit and reboot.  I'll let you know what happens then.

---

### Post by Kikketer on 2011-09-18
Ok so disabling the wireless completely worked.  This will get me by, as I won't be moving the machine to a wireless connection anytime soon.

Thanks for the help!

---

