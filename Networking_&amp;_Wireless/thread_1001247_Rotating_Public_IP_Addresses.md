---
title: "Rotating Public IP Addresses"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by stygma on 2008-12-03
Hey,

I have a few public IPs I can use and I need to be able to rotate through them. Is there anyway I can make my ubuntu server box rotate through the IPs that will be viewable by the people that I am browsing?

I program ruby, so if anyone knows of a solution that I can program myself there I would appreciate knowing how.

---

### Post by doas777 on 2008-12-03
well you could set up a cron job and a script/applet to reconfigure your /etc/network/interfaces file, then down and re-up the network stack and the interface, but doing so would drop all existing connections, so doing it automatically on a schedule could be awkward if you are actually using the network.

I have to ask, why do you want to do such a thing? I can't come up with any good reason to do so. if it's a privacy thing, I'd recommend application layer proxies rather than a network re-configuration.

have fun

---

