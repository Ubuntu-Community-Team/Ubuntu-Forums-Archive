---
title: "How to keep /etc/resolv.conf static"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-04-22
How can I keep /etc/resolv.conf static ... as in preventing it from being changed by the network manager ... without actually disabling the network manager (so wireless users can get their wireless setup that includes IP address, but leave the resolver configuration as is)?

---

### Post by alexfish on 2010-04-22
don't think you can keep /etc/resolv.conf static

this file is use by the network manager, a sort of working file, so therefore will change depending on the type of connection you are using and most obvious is the named servers NS1 and NS2 as these can change depending on the type of connection , although you can set the Network Manager connections to use address only, also  each type of connection may have it's  own resolv.conf IE . on my system there is also a etc/ppp/resolv.conf 

there is a prog called resolvconf don't know if this will help on what you are trying to achieve

regards

alexfish

---

