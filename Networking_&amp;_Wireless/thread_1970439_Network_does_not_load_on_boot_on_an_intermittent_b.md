---
title: "Network does not load on boot on an intermittent basis"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by sefs on 2012-05-01
Hi,

I've installed 12.04.  The problem I am experiencing is that the network does not load all time time.

So on the purple screen with the logo and loading dots I get the message...

"Waiting for network configuration"  

It will sit there for a while then display

"Waiting up to 60 more seconds for network configuration"  

Then it will go to the login prompt and i can log in.

If I do a "ifconfig"  eth0 is not there.  I would then have to do a "/etc/init.d/networking restart"  and then eth0 will appear and the network will start.

This happens in my estimation about half the time.

Thanks.

---

