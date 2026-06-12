---
title: "Wired and Wireless Internet conflict"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by KyHx on 2010-11-07
I get my Internet connection from a wireless router (from a neighbor in my apartment complex) When I connect my computers to a switch FOR THE ONLY REASON of file transfer it tries to get my Internet connection from it.

So is there a way I can set my wireless connection to be my primary connection?

---

### Post by KyHx on 2010-11-07
I figured it out, sorry this thread may be removed.

I found a thread about ip routing tables and removed the default and then added the wlan0 gateway as default.

```
 sudo ip route delete default via 192.168.0.1 dev eth0 proto static

```

then

```
sudo ip route add default via 192.168.1.1

```

---

