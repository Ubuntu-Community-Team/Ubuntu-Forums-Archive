---
title: "HOWTO Home wifi access point the newbie way"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by daigorobr on 2006-01-28
It's more like a patchwork of other people's job, but it worked right for me and, with few adaptations, may be used by others.
I use it mostly for sharing internet with my Playstation Portable.

1. First you have to install your madwifi modules. I strongly suggest using [this]("http://ubuntuforums.org/showthread.php?t=105437&highlight=madwifi+ng") method since madwifi-ng added master mode to many cards.

2. The forementioned Howto is great, but madwifi goes to managed mode by default. That's why you have to use this line under your ath0 (or whatever iface it is) dection in /etc/network/interfaces:
```
pre-up wlanconfig ath0 destroy && wlanconfig ath0 create wlandev wifi0 wlanmode ap
```
(Just remember to change the ath0 bits for your own interface name)
Mine got like this:
```
iface ath0 inet static
	pre-up wlanconfig ath0 destroy && wlanconfig ath0 create wlandev wifi0 wlanmode ap
	address 192.168.1.1
	netmask 255.255.255.0
	wireless-mode master
	wireless-essid your_ess_id
	wireless-key s:your_pwd
	auto ath0
```

3. The dirty work is done, and you only have to [share your connection]("http://ubuntuforums.org/showthread.php?t=91370&highlight=share+internet+connection+howto") with the listener devices.

Voilà, it's done!

Just to remember that I didn't really know how to setup the DHCP server so I used fix IP address. And had to set everything manually in the client side too.

Seeya.

---

