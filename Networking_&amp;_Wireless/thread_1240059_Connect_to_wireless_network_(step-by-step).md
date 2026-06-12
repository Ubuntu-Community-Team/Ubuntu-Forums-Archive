---
title: "Connect to wireless network (step-by-step)"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Dhekke on 2009-08-14
I'm having some troubles connecting to my University's wireless network and after a bunch of research, I'm starting to think the problem is with Network Manager...

I'm fairly new to linux so if anyone could provide me a step-by-step guide to set wpa_supplicant.conf (for some reason, mine is totally empty) and connect to a wireless network from the command line (with a verbose log, preferably), I'd very much appreciate it...

I'm at the university right now (using the lab's computer) so I can't download wicd to my notebook... I have wpa_gui installed, but it doesn't work...

Thanks a lot!

Edit for some info:
Ubuntu 9.04
Dell Inspiron  1545
Wireless works just fine at home

---

### Post by AmerNewbieInDE on 2009-08-14
first of all there is more information needed .. what card are you using... i have intell 5100 and used :

sudo modprobe -r iwlagn

sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

when i had my network security correct i had no trouble conecting...

Only problem i had was having to keep applying that everyrestart, then i upgraded the kernel. then no more problem

---

### Post by Dhekke on 2009-08-14
Thanks for the reply.
I friend of mine helped me out with the commands... It works great now (specially with wicd installed)

---

### Post by rob22941 on 2009-10-05
I am having the same problem, I am also new to linux. I use my laptop with Ubuntu 9.04 on my home network but I can't get on wireless at my university either. Please Help!

---

