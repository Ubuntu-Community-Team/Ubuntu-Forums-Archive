---
title: "Cannot remove package"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by RFXCasey on 2012-10-21
Hey all, sure this has been asked and I've found several post about similar situations with different packages. Anyways I just installed Ubuntu server and I'm trying to set it up for a static IP. First question is after following this post [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

I'm unclear what the broadcast field is and whether or not I need it and if so what the address should be.

The other problem I am having is when trying to remove the dhcp-client package I get an error stating 'Virtual packages like 'dhcp-client' can't be removed'

Is there any way to get rid of it? Do I really have to? And if I don't does it leave a security hole open? Thanks.

---

### Post by 2F4U on 2012-10-21
In my static network configuration, I only use the fields
- address
- netmask
- gateway

I haven't removed dhcp-client, because it doesn't hurt to be there and it won't be used.

---

