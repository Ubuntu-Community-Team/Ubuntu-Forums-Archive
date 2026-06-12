---
title: "wireless problems loading some webpages with new kernel"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by darmok47 on 2010-01-06
hi, 

i have ubuntu 9.10 32 bit

i have discovered 3 days ago that i have problems with my wireless connection.

here the problem

with wired connection no problem, but with wireless i can't load some webpages, expecially webmail(gmail. hotmail...) and wikipedia, instead of other sites that i can load very fast (like [www.lcarscom.net](www.lcarscom.net))

the browser say "waiting for www.sitename.com/........." and... nothing.

either with firefox and konqueror.

I dont know if the problem is correlated with some upgrade that i have made one week ago (that of course i dont remember what packages have been upgraded), but with the old kernels (2.6.28-16 and olders) everything works fine (and also with winxp in the same laptop)

with the new kernels (2.6.31-14 and 2.6.31-16) i have this problem.

my wireless card is 
02:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
my laptop is a toshiba satellite A100-508

and the module used is ath5k (also for the old kernel)

now my questions 
what is the cause?
can the problem be solved?
if is only a config problem, how i can copy/transfer config parameters/files from the old kernel to the new?

p.s. in the working kernel mouse trackpad doesn't work, it is the same problem?

Thank's for help

Darmok47

---

### Post by darmok47 on 2010-01-06
Hi,
problem solved!

i have just reinstalled old madwifi modules following this guide

[http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/)

and after in etc/modprobe.d/blacklist.conf i have blacklisted ath5k, but for me work also without this!

---

