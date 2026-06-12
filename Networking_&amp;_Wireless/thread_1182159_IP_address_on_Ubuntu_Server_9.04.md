---
title: "IP address on Ubuntu Server 9.04"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by hitman_dreams on 2009-06-08
On a normal windows server you turn the machine on and before logging in, your server has an IP address...with Ubuntu Server, you don't. Anyone know how to fix this? I need this server to be restarted and given an IP address without any human intervention for things like doing remote work on it.

---

### Post by brabo on 2009-06-08
you should specify a fixed ip address then in
/etc/network/interfaces

or, if you get a dynamic ip directly from a modem, use a dynamic hostname like dyndns and the likes offer.

post back if that's not what you meant or so ^^

brabo.

---

### Post by chili555 on 2009-06-08
See post #2 here:  [http://ubuntuforums.org/showthread.php?t=1180469](http://ubuntuforums.org/showthread.php?t=1180469)

---

### Post by hitman_dreams on 2009-06-08
Is that different than setting a static IP through the network tools? That's where I set the static IP address. When I open /etc/network/interfaces it is not in there, only the wired network is there but I'm running off of wireless, which is not in that file.

---

### Post by hitman_dreams on 2009-06-08
Thanks chili, that did help some. In that post eth0 is used, I'm assuming that was a wired connection. Since I'm using a wireless do I need to add what my wireless is plus all the same information regarding my IP address etc.?

---

### Post by chili555 on 2009-06-08
Yes, indeed you do. Here is an example using WEP encryption. If you are using WPA, it's a bit more complex: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid <your_essid>
wireless-key <your_key>
```

---

### Post by hitman_dreams on 2009-06-08
I am able to get a static IP address, but can't seem to get the address on boot before the log in. I used [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) to go through and set it up for on boot, but it doesn't work. I don't know if this helps but I am using an atheros card/driver and ath0 for everything.

---

### Post by hitman_dreams on 2009-06-09
Chili, thank you for your help! I got this working on another computer using the eth0 connection which is what we needed in the end. You're the best!!!

---

