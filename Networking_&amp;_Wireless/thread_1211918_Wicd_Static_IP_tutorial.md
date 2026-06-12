---
title: "Wicd Static IP tutorial?"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Tindytim on 2009-07-13
I read on another post here that there was one, but I can't seem to find it. I can't seem to find my netmask, gateway, or the static DNS servers I'd need to use.

Any help?

---

### Post by hansdown on 2009-07-13
Hi Tindytim.

I came across one.

[http://www.dedoimedo.com/computers/wicd.html](http://www.dedoimedo.com/computers/wicd.html)

More info.

[http://www.google.ca/search?q=Wicd+Static+IP+tutorial+for+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Wicd+Static+IP+tutorial+for+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Tindytim on 2009-07-13
That's not a tutorial for setting up a static IP. And the first thing I did was a google search.

I tried using the GUI, but I do not know how to find my DNS, netmask, and gateway. Any help?

/etc/network/interfaces is just
```
auto lo
iface lo inet loopback
```

---

### Post by t0mppa on 2009-07-13
These three can be found from your routers configuration. They're not dependant on anything local on your computer and thus aren't stored anywhere, if you're using a dynamic IP as that involves polling them directly from the router. For DNS there are even free services like opendns.com which offers DNS servers for everyone who's dissatisfied by their ISP's equivalents to use.

[QUOTE=Tindytim]I can't seem to find my netmask, gateway, or the static DNS servers I'd need to use.[/QUOTE]

There's no difference for any of the above between dynamic & static. They're the same for both. Dynamic simply means that you're letting your router assign your IP, so that you don't have to go through the trouble of making sure there are no conflicts when multiple devices are connected to your network, as they all need to be assigned different IP addresses and no two can have the same one.

And if you really don't know what your netmask & gateway are, then why're you setting up a static IP in the first place?

---

### Post by Tindytim on 2009-07-13
I ended up solving this myself, but thanks for the comments.

> **t0mppa said:**
> And if you really don't know what your netmask & gateway are, then why're you setting up a static IP in the first place?I know what they are, and I understand the difference between dynamic and static IPs, but I don't know how get such information within Linux. I ended up booting into Windows and getting them.

I just realized the typo I made by putting 'static' infront of DNS.

---

### Post by t0mppa on 2009-07-14
Well, you can also get them on Linux by simply enabling a DHCP connection (like you probably did on Windows) and copying them from there, but the real source of those is on your router.

---

### Post by knowlittle on 2012-05-06
To find your global dns. Google is a good place. For example: I am with TPG and it is 203.12.160.35, 203.12.160.36, 203.12.160.37. 

First, you need also to know the following: IP address, subnet mask and gateway. (To obtain this, in Terminal: ifconfig. Your current ip address is one that follows "inet addr:". Ignore 127.0.0.01 is your local host, everycomputer is the same.) The IP address is one of your desired. Make sure it belongs to the subnet mask, else, you will not be able to connect to other computers on the subnet mask, or any computers at all. Also, make sure the ip address you like to use is not already used by another network interface. You only can do this by changing the IP range the DHCP uses to allocate from, make sure your desired IP address is not in this range. If you do not do this, you will not connect. 

You can NOT change ip address of the interface currently being used. (To do this you must stop WICD first. To stop wicd: sudo /etc/init.d/wicd stop). A better approach is to connect wired and do the change for the wireless connection, and then disconnect wire (connect to wireless) and do change for the wire. If you do not connect both at the same time, you can use the same IP address for both the wireless and wired. I do as I share my printer. If you stopped WICD earlier, you have to start it by sudo /etc/init.d/wicd start.

Check your connection, now it should be static as you like. In one instance, I had to enable networking and enable wireless from the WICD gui and restart my computer, maybe when I stopped WICD, my wireless dongle was stopped as well. Thankfully, it worked again when I restart.

---

### Post by sffvba[e0rt on 2012-05-06
Not sure OP will be checking this after so many years... but thanks for the additional info.

*Thread **closed**.*


404

---

