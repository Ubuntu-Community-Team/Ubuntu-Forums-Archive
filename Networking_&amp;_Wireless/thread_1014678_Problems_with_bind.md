---
title: "Problems with bind"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by macros_the_black on 2008-12-18
Morning Everyone

I am having a problem setting up bind9, first of all I have done something really stupid and deleted everything in the /etc/bind9/ directory thinking that when I install it again it would put everything back fresh well that didn't happen, so now when I try to start bind9 I get the following message in my console

# /etc/init.d/bind9 start
 * Starting domain name service... bind                                  [fail]

and in /var/log/syslog

Dec 18 07:56:19 kubuntu named[21784]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Dec 18 07:56:19 kubuntu named[21784]: found 1 CPU, using 1 worker thread
Dec 18 07:56:19 kubuntu named[21784]: loading configuration from '/etc/bind/named.conf'
Dec 18 07:56:19 kubuntu named[21784]: /etc/bind/named.conf:7: change directory to '/var/named' failed: file not found
Dec 18 07:56:19 kubuntu named[21784]: /etc/bind/named.conf:7: parsing failed
Dec 18 07:56:19 kubuntu named[21784]: loading configuration: file not found
Dec 18 07:56:19 kubuntu named[21784]: exiting (due to fatal error)

please be aware that bind is chrooted, and I have uninstalled app armour thats what was causing the problem I was trying to fix in the first place, if someone can help and save some of my remaining hair I would appreciate it /var/named does exist I have checked and so does /etc/bind/named.conf

---

