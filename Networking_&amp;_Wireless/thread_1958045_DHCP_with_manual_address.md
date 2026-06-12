---
title: "DHCP with manual address"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by Alabamian on 2012-04-13
I'm trying to do something that's very, very easy on the Macintosh.  We're on a DDNS configured network.  I have no control over the DHCP server.  One of our existing Ubuntu servers needs a certain IP address (fixed), but needs to get ALL other network configuration parameters from the DHCP Server.  On the Macintosh, one can set up Eth0 with these options:

Using DHCP
Using DHCP with manual address
Using BootP
Manually

Manual won't work, because as the DDNS' change, the resolv.conf will be pointed at the no-longer-in-production DNS boxes, so no DNS resolution.  DHCP doesn't work well for this particular box, because it gets a DHCP address but doesn't bind the stored name to this server, so it disappears in terms of being able to ssh or otherwise connect to it. But if there was some way to have it use DHCP for all settings except the IP address, the second option in the Macintosh choices above, everything would be good.  Is there a way to do this?

---

### Post by Alabamian on 2012-04-17
Wow, don't everybody jump on this at once now.

---

### Post by Ms. Daisy on 2012-04-17
I was hoping you'd get some responses- I've been following your thread because I'm interested to know as well. 

I searched for an answer before, but all roads led me to reserving the IP on the DHCP server. But you said you don't have control over the DHCP server, and I didn't find a way around that.

---

### Post by SeijiSensei on 2012-04-17
Take a look at the file /etc/dhcp/dhclient.conf.  The "request" directive lists the items that will be requested from the remote server.  You can change the items in the list, or override the request with entries appearing in the "alias" and "lease" directives.  Run "man dhclient.conf" for more details.

---

### Post by lykwydchykyn on 2012-04-17
With the disclaimer that I've never actually done this, I think it can be done by editing /etc/dhcp/dhclient.conf

There are some examples in the comments of that file, or you can check out the man page for dhclient.conf (man dhclient.conf) for more details.

EDIT: man, sniped by only minutes... :)

---

