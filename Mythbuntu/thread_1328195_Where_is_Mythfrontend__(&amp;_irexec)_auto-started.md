---
title: "Where is Mythfrontend  (&amp; irexec) auto-started??"
date: 2009-11-16
forum: Mythbuntu
---

### Post by SiHa on 2009-11-16
Hi,

Please bear with me.

I've been trying to get irexec to work properly with my new 9.10 setup (had it working fine in 8.04).

I appears that once you've used irexec once, it sets itself to auto-start. Problem is that it doesn't pick up the config from ~/.lirc/irexec. So I've tried adding to both /etc/rc.local and creating /etc/rc2.d/00irexec (at different times!). Both attempt to kill any existing irexec process and start the daemon again, but taking the above config. Neither seems to work.

After a bit more digging, it seems that the lirc init script will start irexec, but it points to the old location for the config (/etc/lirc/lircrc). So I removed the rc.local and rc2.d entries, and put a copy of ~/.lirc/irexec here. Now I get two instances of irexec started by root, I assume that these are both from the lirc init, and one started by 'frontend'. The two root copies are taking their configuation from the correct location, but the frontend one isn't. 

So I've had to resort to a nasty kludge of editing the mytfrontend startup script and added:```
sudo killall -9 irexec
sleep 1
irexec -d /home/frontend/.lirc/irexec
```
...and edited my sudoers to allow frontend to kill the two root processes.

This seems to work, but its a hell of a bodge, and once, yesterday I got two frontends started simultaneously by irexec. I imagine it's a result of multiple irexec's.

So, to finally get to the point. I'd like to find out where the 'frontend' user is  starting irexec, so I can simply modify the call to specify a path to the configuration file.

Anyone care to take a stab?

TIA,

Simon

---

### Post by Neon Dusk on 2009-11-16
Not sure if this will help but on a clean install of 9.10 I didn't need to anything to get irexec work.

I just put the keymappings for irexec within the .lirc\mythtv file

---

### Post by SiHa on 2009-11-16
Interesting.
In that case, perhaps I should remove my meddling, revert back to the original and see what happens.

Thanks.

---

