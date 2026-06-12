---
title: "Mobloquer issue"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by nmxdaven on 2011-07-24
Hey guys!

I've recently switched from iplist to mobock and im using mobloqer to manage it. I have a very large block list. Everything updates fine, no errors, but for some reason in the blocked-ip list at the top of the manage page its only showing around 1,000,000 blocked ip's. This number should be much larger. Im wondering if this is just a glitch with the mobloquer program?

Thanks!

---

### Post by nmxdaven on 2011-07-24
A little more info for you.

I was playing around with it a bit and it acts strange. I deactivated all list but one. I updated and refreshed and it showed 900,000 ip's blocked. I updated another with this (so now I have the original + 1 ) and the ip's blocked went down to 60,000) Then I unchecked the additional list I had just activated, and now have only the original (the one with 900,000) and update and restart. Now it shows 814,000 blocked. Not sure whats going on here.

---

### Post by jre on 2011-07-25
moblock merges the IP ranges if they overlap.
IIRC mobloquer shows the blocked IP ranges. So if you block the whole IPv4 internet (0.0.0.0-255.255.255.255) you will only block 1 range.

---

### Post by nmxdaven on 2011-07-25
> **jre said:**
> moblock merges the IP ranges if they overlap.
IIRC mobloquer shows the blocked IP ranges. So if you block the whole IPv4 internet (0.0.0.0-255.255.255.255) you will only block 1 range.

 awesome, thanks for that info. I was used to ipblock listing individual ip's.

---

