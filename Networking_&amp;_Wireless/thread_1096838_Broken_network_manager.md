---
title: "Broken network manager"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by sxam08 on 2009-03-15
I broke my Network manager and would like to know how to fix it.

Last week I was having problems with my DSL internet. Usually the DSL modem is connected to my router and my computer to the router, to check my problem was not router related I connected my computer directly to my modem and set up a new DSL-modem PPPoe widget. I did eventually get that working but the problem was my ISP.

So after my ISP fixed their problem I turned off that connection via poff dsl-provider and everything was working fine (connected normally via router to modem)

Until I restarted.

I could not get connection working at all after I started. And network manager when I left click says under "Wired Network" that "device is unmanaged". I removed the DSL connection (which still existed) and restarted. No good. A few more attempts at stopping and starting eth0 (wired interface) all failed. I made sure the wired connection in network connections was correct. More restarts.

Nada.

I finally sort of resolved it by looking at /etc/network/interfaces where I noticed among other things that the dsl-provider stuff was still in there (not commented out) and set to auto (even though it is not listed in Network Connections - DSL. I manually edited /etc/network/interfaces to be the following
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

And restarted and I am on the internet. Hoo-ray. 

But now it's as if the GUI is out of sync. Networking manager still says the device is unmanaged and if I click "Connection information" then I get an error dialog that says "Error displaying connection information: No valid active connections found"

Well. I'm connected to the internet so there is A valid active connection. 

How can I fix this?

PS. This is Ubuntu 8.10 kernel 2.6.27-11 generic

---

### Post by sxam08 on 2009-03-15
Fixed.

I commented out eth0 in /etc/network/interfaces after reading a few threads that I didn't think were related but I guess are.

What threw me and could help someone in future is that the DSL setup put some stuff into /etc/network/interfaces but whatever appears there won't be managed by the Network Manager. So remove (comment out) everything but the localhost stuff and it seems to be working fine again.

---

