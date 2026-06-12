---
title: "lokkit broke my networking"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by eyephisc on 2006-07-15
Hi, I am running Dapper Drake and I had it working great until I installed the lokkit firewall.  Even though I selected the low security option, my wireless connection to the internet stopped working after rebooting.  I could no longer access any web pages.  So I tried running lokkit again and telling it that I wanted to disable the firewall.  This didn't fix the problem.  So I completely removed lokkit, purging the configuration files.  Still, no internet.

So I installed firestarter, hoping that it could configure iptables so that they work again.  This does fix the problem, but it requires that I start firestarter manually each time I start the computer after I connect to the wireless network (via NetworkManager).

Can anyone help me troubleshoot how lokkit permanently broke my iptables at startup, even after I removed the lokkit program?

Thanks for any guidance!

---

