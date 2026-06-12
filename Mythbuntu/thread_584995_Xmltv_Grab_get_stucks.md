---
title: "Xmltv Grab get stucks"
date: 2007-10-21
forum: Mythbuntu
---

### Post by kerwin007 on 2007-10-21
Hi all,

I installed mythbuntu based on gutsy (7.10) and i'm trying to setup xmltv to grab a tv guide. When mythtvfilldatabase runs, I can see in the terminal :

getting list of channels
grabbing channels

and then it gets stuck there forever. I tried to run the grab script manually as well, with the same results.

Any help will be highly appreciated :)

---

### Post by axelsvag on 2007-10-21
Which grabber did you choose?

---

### Post by kerwin007 on 2007-10-21
I don't have access to it right now but the script is something like tv_grab_ch_search

---

### Post by kerwin007 on 2007-10-22
ok apparently it's just that the script is insanely slow, mostly due to the website being slow.

So this raise the question, is there an alternative to xmltv ?

---

### Post by laga on 2007-10-22
> **kerwin007 said:**
> ok apparently it's just that the script is insanely slow, mostly due to the website being slow.

Slowness is normally not an issue because mythfilldatabase is usually run as a background task.

> 
So this raise the question, is there an alternative to xmltv ?

Maybe nxtvepg or tv_grab_eu_epgdata which I have written - you'll have to install XMLTV from CVS, request a test PIN at [email]service@epgdata.com[/email] and maybe bug me to add any missing channels ;). It's a commercial grabber so you'll likely have to start paying for the data in 2008. </shameless plug>

There's also the very new tv_grab_ch_cablecom which is reasonably fast (still takes a while to download the data, though): [http://www.dmesg.ch/wordpress/tv_grab_ch_cablecom/](http://www.dmesg.ch/wordpress/tv_grab_ch_cablecom/)

---

### Post by KCPokes on 2007-10-22
The other option is to pay for Schedules Direct, which is the pay service replacing Zap2It.  Paying for something that was previously free does bite, but knowing that it just works is a nice peace of mind that is worth the minimal money, to me at least.

---

### Post by laga on 2007-10-22
> The other option is to pay for Schedules Direct, which is the pay service replacing Zap2It. 

Only if you're located in North America. Since the OP decided to use tv_grab_**ch**_search it's likely that they are located in Switzerland :)

---

### Post by kerwin007 on 2007-10-23
Ok, thanks :)

and yes, I am in switzerland ...

---

