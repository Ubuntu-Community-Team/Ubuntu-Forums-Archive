---
title: "Host Website with dynamic IP address with NAT"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by MDguy on 2010-11-06
We have Verizon as our ISP with a dynamic IP address. We published our website but the IP changes frequently. How can we set Network address translator(NAT) so our website can be published regardless of IP changes? We don't have domain name and have no intention for one. I appreciate if anybody can share your experience.
Best regards,
MDguy

---

### Post by lisati on 2010-11-06
I'd be inclined to look into getting a domain name to use, even if you don't publish it to the general public. 
I use FREE domain names from [no-ip]("http://no-ip.com") and [DynDns]("http://www.dyndns.com"), both of which have a user agent process that can take care of updating the DNS records automatically.

If getting a domain name isn't an option, for whatever reason, an alternative might be to have a process that periodically checks to see if your public IP address has changed, and then email the people who might need to know. I'm not sure how to implement this, but have seen it described in the forum.

---

### Post by uncaspi on 2010-11-06
I don`t think it can be done without static address. Have never heard of it.

---

