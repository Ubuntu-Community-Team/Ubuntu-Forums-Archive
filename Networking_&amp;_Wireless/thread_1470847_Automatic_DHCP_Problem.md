---
title: "Automatic DHCP Problem?"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by jejo11 on 2010-05-03
Hi friends,

I'm a new user to ubuntu and I have installed 10.04 in my desktop. I've configured my internet connection with manual DHCP and it was working fine. 
The problem is that when I try to configure it to Automatic DHCP with router congiured for automatic dhcp, My ubuntu updates and software installation are working fine, but I'm not able to browse through the browser(Displaying connecting).

With the same configuration in the Windows XP I'm able to browse web.

Please help me to figure out the solution for this.

---

### Post by P4man on 2010-05-03
sounds like a problem with DNS? Have you set it to "automatic" or "automatic addresses only" ? 

Anyway, if the first option and it doesnt work I suspect something fishy with your router settings (does it have dns server configured, or is it forwarding requests to your ISP?)

If so, try the second option and manually add google's DNS servers:

8.8.8.8, 8.8.4.4

If it its the latter, then you have to specify your DNS servers, see above (or use those of your provider, or set the router IP to have the router forward the DNS queries).

---

### Post by jejo11 on 2010-05-04
Thanks for your help

I've set it to automatic DHCP and it was not working and now I've set it to automatic dhcp only address and manually entered open dns addresses and it is working.

I still want to know that what is the difference between windows and ubuntu when I configured in windows 7 set IP and DNS automatically,is working perfectly but with ubuntu I have to give the DNS address.

---

### Post by P4man on 2010-05-04
AFAIK, there shouldnt be any difference. How is your router setup? Does it have DNS servers of your provider configured? If so, can you look them up and try those in ubuntu, rather than using google's? Maybe its something with your provider, possibly related to ipv6.

---

