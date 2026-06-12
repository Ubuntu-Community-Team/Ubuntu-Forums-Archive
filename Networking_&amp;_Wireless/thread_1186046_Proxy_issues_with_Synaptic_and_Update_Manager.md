---
title: "Proxy issues with Synaptic and Update Manager"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by Brodie337 on 2009-06-12
Hi all.

Ive been using these forums quite a bit, as I'm relatively new to Linux, but this is the fist time I've had to post.

I'm using Ubuntu 8.10 Netbook Rmix on my Eee 1000H at university and at home. The university internet connection is through a proxy whereas the home connection is not.

I had my Eee set up so that Synaptic and the Update manager were working through th proxy, but when I get home, despite setting the proxy to "Direct connection" in bith synaptic and using the tool under the preferences menu, I cannot use Synaptic or the Update. Both return an error like this:

```
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/p/pm-utils/pm-utils_1.1.2.4-1ubuntu8.1_all.deb
  407 Proxy Authentication Required [IP: xxx.xxx.xxx.xxx xxxx]

```IP has been blanked out.

It seems that while I can set a proxy server, it cannot be "unset"

Can anyone help?

Brodie.

---

### Post by Brodie337 on 2009-06-13
No takers?

---

### Post by Brodie337 on 2009-06-13
I found it... The global proxy setting under preferences dosent change the setting in /etc/environment

Just delete the proxy line in there

---

