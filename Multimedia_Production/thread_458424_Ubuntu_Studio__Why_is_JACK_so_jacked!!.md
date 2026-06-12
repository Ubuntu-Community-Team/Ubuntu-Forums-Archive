---
title: "Ubuntu Studio:  Why is JACK so jacked?!?!"
date: 2007-05-29
forum: Multimedia Production
---

### Post by michwill on 2007-05-29
Hi All,

Working with Ubuntu Studio here.  Can someone please explain to me why in the world JACK works the way it does (e.g. hijacking system sound) and who in the world thought that was a good idea?  I'm currently trying to work with Audacity but I can't unless Jack is running (which is retarded because I'm not sure that was the case in my previous distros).

Why can I not work with JACK related programs and still use sound otherwise?  Although it seems unlikely that people would *need* to do this, forcing it to be the case is simply unacceptable.  Take me to your architect!!! :mad:


. . .seriously though, please help


Thanks

---

### Post by MetalMusicAddict on 2007-05-29
Just how it is.

[JACK]("http://jackaudio.org") On IRC talk to people on #jack or #ardour.

---

### Post by moron on 2007-05-30
If jackd is taking complete control of your sound then this is more of an ALSA configuration problem than a Jack one since ALSA should be doing software mixing if needed.  

ALSA is the lower level sound card driver.  It depends on your card as to whether it has an onboard mixer or not (some cards like the M-Audio USB Audiophile don't have them) as well as whether it needs some special setup to support multiple clients at once.  

You could just as easily be asking why your Gnome or KDE audio daemon is taking control of the card since that is what happens the rest of the time.  

All that said, the whole point of Jackd is to have reliable, sample accurate co-ordination between audio clients.  So it actually makes more sense to not have another daemon messing around with the soundcard at the same time since that could lead to issues with timing and such.  For example, if you are using Ardour you certainly don't want KDE (or Gnome) messing with your audio performance to play superfluous system sounds.

Jackd is intended to be a professional level audio subsystem so their concerns are not so much whether it integrates nicely with regular desktop applications.  If you are building a dedicated Ardour box (for example) you could care less whether the mail bell rings (your machine likely isn't even connected to the Internet).

=)

Cheers

---

### Post by kayosiii on 2007-05-31
Jack only takes over the soundcard in a case where the card does not support hardware mixing and dmix is not configured properly.

The primary concerns with Jack design are low latency, reliability and the ability to chain audio from one app to another.

---

