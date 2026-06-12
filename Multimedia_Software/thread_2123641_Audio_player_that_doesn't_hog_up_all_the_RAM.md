---
title: "Audio player that doesn't hog up all the RAM"
date: 2013-03-08
forum: Multimedia Software
---

### Post by Dagon^ on 2013-03-08
Hey guys!
I apologize if I'm stupid enough to create a thread with a subject that already exists.
I am a newbie at this forum and I wasn't in the mood of searching through a million threads.

Let me just say that I'm not a newbie in the world of Linux and Ubuntu since I've been using it for the past 6-7 years.

To the question!
I'm constantly looking for an audio player that doesn't hog up all the RAM. I've got 6GB and the last players I've tried consumed at least 700MB of RAM and that's not okay.

After all the "research" I've done, digging through the Software Center, installing almost every audio player there is I'm back with **mocp **again.

So, is there an audio player that doesn't eat all my RAM?
I already know of **mpd **and **xmms2**. I'm thinking a complete audio player with a GUI like **banshee **etc.

Shoot!

---

### Post by mc4man on 2013-03-08
How are you coming up with this 700MB number?
(if it's VIRT in top then you are mis-understanding it

---

### Post by Dagon^ on 2013-03-08
700MiB that is in the system monitor.

---

### Post by speartip on 2013-03-08
Even Amarok, which is probably the most resource hungry media player in Linux, is using less than 100mb ram of my 4 Gig.
How are coming up with that figure? & What system are you running, is it a proper install, wubi, or a virtual install?

---

### Post by mc4man on 2013-03-08
Generally all players here use 30 -60 MiB, rhymthbox a bit more.
(all just a drop in the bucket on machines with decent ram

The current exception would be banshee which here on 13.04 may have quite a memory leak - 1 Mib per sec while playing
(am going to look at that further shortly
Edit: that was only on a first run of banshee, now holding around 42MiB

---

### Post by Dagon^ on 2013-03-08
This is a clean install of Ubuntu 12.04 since a week ago. And yes, it's updated etc.

Sure, **mocp** uses about 50MiB and that's okay in my book.

OT; Just out of curiosity. Why would I listen to music in a wubi och virtual install? :P

---

### Post by andrew.46 on 2013-03-09
Hmmmm.... has anybody mentioned Audacious yet? It looks good and runs nicely with not much ram-grabbing. Not sure of the exact figures...

---

### Post by mc4man on 2013-03-09
> **andrew.46 said:**
> Hmmmm.... has anybody mentioned Audacious yet? It looks good and runs nicely with not much ram-grabbing. Not sure of the exact figures...
about 24MiB avg.  here
(pidstat is pretty accurate, in sysstat package

---

### Post by andrew.46 on 2013-03-09
What commandline are you using for pidstat?

---

### Post by mc4man on 2013-03-09
> **andrew.46 said:**
> What commandline are you using for pidstat?
```

pidstat -r -p [COLOR="#0000CD"]2666[/COLOR] 2 25  >> aud_mem.log
```

Where blue is process id, 2 = secs between reports, 25 = number of reports (time & number as suitable
(mpstat is also an interesting tool

---

### Post by andrew.46 on 2013-03-09
Thanks, I shall experiment :)

---

