---
title: "dialup ppp0 does not appear in ifconfig"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by LancerNZ on 2012-05-27
I've set up a dialup modem by running pppconfig and answering all the questions. It works in that the modem dials out with the pon (provider) command. However, when it's online there is no ppp0 appearing in ifconfig. This needs to happen or certain scripts won't be able to successfully manipulate the network to assign gateways and other stuff.

How do I ensure that the ppp0 entry appears in ifconfig?

As a side note, I notive that ppp0 does appear when I use gnome-ppp. This is no good to me however because my scripts need to use console based apps (ideally the pon command which was working fine in my previous install before upgrade to 12.04)

---

