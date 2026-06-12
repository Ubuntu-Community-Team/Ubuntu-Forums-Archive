---
title: "How Does MythBackend Autostart at Boot on MythBuntu?"
date: 2016-04-28
forum: Mythbuntu
---

### Post by mattlach on 2016-04-28
Hey all,

I recently migrated my 14.04/0.27 mythbuntu dedicated backend install over to new hardware by cloning the install drive.

Everything seems to work perfectly, except, mythbackend no longer starts at boot time (which is odd).  Every time the server restarts, I have to manually go in and start the backend.

In order for me to troubleshoot this I feel like I need to understand how it is supposed to work.

It doesn't appear as if the mythbackend is set up like a service.

So, when my 14.04/0.27 backend was starting up properly on boot, how was it doing it so I can troubleshoot what went wrong?

Much obliged,
Matt

---

### Post by blm-ubunet on 2016-04-28
AFAIK it uses upstart, that's what I use..

[https://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](https://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
sudo initctl [start|stop|restart] mythtv-backend

I think mythbuntu 16.04 moves/transitions to systemd.

---

### Post by mattlach on 2016-04-29
> **blm-ubunet said:**
> AFAIK it uses upstart, that's what I use..

[https://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](https://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
sudo initctl [start|stop|restart] mythtv-backend

I think mythbuntu 16.04 moves/transitions to systemd.

Hmm.

Interesting.   I had assumed it did not do this, because in the general settings in the mythbackend configuration the "backend start command" is just listed as "mythbackend"  and the backend shutdown command as "killall mythbackend" (I believe, can't look right now, but its' something like that)

If it used a service like the above, I would have expected it to look something like "service mythbackend start" and "service mythbackend stop" or something like that.

I'll definitely take a look at this though.   I just used whatever method the installer on the 14.04 ISO did out of the box, so I never had to look into it before.

---

### Post by blm-ubunet on 2016-04-29
How's the BE meant to start if it does not use init/upstart or systemd?

Most settings in mythtv-setup are stored in the dB, can be accessed only after finding dB credentials in config.xml file(s) & connecting to mysql server.

The setting "Startup Command" in mythtv-setup is for **additional** command/script to run after the backend is launched.
I would guess bad things will happen if you have "mythbackend" there!

The settings backend stop & start are for use by "mythtv-setup" to be able to stop & restart the BE if you require, these have nothing to do with BE service starting.
For 14.04 & upstart I would delete the backend start cmd &/or use:
sudo initctl start mythtv-backend

---

