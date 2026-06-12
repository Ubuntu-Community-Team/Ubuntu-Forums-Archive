---
title: "Configuring NetworkManager to use IPv4 for DNS"
date: 2006-02-05
forum: Networking &amp; Wireless
---

### Post by draggett on 2006-02-05
Like many others I am having problems with apt-get and DNS since my ADSL box doesn't support IPv6. A tedious work around is to ping each of the repositories before running apt-get. If I forget, I see sites appearing with an IP address of 1.0.0.0 due to a botched attempt to resolve the host name as an IPv6 address. Once that happens, you have to wait for ages before the cached IP address is discarded.

A potential solution is to run bind9 and to use the -4 option for named, with all name look ups routed via 127.0.0.1. My problem is how to set this up. I've tried OPTIONS="-4" in /etc/init.d/bind9 but this isn't working. If I grep the output of ps for named, I see:

bind      8193     1  0 18:14 ?        00:00:00 /usr/sbin/named -u bind
bind      8235  7697  0 18:14 ?        00:00:00 /usr/sbin/named -f -u bind -c /var/lib/NetworkManager/NetworkManager-named.conf

that is, the -4 option isn't reaching named. Note that I am also using the very cool NetworkManager which makes it easy to pick wireless networks when you aren't plugged into the wired LAN.  NetworkManager automatically configures bind to forward DNS requests to the remote name server it has identified via DHCP. There must be a way to persuade it to add the -4 option to named so that forwarded requests are always for IPv4 addresses. I don't know why named is being run twice. However, the botched lookups occur if when you don't have NetworkManager installed. I skimmed the bind configuration reference manual but couldn't find how to set the equivalent of the -4 option on named.

Any ideas?

---

### Post by toorima on 2006-02-10
Don't know if you have solved your problem but I had same problem and this did it for me [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4)

---

