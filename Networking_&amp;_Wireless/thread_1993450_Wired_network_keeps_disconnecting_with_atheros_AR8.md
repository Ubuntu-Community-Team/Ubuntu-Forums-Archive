---
title: "Wired network keeps disconnecting with atheros AR8131"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by alberto1976 on 2012-06-02
Hi all,

I am running Ubuntu on my Sony Vaio laptop.
Wireless network works fine (AR985).
When I plug in the ethernet cable, I get connected to the network but the connections go down invariably every 30 seconds or so. I tried many cables and in different networks. 
This happens whether or not I disable wireless.

I am using NetworkManager to manage my connections.
the output of 
```

cat /etc/NetworkManager/NetworkManager.conf

```is
```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=true

```I have changed the "managed" to true following an online suggestion, but it didn't make any difference.
The output of 
```

cat /etc/network/interfaces 

```is
```

auto lo
iface lo inet loopback

```I experienced this problem with Ubuntu 11.10 and upgrading to 12.04 did not fix it.

There is a related (unsolved) old post at 

[http://ubuntuforums.org/showthread.php?t=1527628](http://ubuntuforums.org/showthread.php?t=1527628)

Any help is much appreciated!

---

### Post by LoveIsLost on 2012-06-16
Same problem here!:(

---

