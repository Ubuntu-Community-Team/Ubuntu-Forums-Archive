---
title: "pptpd cannot connect to Internet"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by Jekshadow on 2009-10-14
I installed pptpd, configured it, and for some reason, it will not allow me to connect to the internet (however it will allow me to connect).

To make sure this was not a problem with my config, I installed it on a clean Debian system (well, apache was installed) and I have the same problem. All I did was enable ipv4 forwarding and add myself as a user, in addition to configuring DNS servers and IP ranges.

This is NOT a problem with the DNS server config. I cannot even connect to IP addresses (I tried Google's).

---

### Post by iarp on 2009-10-22
I'm having the same issue. Ubuntu Server 9.04. Tried connecting from my school and it connected fine and i was able to browse all computers on the internal home network but couldn't browse any websites or even stream radios from ip addresses.

Edit: I fixed my issue when i ran into the article below. I also found that commenting out the wims(or wins) server address and DNS server address also helped.

[http://ubuntuforums.org/showthread.php?t=882908](http://ubuntuforums.org/showthread.php?t=882908)

---

