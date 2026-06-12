---
title: "No wireless after upgrading"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by Fibonacci on 2011-06-20
Hello.

I've got a Broadcom 4311 wireless card on my laptop, which has worked relatively smoothly for me ever since I installed Ubuntu (Karmic).
After upgrading to Natty it simply doesn't work anymore.
I've tried, as suggested somewhere, to purge every package with b43 or broadcom on its descrpcion, and then reinstalling bcmwl-kernel-source. I've also tried removing all other packages and installing the STA driver via Jockey.
In both cases NetworkManager won't even have a section for wireless connections, as if I had no wireless card at all.

I'm all out of ideas.

---

### Post by zander1013 on 2011-06-20
> **Fibonacci said:**
> Hello.

I've got a Broadcom 4311 wireless card on my laptop, which has worked relatively smoothly for me ever since I installed Ubuntu (Karmic).
After upgrading to Natty it simply doesn't work anymore.
I've tried, as suggested somewhere, to purge every package with b43 or broadcom on its descrpcion, and then reinstalling bcmwl-kernel-source. I've also tried removing all other packages and installing the STA driver via Jockey.
In both cases NetworkManager won't even have a section for wireless connections, as if I had no wireless card at all.

I'm all out of ideas.

i am facing the exact same problem. and i have tried many of the same solutions without success.

most recently i have recompiled the sta driver and installed it on my system. 

the output from iwconfig is now...

lauren@jadeakins:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lauren@jadeakins:~$ 


please advise.

---

### Post by zander1013 on 2011-06-20
hi,

i found a solution that worked for me here...
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

i removed the sta driver and then deployed Alternate Solution 2 given in the link. i do hope it works for you.
:popcorn::KS

---

### Post by Fibonacci on 2011-06-21
> **zander1013 said:**
> hi,

i found a solution that worked for me here...
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

i removed the sta driver and then deployed Alternate Solution 2 given in the link. i do hope it works for you.
:popcorn::KS

This did it. Thank you!

---

