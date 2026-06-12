---
title: "How can i disable ipv6 in jaunty?"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by BlackDex on 2009-04-27
Hello there,

I need to disable ipv6 in jaunty, but i can't seem to get it to work.

I tried adding it to the blacklist, but because it is compiled into the kernel this won't work i think.

I also added /proc/sys/net/ipv6/conf/all/disable_ipv6.
But every time i reboot the contents reverts to 0.

How can i prevent it from turning my 1 into a 0 on reboot??

Or are there any other ways of disabling ipv6?

thx in advance.

---

### Post by BlackDex on 2009-04-27
I already saw that thread. But that didn't worked.
Hope a new thread would help me :).

I now posted a reply in that thread hoping it can help.

---

### Post by uniden9 on 2009-04-27
Add the kernel option to your /etc/sysctl.conf

$sudo echo net.ipv6.conf.all.disable_ipv6 = 1 >> /etc/sysctl.conf
$sudo sysctl -p

This will make the setting persistent between boots.

---

