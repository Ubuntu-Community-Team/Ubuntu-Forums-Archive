---
title: "pulseaudio - no sound after jackd accidently installed"
date: 2010-02-25
forum: Multimedia Software
---

### Post by danushk on 2010-02-25
hi guys,

i don't get the sound after i logged it to a session , but sound works before login but no sound even while jackd server is running.

How do i get my sound working  back again ?


/**edit comment**/
solved the audio issue by removing jackd , which is not a very linux way of solving things.
But sadly had to take that route , will try my best to get jackd and pulseaudio running soon. !

---

### Post by RaumTrug on 2010-02-25
stop/kill jackd/qjackcontrol and pulse sound will work again.

either jack grabs the alsa device of the soundcard, or pulse does. both together can only work with a jack sink for pulse, or a pulse sink for jack. I think both exists, but is not included in the standard ubuntu for insane reasons, so installing can be a hassle.

---

### Post by danushk on 2010-02-25
> **RaumTrug said:**
> stop/kill jackd/qjackcontrol and pulse sound will work again.

either jack grabs the alsa device of the soundcard, or pulse does. both together can only work with a jack sink for pulse, or a pulse sink for jack. I think both exists, but is not included in the standard ubuntu for insane reasons, so installing can be a hassle.

Hi Raum ,

i completely removed jackd and qjackctl  and now audio is working now !

---

### Post by RaumTrug on 2010-02-26
hey, no, you don't need to remove them, it's just when the qjackctl app (which can start up jackd, it's just an interface) is currently running, then pulseaudio gets "suspended", which means no normal multimedia sound can get through to the soundcard - that is because jackd needs to get total control over the card to work.

normally, when neither qjackctl or jackd are running (but they can still be installed) pulse should work well. when you use jack, then because you need to have low latency (low delay) audio throughput for audio production, and there's little need for normal stuff like system sounds or the like, it'd just mess up the recordings ;) ...but there's still plugins that enable pulse playback via jack, for people who don't like to terminate their jack server for "normal" multimedia playback - search on these forums, and you'll find sollutions.

if it had really been the case, that jack just being installed (and qjackctl was not running) and pulse sound didn't work, it might surely interest some people why that happened! pulseaudio should work normally when jack is installed, unless the qjackctl app is currently running!

---

