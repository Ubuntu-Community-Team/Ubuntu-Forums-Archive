---
title: "Dual IP addresses on eth0?"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by Stronghol on 2009-07-31
How do I set up two IP Addresses on eth0? I want to assign it a public IP so I can access it from the net.

---

### Post by Iowan on 2009-07-31
Seems like aliasing might work... but how do you access internet - direct of via router/modem? If it's through another device, you will probably need to set up port forwarding.

---

### Post by iponeverything on 2009-07-31
> **Iowan said:**
> Seems like aliasing might work... but how do you access internet - direct of via router/modem? If it's through another device, you will probably need to set up port forwarding.

yes.. its not as easy as just giving yourself a public address. The rest of the universe needs to know how to find you. 

sudo ifconfig eth0:1 <address> netmask <mask> 

will add a secondary address to an interface.

A better route for you might be to check to see if the your ISP is issuing your device (dsl modem, cable modem, etc) a public address and if they are -- just setup a portforward for the service that you need to access from the outside.

---

