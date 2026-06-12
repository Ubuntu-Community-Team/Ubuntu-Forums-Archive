---
title: "Intermittent connectivity via router"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2013-07-04
Hi,
I've got a Netgear router providing wireless and wired connectivity to the Internet. I also use it to move files back and forth between my laptop and desktop computers (both running 12.04). I've got no problems accessing the Internet from either network (wired or wireless) and I SOMETIMES have connectivity between the two networks. However, there are also times when I can't access my desktop from my laptop (using ping or scp etc.) and vice versa. And there are also times when I can ping one way, but not the other. I can ping the router (10.0.0.1) at all times.
And the most weird part of it is that I can lose or gain connectivity within one session - without any reboots or networking restarts!
And ideas?
David

---

### Post by Cheesehead on 2013-07-04
The problem you describe smells like an intermittent hardware fault rather than a software issue.
When possible, try replacing one component at a time until the problem goes away.
Components include wireless cards, ethernet cards/ports, network cables, and routers.

I suggest starting with the router. They do fail.

---

### Post by dbclinton on 2013-07-04
Darn. I was afraid of that. And I was just getting to like my router... :)
Thanks,
David

---

### Post by Gfurst on 2013-07-05
Hey, i was having similar problems, but I had no internet connectivity, wifi would try to connect but couldn't resolve ip.
Setting router to a single encryption method and to disable DNS relay worked fine for Wifi.

However, my wired connection would work for a while, about half a minute of accessing internet and router, after that couldn't access it at all.
Haven't tried it after I got the Wifi working, but Wifi and wired configs shouldn't interfere on the router.

Now this problem interest me because I'm having problems transferring files between lan, tried wired and wifi with both Ubuntu machines:
[http://ubuntuforums.org/showthread.php?t=2159894](http://ubuntuforums.org/showthread.php?t=2159894) (link for my thread)
Faulty hardware, on my case, is unlikely but possible. Still i would like to know if this is solved for you.

---

### Post by dbclinton on 2013-07-05
Hi,
I don't think that I can disable DNS relay on my Netgear WNR2000 - and a bit of forum searching suggest that I'm not the first person to wonder why...
Lowering the encryption didn't seem to have much effect in my case either.
Could be it's just time for a new router.
Thanks,

---

