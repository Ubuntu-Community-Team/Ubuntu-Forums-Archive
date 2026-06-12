---
title: "OpenDNS, Network Manager is adding IP's DNS as well"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by User3k on 2009-12-17
I have OpenDNS set up and it is working fine. But I am wondering about something. I used hardinfo and I noticed that it is showing me that both OpenDNS ip's are there, 1st and 2nd, but 3rd and 4th are showing my IP's DNS. Why is this?

---

### Post by kerry_s on 2009-12-17
because its read from your router.

---

### Post by bruno9779 on 2009-12-17
> **kerry_s said:**
> because its read from your router.

+1

your router has a dns server too

---

### Post by User3k on 2009-12-17
You mean my cable modem then?


So is it,

My computer>Modem>IP's-DNS>OpenDNS?

---

### Post by kerry_s on 2009-12-17
> **User3k said:**
> You mean my cable modem then?


So is it,

My computer>Modem>IP's-DNS>OpenDNS?

if you have the opendns set it will use those first, if those fail then the router dns is used. it go's down the line, look in /etc/resolve.conf you should have opendns first & your modem dns after.

---

### Post by wojox on 2009-12-17
Sounds like you didn't set it up right: [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

---

### Post by User3k on 2009-12-17
> **wojox said:**
> Sounds like you didn't set it up right: [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

Thank you, I did have it set up wrong, well half wrong, lol.

I followed directions for Xubuntu but they where not the same directions as the link you provided. It appears that I had it half set up. It is now set up perfectly and the only two DNS addresses there are for OpenDNS.


Thanks for the help and trouble shooting this everyone.

---

