---
title: "Realtek RTL81111DL network disabled"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by dargaud on 2009-04-07
Hello all,
I just changed mobo (Asrock M3A790GXH/128M) and I can't get the onboard network card to work. I have most of the symptoms of [this old thread]("http://ubuntuforums.org/archive/index.php/t-1099828.html") that was related to wireless:
- lshw shows "network disabled / logical name pan0"
- /etc/network/interfaces contains neither eth* nor pan0 (adding them doesn't change anything)
- ifup pan0 returns "ignoring unknown interface pan0=pan0"

The strange thing is that I plugged in an old e100 card and I get exactly the same failures although that one is on eth2.

```

# lshw -c network
*-network DISABLED
  description: Ethernet interface
  physical id: 1
  logical name: pan0
  serial: ba:...
  capabilities: ethernet physical
  configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
*-network DISABLED
  description...
  product: 82557/8/9/0/1 Ethernet pro 100
  physical id: 6
  logical name: eth2
  ... (many more options for this card)

# dmesg | egrep -i "realtek|rtl|net"
net_namespace: 1552 bytes
NET: registered protocol family 16/8/20/2/1/10/31
Netlabel...
audit: initializing netlink socket (disabled)
e100: Intel PRO/100 network driver, 3.5.23-k4-NAPI
udev: renamed network interface eth0 to eth2
ip_tables...

# cat /etc/network/interfaces
auto lo
iface lo inet loopback

# ifconfig -a
eth2 link encap:Ethernet HWaddr 00:90...
     Broadcast multicast mtu:1500 metric:1
     RX packet:0... all 0
pan0 link encap:Ethernet HWaddr ba:13...
     Broadcast multicast mtu:1500 metric:1
     RX packet:0... all 0
lo   ...

```

If it's a driver problem (card too new), then how come the old one fails in the same way ?!? A general misconfiguration somewhere ? 
Thanks a bunch, I have a useless paperweight until this works (and the onboard DVI, but that's not a linux problem).

---

### Post by dargaud on 2009-04-07
OK, so upon further research, pan0 is for blutooth, so I was confusing the two. Probably means that the card is not recognized (BTW, it's a RTL8111DL, there was one '1' too much in the title). But it still doesn't explain why my old card doesn't work also. No RX/TX lights on the onboard nic when I connect a network cable, while the old card lights up properly.

Apparently there's a [workaround on this thread]("http://ubuntuforums.org/showthread.php?t=1022411")... which worked like a charm ! Let's just hope that the new driver makes it into the next iteration of the kernel. Go Linus !

---

