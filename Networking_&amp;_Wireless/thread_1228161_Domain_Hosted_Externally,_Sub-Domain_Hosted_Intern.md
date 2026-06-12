---
title: "Domain Hosted Externally, Sub-Domain Hosted Internally... What to do with bind?"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by chris.zeman on 2009-07-31
I have a domain that is hosted by my web host. I'll call it "example.com" for the sake of this message. I am setting up a Zimbra server and a couple of Samba servers for my LAN. The Zimbra server will be accessible from the Internet & LAN as "secure.example.com". Machines on the LAN will use the Zimbra server for a nameserver and will have their own entries in bind. 

Is it possible to configure bind so that any names associated with example.com that don't exist in my bind configuration will be checked against my web host's nameservers (ie, [www.example.com](www.example.com), etc.)?

Thank you,
Chris

---

