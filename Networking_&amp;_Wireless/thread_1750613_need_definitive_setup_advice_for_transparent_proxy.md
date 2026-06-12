---
title: "need definitive setup advice for transparent proxy with squid3 and 10.04"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by wideyes on 2011-05-05
Wow. what a task it's been trying to set up a transparent proxy server with Squid3 on Ubuntu 10.04! I've followed every guide I've found (most of them seem to be permutations of one specific guide which I cannot get to work - [http://www.ubuntugeek.com/setting-up-ubuntu-10-04-lucid-server-with-squid-3-as-a-transparent-proxy.html](http://www.ubuntugeek.com/setting-up-ubuntu-10-04-lucid-server-with-squid-3-as-a-transparent-proxy.html)) with no success. I've seen so many different squid.confs and iptables routing schemes, and I just can't get it to align.

I beseech somebody to suggest configuration entries for squid.conf and iptables that will get this combination up and running. From my searches on this forum, it just seems to be a very tricky beast to set up. I wish squid (and especially squid3) had better documentation.

I have a very standard setup: eth0 goes to my internet gateway, eth1 goes to my internal network, and I want clients on the internal network to have a transparent proxy through which their requests pass so I can apply content filtering with squidGuard.

Any suggestions will be tried and greatly appreciated!

---

