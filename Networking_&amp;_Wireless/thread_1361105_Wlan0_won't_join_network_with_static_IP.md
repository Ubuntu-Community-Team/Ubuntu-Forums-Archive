---
title: "Wlan0 won't join network with static IP"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by Quarg on 2009-12-21
Hello all, I'm trying to edit my /etc/network/interfaces file in a debian 5 system to have wlan0 use a static ip. Here's what I have so far:
```

auto lo
iface lo inet loopback

allow-hotplug wlan0

iface wlan0 inet static
	address: 192.168.0.102
	gateway 192.168.0.1	
	netmask 255.255.255.0
	network 192.168.0.1	
	broadcast 192.168.0.255
	dns-domain lan
	dns-nameservers 192.168.0.1

	wireless-essid PhillipsDlink
	wireless-key   s:tuxxx
	wireless-channel 1
	wireless-keymode open
	wireless-mode managed

```
when i restart by /etc/init.d/networking restart
and then do a
```

#ifup wlan0

```
I get this output: 
```

Don't seem to have all the variables for wlan0/inet
Failed to bring up wlan0

```
any ideas as to what I'm doing wrong? messing with the network never seems to work with me.

---

### Post by Iowan on 2009-12-21
The network address may be unnecessary,
If included, it should probably end in "0" (192.168.0.0).
(The broadcast address may also be unnecessary.)

---

### Post by Quarg on 2009-12-21
tried taking that out. same error message. Thanks though.

---

### Post by Iowan on 2009-12-21
Does Debian 5 use Network Manager? If so, have you tried a manual configuration there?

---

### Post by Quarg on 2009-12-21
I'm not using a gui, and don't like network manager. (The purpose of this box is a kernel building machine, that i can ssh into and build a kernel)

---

### Post by acho on 2009-12-21
put your dns ip. if u use static config... sometimes automatically dns can't connected as well...

---

