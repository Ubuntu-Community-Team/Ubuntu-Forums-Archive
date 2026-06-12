---
title: "lockd: server xxx not responding... help!"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by mrtorture on 2008-12-12
I'm trying to set-up an Ubuntu 8.10 client machine to use remote home directories trough NFS in a central server, but when the user get logged, the system can't load the profile, jamming in a "blank" screen. On messages log, this one appears:

client-test-machine kernel: [  129.628031] lockd: server xxx.xxx.xxx.xxx not responding, still trying

The NFS mount is ok, the homedirs are visible and accessible if a local machine profile (administrator) is loaded, also the ldap client config is working, but this lockd stuff is really weird.

I've another machine set-up with Ubuntu 8.04 and it works normally, load the profile config and works fine... But I need upgrade to 8.10 for some software tests that aren't working fine on 8.04.

Anyone could help me? 
Thanks!

---

