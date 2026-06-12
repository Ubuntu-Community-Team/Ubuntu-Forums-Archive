---
title: "connecting wireless and eth"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by monkeyking on 2009-03-30
Hi,
I'm having a somewhat strange problem.

I got a private router linksys wrtgl54.
This router is connected to the inet through another router.
But the problem is the following.

I got a laptop using wlan,
I got a desktop using eth0.

Both of these can access the internet, and ping themselves.
But neither can ping eachother.

Using netview(windows) I can see both of my machine but can only ping the local machine. When I click network neighborhood I can also see both machines(windows), but doublecliking or righclicking and selecting properties gives me a timeout, or something like, the selected machine is not on the network.

When using the tracert utility, it seems it is trying to go all the way out on the internet, instead of just using a local dns.
I really have no idea what is happening.

btw my wrtgl54 is using opendns while, the next router is using something else.

thanks in advance



The reason I want to do this,
is simply for beeing able to reboot or shutdown the computer remotely(windows).

If anyone has a better idea than using 'shutdown', I'll be happy to  know.

---

### Post by abyssius on 2009-03-30
> Both of these can access the internet, and ping themselves.
But neither can ping each other.

I know that the router has a feature called [AP Isolation] which allows wireless clients to access the internet, but keeps each client isolated from other computers on the LAN. Maybe this is enabled?

---

### Post by monkeyking on 2009-03-31
Thanks for your reply.
But the ap isolation was off,
so that wasn't the problem.

---

