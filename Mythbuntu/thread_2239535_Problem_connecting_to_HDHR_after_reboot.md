---
title: "Problem connecting to HDHR after reboot"
date: 2014-08-14
forum: Mythbuntu
---

### Post by lordviperz on 2014-08-14
I have finished building my new system and have one small problem left to solve. The problem is with my hdhomerun dual and connecting to it after a reboot. I have the hdhr connected directly to a second nic in my master/frontend. There is no dhcp for this nic and it is set for local connections only. If I need to reboot the system for any reason I always have to restart the backend service after the reboot so it will connect to the hdhr. If I don't restart the backend the network led on the hdhr just flashes and I cannot access it either from the frontend or from the mythbuntu desktop. Once I restart the backend the hdhr led stays solid and all connections work.

I'm using the old style hdhr dual, the white box with 2 cable connections for the tuners. The nic for the direct connection is an old linksys 10/100/1000. 

I did purchase this hdhr used and I just had a thought. Is it possible it is still holding the IP from the original owner's dhcp? I did upgrade the unit with the latest firmware. Is there a way to factory reset the unit to clear any IP it may have received?

---

### Post by lordviperz on 2014-08-22
Does anyone have any ideas?

---

### Post by uteck on 2014-08-24
I would hazard a guess that the Mythtv-backend is getting started before your 2nd nic sorts out its connection so it does not see it.

You could put a restart command in /etc/rc.local for the backend.  rc.local gets run last when the system starts, so if you put in something like this before the "exit 0" line;
sleep 20 ; service mythtv-backend restart &

It will wait 20 seconds, just to be sure that all services are up, then restart the mythtv-backend.

---

### Post by lordviperz on 2014-08-25
> **uteck said:**
> I would hazard a guess that the Mythtv-backend is getting started before your 2nd nic sorts out its connection so it does not see it.

You could put a restart command in /etc/rc.local for the backend.  rc.local gets run last when the system starts, so if you put in something like this before the "exit 0" line;
sleep 20 ; service mythtv-backend restart &

It will wait 20 seconds, just to be sure that all services are up, then restart the mythtv-backend.

Thanks, I will give that a try.

---

