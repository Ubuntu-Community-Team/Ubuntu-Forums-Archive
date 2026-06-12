---
title: "Accessing Apache Server Through Emulator with subdomains"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2009-09-30
Hey everyone,

I do quite a bit of web development and set up my local copies of my sites as subdomains i.e. SiteName.localhost. Now I know to access this in an emulator you can use localhost, so you would use the inet address (In my case 192.168.1.9) Now this lets me look at the top site of my /etc/hosts/ file but I can't work out how to get at my other subdomains. Does anyone have any ideas of how to do it? If it even possible?

My /etc/hosts file is:

```
127.0.0.1	localhost
127.0.0.1	drop.localhost
127.0.0.1	gauntface.localhost
127.0.0.1	wheretodo.localhost
127.0.1.1	matt-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Any help would be great, and if it can't be done just say cos I'm not overly bothered, it would just mean everything will have to been done live on a web server which is just a hassle.

Many Thanks,
Matt

---

