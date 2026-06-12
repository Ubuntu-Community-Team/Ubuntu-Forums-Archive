---
title: "Can't record with Audacity"
date: 2008-09-20
forum: Multimedia Software
---

### Post by svivian on 2008-09-20
I've searched through tons of forum threads but not found anything helpful. I want to record whatever my computer is playing, i.e. record what's coming through the sound card. I can do this on Windows with no probs, but not in Ubuntu. I think I've tried every combination of settings I can think of.

My sound card is a realtek (don't know exactly what type - is there a command that will tell me?).

In Audacity prefs the options I get under Recording are:
OSS: /dev/dsp
ALSA: HDA nVidia: ALC883 Analog (hw:0,0)
ALSA: HDA nVidia: ALC883 Analog (hw:0,4)
ALSA: default

If I'm playing any audio the "playback" field is disabled. I'm using version 1.3.4 (newest, beta)

Can anyone give me some hints, things to try, etc?

---

### Post by vwbug on 2008-09-20
Hi,

See my thread regarding this. Never could get my Realtek to record but I could with my Turtle Beach card.  There was no option for "mixer", but when I installed the old card, I had the option. Not sure why but it works:)

---

### Post by eye208 on 2008-09-20
@svivian:

Audacity is currently incompatible with PulseAudio. You can make it work either by suspending PulseAudio before starting Audacity (using the "pasuspend" command) or by removing PulseAudio altogether (see [here](http://ubuntuforums.org/showthread.php?t=885437)).

@vwbug:

Some ALSA drivers don't offer the "Mix" option because it is redundant. ALSA brings its own loopback driver which is much more versatile anyway. See [here](http://ubuntuforums.org/showthread.php?p=5817175#post5817175) for more info. This driver completely bypasses any soundcard hardware and therefore does not affect sound quality in any way (i.e. no sample rate conversion etc.).

---

### Post by svivian on 2008-09-20
> **eye208 said:**
> @svivian:

Audacity is currently incompatible with PulseAudio. You can make it work either by suspending PulseAudio before starting Audacity (using the "pasuspend" command) or by removing PulseAudio altogether (see [here](http://ubuntuforums.org/showthread.php?t=885437)).

No luck here. I've followed the instructions to replace pulseaudio with esound. Audio playback is fine. "Volume control" is using ALSA, as is Audacity. Nothing coming up when I record. I tried installing oss as another thread suggested and running both audacity and vlc through aoss, still nothing!

---

### Post by eye208 on 2008-09-20
As I said before, if the ALSA driver for your soundcard does not offer a "mix" recording source, you have to use the loopback driver.

---

### Post by svivian on 2008-09-21
Thanks for your help so far :)

I've set up the loopback driver like your instructions, but the asound command at the bottom of the post doesn't work, I get "audio open error: Device or resource busy".

Also you say further down "Audacity doesn't work properly with the loopback driver" - is that still the case?

---

### Post by svivian on 2008-09-21
Update: I installed Ardour as suggested in the other thread, but I get an error when trying to make a new session: "Ardour could not start JACK". I've tried various parameters but no luck.

Regarding the previous problem, a restart fixes the "busy" message but Audacity isn't recording still. I'd really like to use Audacity if possible. Why can't this be simple?!

---

### Post by markbuntu on 2008-09-21
It is better to start jack before starting ardour. You need to have jack installed to do that. look in my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Look for the jack section.

The reason that audacity is such a pain is that it was written for the portaudio sound server which was never used by many distributions so it is somewhat of an orphan. The alsa and oss plugins for audacity were not written very well so it is somewhat problematic to get working correctly.

---

