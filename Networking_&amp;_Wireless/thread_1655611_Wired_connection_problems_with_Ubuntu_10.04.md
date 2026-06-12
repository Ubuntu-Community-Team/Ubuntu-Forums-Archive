---
title: "Wired connection problems with Ubuntu 10.04"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by unhunkygiuy on 2010-12-29
Hi, I can't seem to be able to connect to the internet in my Ubuntu 10.04 Dell Dimension E-310 desktop. I am able to connect to the router(a 2wire AT&T wireless gateway) with my UNR 10.10 Lenovo ideapad S10-3t both wired and wirelessly. I tried connecting manually to the router on my desktop using the eth0 connection but it still says "You are now offline" after a few seconds. Any help would be greatly appreciated.

---

### Post by supershin on 2010-12-29
Ensure the desktop is getting an ip address from the router. In terminal type "ifconfig /all". You'll see a listing with ip address, subnet mask, default gateway etc

The default gateway should be the address of your router.

---

### Post by unhunkygiuy on 2010-12-29
@supershin

I tried it, but all it says is:
```
/all: error fetching interface information: Device not found
```


EDIT:

I was able to establish a connection. What I did was type into the terminal "ifconfig", use the "inet addr:" and "Mask" for "lo". I put in the data manually into IPv4 Settings and disabled IPv6 Settings. THANKS!

---

### Post by supershin on 2010-12-30
Ipv6 was on? Then that could have been why. Your connection must only be able to support IPv4. If you get further problems you can just try setting IPv4 to connect automatically, it should work.

---

