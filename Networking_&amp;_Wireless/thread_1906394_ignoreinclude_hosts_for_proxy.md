---
title: "ignore/include hosts for proxy"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2012-01-09
Hi,

The company I work for, let's call it 'xyz.com', has some hosts on the intranet and some on the internet, both in the same 'domain'.

EG, [www.xyz.com](www.xyz.com) is only available from the internet, and home.xyz.com is only available from the intranet.

To get to regular internet sites from the intranet, I use a proxy server. I have added '*.xyz.com' to the 'ignored hosts' tab in network manager. Unfortunately, this stops me from being able to get to [www.xyz.com](www.xyz.com) (and a few others).

Is there a way to add an 'exception' to the ignored hosts? I was hoping for something like :

+*.xyz.com
-www.xyz.com

or even some kind of reg-ex or bash-like syntax :

!(www).xyz.com

Max.

---

