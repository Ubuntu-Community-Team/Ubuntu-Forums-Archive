---
title: "Something is using bandwith"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by thommyy on 2012-03-15
I have one really strange problem that i haven't till now. I have network widget on desktop, and it shows that something is downloading at 60-140 Kib/s. I installed NetHogs and it doesn't show network traffic at all or sometime something small(less than one KB/s), never before i had this problem. So question is: Is something wrong with nethogs or with widget? but light on my ethernet is constantly blinking so something is definitely using bandwidth. Should i just leave it like that or should i be concerned? (I'm using KDE)
Thanks for any help

---

### Post by miegiel on 2012-03-15
Keep in mind that you trafic in **bits** seems about 10 times higher (8 times + 20% overhead) than your trafic in **bytes**

If you want to try another monitoring program, try *nmon*. It's a comandline/terminal monitor, a bit like *top* but it also shows netwok and disk info (and more).

---

### Post by thommyy on 2012-03-15
Okay, i analyzed network traffic with wireshark. and i get lot of ARP packets, and with little serachin on google, i came to conclusion that it is broadcast storm. correct me if i'm wrong, so how to fix that?

---

### Post by miegiel on 2012-03-15
> **thommyy said:**
> Okay, i analyzed network traffic with wireshark. and i get lot of ARP packets, and with little serachin on google, i came to conclusion that it is broadcast storm. correct me if i'm wrong, so how to fix that?

Can't you see where (what machine) the packages are coming from? Since it's ethernet, is your switch connected to other switches? There could be a loop connecting 3 switches in a triangle, for example.

If you can change the thread title from "something is using bandwith" to "ARP broadcast storm is using bandwith" you might atrack an arp and/or broadcast storm expert. (I'm not :D)

---

