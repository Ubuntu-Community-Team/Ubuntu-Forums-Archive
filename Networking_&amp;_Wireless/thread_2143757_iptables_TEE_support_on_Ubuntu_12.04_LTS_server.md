---
title: "iptables TEE support on Ubuntu 12.04 LTS server?"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by x0ne on 2013-05-10
I have a Ubuntu machine functioning as a simple router and wanted to duplicate traffic I had coming into eth1 and forward a copy on to eth0 without impacting the actual routing. Searching online took me to the "TEE" option which is not built-in to the default iptables packages in Ubuntu. Instead I was directed to install xtables-addons, but as I watch the compilation, I see no xt_tee module installed. In fact, it appears it may have been dropped off the main package. 

If TEE is not available, is there another way to duplicate traffic on an interface? I need to keep a low overhead to avoid exhausting the machine and want to avoid packet loss as much as possible. I am using iptables 1.4.12, kernel 3.2.0-41-generic and xtables-addons 1.41-2ubuntu0.1.

---

