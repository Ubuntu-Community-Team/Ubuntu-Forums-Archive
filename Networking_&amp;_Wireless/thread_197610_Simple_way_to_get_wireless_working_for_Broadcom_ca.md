---
title: "Simple way to get wireless working for Broadcom cards"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by Serenader on 2006-06-16
I am sorry if this has been posted before, but I felt I spent quite some time searching the internet to get my wireless working. I thought this might help others and save a bunch of time.

Here is what I did to get my Broadcom wireless card working.

1. Install wifi-radar using Synaptic Package Manager.
2. #sudo echo "blacklist hostap_cs" >> /etc/modprobe.d/blacklist
3. Run wifi-radar from Applications->Internet.

Thats it.

Before doing this, I tried all other means such as using ndiswrapper, fwcutter etc... There was some problem or the other with everything else (Just my experience). 

Hope this helps a few people.

---

