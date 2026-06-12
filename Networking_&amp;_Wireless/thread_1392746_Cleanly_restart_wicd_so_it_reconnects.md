---
title: "Cleanly restart wicd so it reconnects"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by misha680 on 2010-01-28
Dear all:

I seem to be having "disconnects" from my wireless network where I stay connected but am unable to ping any hosts,
including my router.

I would like to make a simple cron script that checks for this and reconnects.

Is there a clean way to tell wicd to reconnect?

How about sudo /etc/init.d/wicd restart?

I am on Ubuntu 8.04 amd64

misha@misha-d630:~$ dpkg -l | grep wicd
ii  wicd                                       1.6.2.2-1                                                  wired and wireless network manager
misha@misha-d630:~$ 

Any help appreciated

Thank you!

Misha

---

### Post by llawwehttam on 2010-01-28
Have a look at the wireless disconnecting link in my sig. It worked for me.

---

### Post by wildmanne39 on 2012-08-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

