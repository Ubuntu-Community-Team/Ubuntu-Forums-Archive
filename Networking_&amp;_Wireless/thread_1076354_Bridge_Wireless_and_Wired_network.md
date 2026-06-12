---
title: "Bridge Wireless and Wired network"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by kvcxn on 2009-02-21
Hey,

What I'm trying to do is basically this, except I'm connecting the cable to a Desktop computer rather than a PS2:
[http://ubuntuforums.org/showthread.php?t=632062](http://ubuntuforums.org/showthread.php?t=632062)

I'm trying to bridge my eth0 interface with my wireless ath0 interface so that I can connect to the wireless connection on my laptop and also be able to use it on my desktop. 

As soon as I follow Friek's solution and bring up br0, I can no longer connect to the internet on my laptop:

```
brctl addif br0
ifconfig br0 up

```

In addition, I don't know how to supply the wireless network the password.

Any help is appreciated, thanks

edit: 
Using Ubuntu 8.04

Also, I'd like to mention I have Windows Vista on this laptop and bridging on Windows solves the problem. That is, after bridging the networks on Windows, I'm able to connect to the wifi on my desktop. But I don't want to have to boot into windows every time I want to bridge the two networks.

---

### Post by superprash2003 on 2009-02-21
so you basically want to setup an adhoc network between laptop and desktop???and then share the internet connection ..
1)setting up adhoc network - [http://www.prash-babu.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://www.prash-babu.com/2008/08/how-to-createjoin-adhoc-network-in.html)
2)sharing internet connection - [http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html](http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html)

---

