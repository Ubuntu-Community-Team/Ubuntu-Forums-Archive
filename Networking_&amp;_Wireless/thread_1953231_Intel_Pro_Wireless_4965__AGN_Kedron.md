---
title: "Intel Pro Wireless 4965 / AGN Kedron"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by tlan on 2012-04-05
Had an issue with two laptops both IBM thinkpads and both running lucid.

Wireless stopped working around the same time, wired stopped working too,

Network Disabled and I could not enable. 

i checked the wireless switch to verify enabled
checked bios
sudo rfkill unblock all

what i found by mistake to fix the issue.

hit the Fn+hibernation key

then wake it out of hibernation and wireless and networking works,

and i believe this has something to do with the IBM disable wireless indefinite if not in use software switch that is present in the ibm windows thinkpad utility.

go figure,

---

