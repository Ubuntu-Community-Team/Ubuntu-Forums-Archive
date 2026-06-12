---
title: "How to stop backend starting up?"
date: 2011-07-02
forum: Mythbuntu
---

### Post by ceejay on 2011-07-02
This ought to be really simple and I'm very puzzled ....

I am trying to set up a config where I have separate front end and backend machines. Both are running Myth 0.24 on Ubuntu 11.04. It is mostly working - I can watch TV on the front end using the tuner in the backend.

However, when I installed mythtv on the frontend machine it was as a combined frontend/backend so both parts are installed. I subsequently moved my tuner to the backend machine, and changed the front-end config to point to the new backend, which works.

My problem is that mythtv-backend is still being started up on what is now meant to be a front-end only machine, and I want to stop it from being started - but can't find where it is being started.

I can manually stop the backend (and the frontend works fine) but I definitely do not want to waste start-up time by starting and then stopping the backend!

I looked in /etc/init.d and found an entry for mythtv-backend ... deleted it, restarted, and the backend starts up anyway! I have looked in /etc/rc*.d and can't find anything there. I have looked in Ubuntu Control Center - Startup Applications, nothing there either.

I guess I could uninstall the backend but I would rather keep it there in case I want to change the config again in the future.

Can someone please point me towards where this thing is being started?

TIA

---

### Post by ian dobson on 2011-07-02
Hi,

If your running 11.04 and maybe 10.10 have a look at /etc/init they use upstart to start processes.

Regards
Ian Dobson

---

### Post by ceejay on 2011-07-02
Thanks! There was indeed an entry in /etc/init, I moved that away and it is now not starting.

It's easy when you know how!

Ceejay

---

