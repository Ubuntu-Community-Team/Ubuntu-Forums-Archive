---
title: "Crazy DNS problem"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by omniwired on 2010-09-05
Hello everyone.

I been having this random dns problem, in Ubuntu 10.04 and in 10.10 it started about 2 weeks ago after (I believe) an update.

Basically when I go to a website randomly I get that the website I'm visiting is not available ("Oops! Google Chrome could not connect to ..." & "This webpage is not available.").

I tested with Chromium "7.0.515.0 (58587)" and Firefox minefield (4.0ish) and 3.6.9.

I did these 4 things already:

/etc/default/grub
GRUB_CMDLINE_LINUX="ipv6.disable=1"

and this:


/etc/sysctl.conf
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

*disabling Chromium DNS pre-fetching 

*using Google and OpenDNS servers.

But didn't improve, also no other computers in my network have the same problem. All computer wired to the same router.

I'm a software engineer that run out of ideas, please help me.

Thanks in  advance.

---

