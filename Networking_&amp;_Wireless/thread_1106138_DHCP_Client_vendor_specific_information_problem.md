---
title: "DHCP Client vendor specific information problem"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by rjcarlson49 on 2009-03-25
How do I set up DHCP client to send the vendor specific identifier in option 60 and request option 43 in response? I have edited /etc/dhcp3/dhclient.conf and that seems to produce no change in the DHCPDISCOVER. I have restarted the network and rebooted. No joy.

I have tried variations on "send vendor-class-identifier "<id string>" and nothing is ever sent.

I have tried "request ..., 43;" and "request ..., vendor-encapsulated-options;" and the request list in the DHCPDISCOVER did not change.

How do I get this to work?

-Bob

---

### Post by rjcarlson49 on 2009-03-26
Doesn't anybody know how thte DHCP client works on Ubuntu?

---

### Post by rjcarlson49 on 2009-03-31
Surely someone knows this.

-Bob

---

