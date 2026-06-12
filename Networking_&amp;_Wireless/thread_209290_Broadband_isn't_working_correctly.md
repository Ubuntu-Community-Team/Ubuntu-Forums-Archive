---
title: "Broadband isn't working correctly"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by takethepain on 2006-07-04
I have a little network going at home with a router (NetComm NB5PLUS4W ADSL2+ Modem Router) supplying the internet to three computers (2 macs and 1 pc), everything works fine under Windows XP and MacOS X but after installing ubuntu I discovered that the internet wasn't working correctly.  I can open up a browser and conect to my router through [http://192.168.1.1](http://192.168.1.1), but not much else.  A few web pages do load, albiet slowly,such as the online help pages for ununtu, [www.doomworld.com](www.doomworld.com) and my ISP's webpage but alot of sites will refuse to load, and eventually time out.  Whats going on?

---

### Post by takethepain on 2006-07-05
Well I think I solved most of the problems by disabling ipv6 however I still have lingering problems.  For example I can't use gaim to connect to my msn account (it just sits there)  and when I run sudo apt-get update, I get a lot of time-outs.

Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

So does anyone know whats going on?

---

### Post by mips on 2006-07-05
Where did you disable IPv6, Firefox only or globally ?

Drop the au. part in your sources file.

---

### Post by g00n on 2006-07-08
I've been harping on this problem for awhile.  I have disabled IPv6 everywhere i can find.. NO HELP.

it's a problem with the router's DNS server... instead of ignoring ipv6 dns queries it's replying with 1.0.0.0

I have fixed the aliases, i createed the 00local, i've created modprobe.conf... no joy.

I just remove my router from /etc/resolv.conf and go on with my day.

nobody has come up with an actual solution.

---

