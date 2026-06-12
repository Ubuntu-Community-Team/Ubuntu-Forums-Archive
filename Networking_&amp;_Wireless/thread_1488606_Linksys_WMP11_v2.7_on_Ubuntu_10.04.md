---
title: "Linksys WMP11 v2.7 on Ubuntu 10.04"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by xaxtree on 2010-05-20
Alright well I've read just about every topic related to this PCI card and anytopic that was related to the errors this card has given me, so far I have found no solution.  Currently I'm not on my Ubuntu PC but here is what is going on so far.

I spent about an entire day figuring out what to do correctly to install the drivers for this card to work.  I've tried b43legacy and ndiswrapper with no luck.  After installing b43-fwcutter in terminal I would enter lshw -C network, everything looked fine other then under wireless it would either show *network DISABLED or network UNCLAIMED.  I cannot figure it out, I've tried manually installing packages, and even using a wired connection and using sudo apt-get b43-fwcutter after I would sudo update, b43-fwcutter would install just fine but I still could not connect to the internet, hopefully someone can help me?

---

