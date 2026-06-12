---
title: "No soud in Hardy Heron with Realtek AC98"
date: 2008-04-29
forum: Multimedia Software
---

### Post by silvano.jorge on 2008-04-29
Hello all

I have this problem, from the last update, Hardy. Each time I boot the sound is reconfigured and it doesn't work.

I have an Acer TravelMate 4152LMi, which have Pentium M740 with 21.73GHz
The Soundcard is a Realtek AC'97 series.

Looking into de kmix I see that the Intel ICH6 mixer doesn't work, and it is pcsp who works.

To solve it for each boot I do the following.

First I reinstall the official drivers.
Then 'alsa reload'
And finally '/etc/init.d/alsa-utils restart'

Everything goes very well, but if I reboot the solution disapears.

Oddly, some time after, a mesaage appears
"error arts message: Sound Server Fatal Error: cpu overload, aborting"
The sound continues running, but wtf means this?

It is a bug? What I have to do to fix it permanently?

Thanks, greetings everybody

---

### Post by silvano.jorge on 2008-05-06
He, nobody knows anything?

Ok, I think that it is an artsd problem. If I kill this process previously to reboot then in the initialization of this process there is an error, but it goes well in the second attempt. The sound don't run yet but yes if I do an "alsa reload" (killing all sound proceses of course), in this case I haven't to teinstall the drivers.

WTF is it happen in my ubuntu?

---

### Post by silvano.jorge on 2008-05-12
I found the quickly temporal solution.
It is necesary only to do a "alsa force-reload" to fix the problem,
maybe the problem is in the kmix daemon, I don't.

Anybody knows anything?

---

### Post by izzyb.ca on 2008-05-26
I'm having the same problem with and Intel 82801G (ICH7 Family) sound card.  Anyone have a solution?

---

