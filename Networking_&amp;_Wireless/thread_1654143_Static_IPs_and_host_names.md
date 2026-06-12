---
title: "Static IPs and host names"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by WA1DH on 2010-12-27
I'm in the process of configuring static IPs for all PCs on my home network. I've run into an issue where the host name seems to be changed after setting the static IP. Instead of being able to resolve a remote PC with 'ssh machine' I now have to use 'ssh machine.local'. If I try to ping the machine from itself, it will work with just the host name (and no .local). Everything on each machine reads the correct host name, but if I try to access/ping from another PC, I must add .local to the host name.

This isn't a major issue, and I can live with it if I have to, but I would just like to know what changed when I went from DHCP to static IP. Is there any way to make it so I don't have to enter .local after the host name?

Thanks.

---

