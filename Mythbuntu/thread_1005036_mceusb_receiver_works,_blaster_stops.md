---
title: "mceusb receiver works, blaster stops"
date: 2008-12-07
forum: Mythbuntu
---

### Post by JAKEOTR on 2008-12-07
Hello...I've been having this problem on and off for close to a year now. I installed Mythbuntu 7.10 last year and had problems setting up the mce remote blaster but finally got it working. The receiver always works, but the blaster will die for no apparent reason and I can never find anything in the logs. Had a good 8-9 month run with no problems after I set up a daily cron job to: shut down lirc, pull out the modules, re-install the modules, re-start lirc, and then restart gdm. This is the only way to get it working again and this daily ritual seemed to be enough to make it fly. Unfortunately, I did a kernel upgrade a few weeks back and started having the problems again. I couldn't get it fixed so I decided to install a new 8.10 version. Things are worse than ever. It stops several times a day, so I am not getting the channel changes I want and (dont know if its related, but started around the same time) my mce remote keeps dying, where I have to pull the batteries mash some buttons for a while, put them back in and its fine. I've been seaching for a year now and have not found anyone with my problem. Has anyone heard of this or have any ideas? I'll post whatever info you need on my system. Maybe its something unique to my hardware because some things just don't work like the howtos say...ie /etc/init.d/lirc restart will not work unless the frontend is restarted after, I've not heard of this happening to anyone else...please help!

---

### Post by JAKEOTR on 2008-12-08
bump

---

### Post by JAKEOTR on 2008-12-09
Anyone??

---

### Post by uMuppet on 2008-12-09
Have you tried alternative hardware?  At least one of those problems may be from hardware that is overdue for replacement.

Have you given your blaster a static event?  If not then after some boots it may be allocated a different event number.

I have a guide on my wiki to fix this but the free server I am using for my website keeps going down so I can't get to it right now.  Let me know if this fits your problem and I'll get back to you.

---

### Post by JAKEOTR on 2008-12-09
Thanks for the reply...I havent tried any thing different as far as blasters or receivers, everything I built the box out of earlier this year was new. I'm not sure what you mean by a static event, but if reloading the modules and restarting lirc brings it back to life then I wouldnt think it was changing its place. I would be interested in the wiki...I need to try anything at this point....WAF is tanking fast!

---

