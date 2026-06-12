---
title: "I think I crashed my apache2"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by abernut on 2010-02-17
I have a machine running Ubuntu 8.04.

Yesterday I tried adding virtual subdomains, today I removed them after installing VirtualBox.

Now I cant browse any localhost site from the server, Network Timeout.  What's weird is I can still hit them from another machine on the network.

Here are the last few lines of my apache2 error log.

[Wed Feb 17 10:31:21 2010] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:443
[Wed Feb 17 10:31:21 2010] [notice] caught SIGWINCH, shutting down gracefully
[Wed Feb 17 10:31:32 2010] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Wed Feb 17 10:31:32 2010] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Feb 17 10:39:17 2010] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:443
[Wed Feb 17 10:39:18 2010] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:443



My /etc/hosts

127.0.0.1       localhost.localdomain    localhost
172.28.159.15   server.name.com  severname
# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts

---

