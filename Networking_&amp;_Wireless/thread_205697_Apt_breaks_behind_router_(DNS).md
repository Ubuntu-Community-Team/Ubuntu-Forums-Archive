---
title: "Apt breaks behind router (DNS?)"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by krs1ars on 2006-06-28
I've been having some trouble with this, searched all around and found out this was somehow related to DNS configurations but never found a solution.

In my general setup, I have a router connected to the internet, and my Ubuntu box behind that. The router is pointed at my isp's DNS servers, and my Ubuntu box is directed to the router as a DNS server (problem still occurs if I point Ubuntu to the ISP servers for DNS). 

Generally, I can access the internet without a problem, firefox, gaim, ... all work fine. But apt, for some reason, always responds "connection failed" when attempting to update. I can ping the servers just fine, resolve the ips, and I can browse there with firefox.

Additionally, when I connect Ubuntu directly to the internet, apt works fine.

Any ideas?

---

### Post by krs1ars on 2006-06-28
If this is any help, here's the console output from an apt-get update:
(Synaptic just says "Could not download all repository indexes")

```

Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Ign http://us.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security Release
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://us.archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Ign http://us.archive.ubuntu.com dapper/universe Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://us.archive.ubuntu.com dapper/universe Sources
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/main Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://us.archive.ubuntu.com dapper-backports/universe Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://us.archive.ubuntu.com dapper-backports/main Sources
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/universe Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://us.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Err http://us.archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Err http://us.archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  Connection failed [IP: 146.137.96.15 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by falcon15500 on 2006-06-28
You got any firewalls running?  Have you put any rules into IPTABLES?  That's all I can think of, because if firefox can get to the same ip/port that apt-get it trying to use - then the problem is something specific to apt.  No apt config problems I can think of.  Leaves me with firewalls?

From a command prompt, try the following and post the results:  

```
sudo iptables -L
```

falc

---

### Post by krs1ars on 2006-06-28
Nope, no firewall on either. Even if there was, the fact that firefox can get to the same server, same port would rule out anything like that. Makes me think its apt specific, but I dont know how or if apt acceses the internet differently from FF (different DNS usage? I really have no idea)

---

### Post by falcon15500 on 2006-06-28
It doesn't seem to be DNS related, as you say when behind the router it doesn't work regardless of if you use the router to forward DNS, or if you use your ISPs DNS directly - whereas if you are directly connected to the net, it works fine.  Router, router, router... <shrug> Strange!

Got another router you could borrow/try?

falc

---

### Post by krs1ars on 2006-06-29
Solution:
For me, it was to clear the line "Acquire::http::Proxy "false"; from /etc/apt/apt.conf file.

---

