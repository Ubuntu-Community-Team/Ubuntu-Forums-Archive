---
title: "jackd and jitter/skipping"
date: 2009-09-25
forum: Multimedia Software
---

### Post by genjix on 2009-09-25
hey all,

i have jack installed so i can play with puredata but when i play 2 sound files at the same time i start getting jitter and skipping which doesnt normally happen so i figure i have a bad setup.

# /sbin/alsa force-reload
# jackd -Rd alsa &
# qjackctl &
# pd

i do this as root. any suggestions?

---

### Post by luctor on 2009-09-25
did you install a real-time kernel ?

and why are you running this as root ?
(just curious)

---

### Post by genjix on 2009-09-25
nope, i haven't got a real time kernel. is it possible to install this without recompiling one cos its really time consuming and i want ubuntu updates. im not sure i need this at all tho as non jackd audio with KDE is FINE. makes me think i have a setup problem with jack.

i run as root as jackd needs to be run as root to use -R (realtime switch) and qjackctl/pd cannot connect to jack unless theyre root- sure theres another way, but not my main concern now

---

### Post by genjix on 2009-09-25
bump

---

### Post by raboofje on 2009-09-25
> **genjix said:**
> nope, i haven't got a real time kernel. is it possible to install this without recompiling one cos its really time consuming and i want ubuntu updates.

You should be able to install the 'linux-rt' package. I remember some of the -rt kernels in Ubuntu weren't very good - not sure if that changed since (switched back to Debian myself), but you might want to try it out.

> im not sure i need this at all tho as non jackd audio with KDE is FINE. makes me think i have a setup problem with jack.

Do you see 'xrun' messages in the Jack messages?

> i run as root as jackd needs to be run as root to use -R (realtime switch)

This is not actually true. You can set up your limits.conf to allow your audio processes to use realtime-mode. This didn't really seem to be documented in an obvious place, so I added it to [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting)

> qjackctl/pd cannot connect to jack unless they're root

Indeed, you must run the jack 'clients' as the same user as jackd.

---

