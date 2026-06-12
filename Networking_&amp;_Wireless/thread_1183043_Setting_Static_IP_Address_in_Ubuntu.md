---
title: "Setting Static IP Address in Ubuntu"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-06-09
I have two Ubuntu machines, and I would like to make it so that their IP addresses do not change when the router reboots or other things like that. Basically I want to set static IPs on these machines; that way when the router loses power or something it doesn't randomly reassign IP addresses, which makes it hard for me to use SSH and things like that (can't SSH a machine if I don't know what the IP is!). Is there a simple/easy/good way to do this? I was looking around the network manager and it looks like I might be able to do it through there, but I'd really rather know the answer before I go about destroying my internet connectivity. Thanks! Oh, and if it's relevant at all, I have a Belkin router currently.

-Dan

---

### Post by chili555 on 2009-06-09
See post #2 here: [http://ubuntuforums.org/showthread.php?t=1180469](http://ubuntuforums.org/showthread.php?t=1180469)

You will also need to make sure that your file */etc/resolv.conf* is set up with a nameserver; usually the IP address of your router is fine. Following my example, it would read like this:```
nameserver 192.168.1.1
```Substitute your details here.

---

