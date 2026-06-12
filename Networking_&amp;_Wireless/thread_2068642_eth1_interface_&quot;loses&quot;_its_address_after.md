---
title: "eth1 interface &quot;loses&quot; its address after a while"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by ulello on 2012-10-09
I'm using Ubuntu on VirtualBox, but I think this is not important in my case.

When I use the command
```
sudo ifconfig eth1 192.168.2.1 netmask 255.255.255.0 broadcast 192.168.2.255 up
``` the interface works as expected, in fact I can ping other (virtual) machines on the same subnet.

But after a while (even if I don't perform any action) seems like the interface "loses" its ipv4 configuration, in fact the output of ```
ifconfig
``` is
[IMG]https://dl.dropbox.com/u/101333517/Schermata%202012-10-09%20a%2017.24.55.png[/IMG]

As you can see, the line of the ipv4 configuration is absent.

Why? How can I resolve?

---

