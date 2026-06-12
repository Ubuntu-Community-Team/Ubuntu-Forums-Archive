---
title: "Help! Strange network problem in Karmic!"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by craptree on 2010-03-08
I have a very strange problem!

If I boot up as usual, the network connects, via dhcp in networkmanager, as usual. All seems ok, and entries look correct in ifconfig. When I try to access anything over the network, eg ping a local address, or access the internet, I cannot!

What is strange is that if I boot into recovery menu root, and then load gdm, I am able to access the network fine!

So what am I not loading up/loading differently when I boot to recovery root and then loading gdm manually?

This problem started when I added an fdi file with regards to a fn laptop key. Removing the fdi file has not helped, and I have updated the fdi-cache since. This could be related.

I have tried this on a few different kernels too, all of which exhibit the problem. Currently using 2.6.32-16 Lucid backport, but have tried it on kernels I know for sure worked before.

Many thanks!

**edit** Formatted the computer in the end, and have began re-installation. Thanks for reading :)

---

### Post by Iowan on 2010-03-08
Have you checked **route -n** and contents of */etc/resolv.conf*?

---

### Post by craptree on 2010-03-09
mmmhmmm. The routes and dns settings were all fine.

I got really impatient in the end, and have just formatted the computer! Now the process of returning all the customisations I had. LONG!

Many thanks for your reply :)
Riz

---

