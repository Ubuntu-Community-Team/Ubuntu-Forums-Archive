---
title: "Route eth0 with wlan0"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by RightIsLeft on 2010-09-19
Hi.

I would like to share the wireless internet connection with eth0 interface but im not sure how i should go about routing eth0 with wlan0.

Basically , in short : all i want is eth0 to be able to access the internet via wlan0 using the route command.

Thanks for any help :popcorn:

---

### Post by Zorael on 2010-09-20
If you want to set up a bridge where your machine links together eth0 with wlan0 to create one big local network, I think a requirement for this to be possible is that you have a wireless device (and driver) that supports network address translation. Also called master mode? I don't readily recall.

The package **bridge-utils** provides the terminal program **brctl** that can help you set it up. It's probably possible using merely iptables, too.
```
$ sudo iwconfig wlan0 mode master # must not output an error, I believe
$ sudo brctl addbr bridge0
$ sudo brctl addif bridge0 eth0
$ sudo brctl addif bridge0 wlan0
*[...]*
```

If you want to set up internet connection sharing, where you act as an outward router and hides eth0 behind you as a local network, this should be easier, using iptables. I have never done it myself, so please share any success stories.

[This blog post](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html) details the procedure in short but doesn't go into details. Albeit old, there's also [this](http://ubuntuforums.org/showthread.php?t=91370) and [this](http://ubuntuforums.org/showthread.php?t=335465) thread.

Perhaps someone with real experience stops by and shares his/her wisdom.

---

### Post by RightIsLeft on 2010-09-20
> **Zorael said:**
> If you want to set up a bridge where your machine links together eth0 with wlan0 to create one big local network, I think a requirement for this to be possible is that you have a wireless device (and driver) that supports network address translation. Also called master mode? I don't readily recall.

The package **bridge-utils** provides the terminal program **brctl** that can help you set it up. It's probably possible using merely iptables, too.
```
$ sudo iwconfig wlan0 mode master # must not output an error, I believe
$ sudo brctl addbr bridge0
$ sudo brctl addif bridge0 eth0
$ sudo brctl addif bridge0 wlan0
*[...]*
```

If you want to set up internet connection sharing, where you act as an outward router and hides eth0 behind you as a local network, this should be easier, using iptables. I have never done it myself, so please share any success stories.

[This blog post](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html) details the procedure in short but doesn't go into details. Albeit old, there's also [this](http://ubuntuforums.org/showthread.php?t=91370) and [this](http://ubuntuforums.org/showthread.php?t=335465) thread.

Perhaps someone with real experience stops by and shares his/her wisdom.

Many thanks!I will try it :)

---

### Post by perspectoff on 2010-09-20
Here's my solutions for network sharing and bridging (also using bridge-utils):

[http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29](http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29)

also at:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29)

---

