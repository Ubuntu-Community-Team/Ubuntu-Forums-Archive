---
title: "How do I install D-Link router to work on Ubuntu"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by Scomeau on 2012-11-14
I have hooked everything up and the router is working fine with the   modem but as soon as I try to install it on the computer through URL   address the book gave me, it won't find the IP address of the computer   or anything it needs to find :sad: I have been using Ubuntu for a while but still don't understand much. Any help would be nice :smile:

---

### Post by ahallubuntu on 2012-11-14
There is nothing specific to an operating system when configuring a router.  (Except for Apple Airport products.)  Configuring your D-Link router can be done via a web browser whether you are using Windows, Mac, or Linux.  All of the smarts are in the router.  No driver is required.

If you can provide more information about your setup, that would help.  How are you connected to the router - wired?  Wirelessly?  Start with a wired connection to one of the D-Link LAN ports if you can.  Are you connecting to it?  

What model D-Link is it?  What make/mode of modem?  How is it connected together?

Do you get an IP address?  In a terminal window in Ubuntu, type:

```
ifconfig
```

If you get an IP address like 192.168.1.5 (the 5 will probably be different for you), then you can go to [http://192.168.1.1](http://192.168.1.1) .  If you got 192.168.2.5 you'd go to [http://192.168.2.1](http://192.168.2.1) to configure.

There's also the chance your modem uses the same subnet - so 192.168.1.1 might also go to the modem.  The modem and router should use different subnets.  If one is 192.168.1.1 the other should be something different.

---

