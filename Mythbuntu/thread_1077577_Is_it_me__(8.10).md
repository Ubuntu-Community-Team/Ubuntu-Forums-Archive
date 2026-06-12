---
title: "Is it me?  (8.10)"
date: 2009-02-22
forum: Mythbuntu
---

### Post by NTBlade on 2009-02-22
Or is this the most broken distro ever?

Yet again I try to setup a backend with diskless frontend and fail.  Now I have a system that takes more than 10 mins just to reboot!:(

Hardware for backend:
HP Proliant ML115 (Opteron + 1GB RAM) 250G Drive

Install 8.10
Setup static IP address (a bit of a joke really)
Updates:  Hmmm install and reboot.
Install  midnight commander (mc)  What's this? aptitude removes a load of stuff (kernel related?) before it installs mc?  WTF?

Rebooting takes an eternity with NTPD / NFS throwing errors

Forget the fact that diskless / DHCP doesn't work out of the box.  Is there no documented solution for this?

Sorry to rant (again) but enough's enough!

Can anyone help please?
Noz

---

### Post by blackoper on 2009-02-22
I had almost no problems setting up diskless clients/frontends with 8.04. I do however use a dd-wrt router that has a built in option for pxe boot so I don't have to setup anything but the boot image on the server. Server boot time was about a minute (lots of hard drives), frontend boot time was probably about 90 seconds.
The option in dd-wrt for this is from this post/thread: [http://ubuntuforums.org/showpost.php?p=5867713&postcount=214]("http://ubuntuforums.org/showpost.php?p=5867713&postcount=214")

It's definitely easier to use dd-wrt than setup anything special for pxe boot on the server/ip's etc. I bought a linksys 150n for the purpose

---

### Post by NTBlade on 2009-02-23
Thanks for the reply.
I'm tthinking that I might just downgrade for the time being and run without any tuners until the diskless problems are sorted out or 9.10 arrives (hopefully the fixes will be in).  I might even go for wee router with dd-wrt on it.

NTB

---

