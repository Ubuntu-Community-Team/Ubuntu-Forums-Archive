---
title: "Lucid: Alsa problems - clicks and stuttering"
date: 2010-05-26
forum: Multimedia Software
---

### Post by ___Kevin___ on 2010-05-26
Hi,

since upgrading to lucid I have serious sound problems.
I am using the SPDIF port of my onboard SigmaTel STAC9227 (HDA Intel) chip. 
Whenever sound is played by any application, sound stutters. Feels like the sound is muted for a couple of milliseconds - every few seconds. Also, when playback is finished I get clicks every few seconds. I ran the alsa-info script, here's its output:

[http://kkdevs.com/alsa.txt]("http://kkdevs.com/alsa.txt")

I tried lots and lots of workarounds, to no avail. Even uninstalled pulseaudio - still the same problem, looks like this is an alsa issue.
I tried different model types in alsa-base.conf, the only one producing sound is "5stack".
I also tried tweeking .asoundrc all to no avail.

Now my knowledge is finished - any more hints?

thanks a lot,

Kevin

---

### Post by ___Kevin___ on 2010-05-27
*Bump*

---

### Post by copycat on 2010-06-13
> **___Kevin___ said:**
> Hi,

since upgrading to lucid I have serious sound problems.
I am using the SPDIF port of my onboard SigmaTel STAC9227 (HDA Intel) chip. 
Whenever sound is played by any application, sound stutters. Feels like the sound is muted for a couple of milliseconds - every few seconds. Also, when playback is finished I get clicks every few seconds. I ran the alsa-info script, here's its output:

[http://kkdevs.com/alsa.txt]("http://kkdevs.com/alsa.txt")

I tried lots and lots of workarounds, to no avail. Even uninstalled pulseaudio - still the same problem, looks like this is an alsa issue.
I tried different model types in alsa-base.conf, the only one producing sound is "5stack".
I also tried tweeking .asoundrc all to no avail.

Now my knowledge is finished - any more hints?

thanks a lot,

Kevin

Hi same here, Lucid server with XBMC frontend stuttering on video's trough spdif and IEC958.  There are more people with the same issues.  ppa update from alsa 1.0.22 and 23 didn't fix it.   

Let's hope a fix is coming.  I see more people with iec958/spdif issues.

---

