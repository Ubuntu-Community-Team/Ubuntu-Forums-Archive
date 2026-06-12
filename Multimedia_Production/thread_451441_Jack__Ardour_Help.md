---
title: "Jack / Ardour Help"
date: 2007-05-22
forum: Multimedia Production
---

### Post by eArquilla on 2007-05-22
To start out - I've been playing guitar for years, but as many, I have just begun to want to record. I figured UbuntuStudio is the distro for me since I've been using Ubuntu for over a year now.

I have not purchased an audio interface yet (thinking about getting the Presonus Firebox), so I just have the stock soundcard that came with my Jetta Jetbook 9700PX.

Here is the situation: After running qjackctl and launching ardour, I decided to import music (since I can't plug my guitar into anything just yet) to get the feel for ardour. I converted some clapton song into a .wav file, imported it into a track, everything worked fine. The problem is that when I play it, it is very... slow and choppy. I cannot play any audio outside of jack (such as rhythmbox) at all when jack is running (I'm not sure if this is supposed to be like this). 

Even when I launch hydrogen without jack and play a 'demo' that was already made for me, it was slightly choppy (although not nearly as bad as trying to play music in ardour with jack running).

Is this a problem with my soundcard- just too low quality for multimedia editing? Will this be fixed when I purchase my firebox? I have, on my own experimenting, found it to be less choppy when I change the latency (increasing it), but isn't the point to have low latency? 

Forgive my noob-ness, but I have been searching everything from the jack manual, ardour faqs, even posts on this forum to no avail. Closest thing I've heard is that running jack in real time can 'improve your experience' although I am not sure what real time even is.

Any help / suggestions / noob flaming?

PS. Songs sound fine when jack is not running (besides hydrogen).

---

### Post by bonsiware on 2007-05-22
same here on my acer aspire 9411... I have a realtek high definition card, but jack output is slow and choppy...

why?

---

### Post by kayosiii on 2007-05-24
It sounds like your Soundcard doesn't do hardware mixing...
this means that once Jack is running it pretty much takes over the whole soundcard. My old system did this and it sucks.
(BTW I am the proud owner of a Presonus Firebox and can reccomend it)

There are two things that be done to stop the stuttering - first things first... Jackd - works a lot better when run in realtime mode. What worked for Edgy was to install the realtime-lsm package (does this still work with feisty) or to set rlimits (need to find details on that I know its in the linux forum at ardour.org)...

the second thing you can do is choose a larger buffer size. This will make playback smoother but increase latency.

Let me know if any of this helped...

---

### Post by alecz20 on 2008-03-16
Did not work for me...

I tried increasing latency, but if it is very high, Jack is being shut down. I couldn't find the buffer setting option.

I don't get it.... why is ardour playback choppy?

BTW the .wav file plays fine in MPlayer!

Any suggestions?

---

### Post by alecz20 on 2008-03-16
Ok, I figured what I had to do on my system:

Open Jack
code: qjackctl

then in Setup -> settings I did the following:

- Checked Monitor
- set frames/period to 512
- set periods/buffer to 3
and, MOST IMPORTANTLY:
changed the interface to hw:0,0
using default or hw:0 makes playback choppy.
I don't know why, but this worked for me...
Apparently hw:0,0 is ALC883 Analog

Good Luck!

---

### Post by Grinder on 2008-03-17
> **alecz20 said:**
> Ok, I figured what I had to do on my system:

Open Jack
code: qjackctl

then in Setup -> settings I did the following:

- Checked Monitor
- set frames/period to 512
- set periods/buffer to 3
and, MOST IMPORTANTLY:
changed the interface to hw:0,0
using default or hw:0 makes playback choppy.
I don't know why, but this worked for me...
Apparently hw:0,0 is ALC883 Analog

Good Luck!

Thanks man! I've been wrestling with this all afternoon. 

I've actually gotten the latency down to 17.4 by lowering the "set frames/period to 256"

---

### Post by konlevin on 2008-03-24
Thanks alecz20! I thought for sure the choppy audio was going to be a show stopper,

---

