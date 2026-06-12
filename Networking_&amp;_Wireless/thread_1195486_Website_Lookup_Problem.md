---
title: "Website Lookup Problem"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by Crimex on 2009-06-23
Using Ubuntu 8.04, whether wireless or wired, the "looking up" of a website in the web browser takes a while to complete. Once connected, the speed is normal.

I also use Ubuntu as a host OS for Windows XP (Virtualbox). However, the website lookup and browsing in Windows XP guest is completely normal.

WHat can be causing the problem?

---

### Post by utnubuuser on 2009-06-24
I've seen posts about disabling ipv6 in firefox through > about:configin the url bar, then find and disable ipv6 by typing ipv6 in the filter and double-clicking on the ipv6 setting.

If you google this, you'll find several threads related to slow browsing issues.

---

### Post by Crimex on 2009-06-24
Thank you utnubuuser for responding.
I tried your suggestion but the issue still exists. The issue occurs in both Firefox and Opera.

---

### Post by Crimex on 2009-06-24
After doing more searching I fixed the problem.

I went to System > Administration > Netowrk > DNS Tab and deleted my (Wireless) Router's IP from the DNS section and left the modem's IP address there.

---

