---
title: "Weird issues using OSS4 on Ubuntu 10.10"
date: 2011-03-11
forum: Multimedia Software
---

### Post by rocky5051 on 2011-03-11
Recently I dumped PulseAudio/ALSA on my laptop in favor of OSS4. I had done this previously on my PC (which runs Debian 6) successfully, but after purging pulseaudio, removing alsa, and installing/configuring OSS4 I managed to get the sound to work only under weird conditions.

Weird conditions in the sense that if I use gstreamer-properties and click "test", I get a tone, but if I go and start up Rhythmbox, I get no sound. *However,* if I go back and click on "test" again, the sound from Rhythmbox randomly picks up (assuming I left Rhythmbox playing a song).

It seems as long as one application has active channels going after this, I can open as many applications as I want and hear sound. But if I close all of these applications and try to fire one up again, there is once again no sound, and I have to click "test" again in gstreamer-properties to bring the sound back.

Even weirder is that in ossxmix, you can clearly see audio being processed, but you can't hear it.

Any ideas?

---

### Post by tommcd on 2011-03-12
> **rocky5051 said:**
> Recently I dumped PulseAudio/ALSA on my laptop in favor of OSS4.
I can fully understand getting rid of that horrible resource hogging scourge that is pulseaudio; but why get rid of alsa? The alsa CPU utilization is low, and it works well. 
I have not found OSS4 to offer better sound quality. I guess that this can vary depending on the sound card and driver used though.
If you really want to only use OSS4, perhaps this tutorial will help: [http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html)

---

### Post by rocky5051 on 2011-03-12
> **tommcd said:**
> I can fully understand getting rid of that horrible resource hogging scourge that is pulseaudio; but why get rid of alsa? The alsa CPU utilization is low, and it works well.

While ALSA does indeed work well, it doesn't share out my cheapo audio chipset on my laptop like OSS4 can. I might not mind it so much if it were my PC where I could buy a nice sound card that can mix multiple channels on its own. OSS4 accomplishes that with less lag than PulseAudio, uses less CPU, and doesn't make short audio clips sound distorted (i.e. logon/logoff sounds in Pidgin).

I'll check out that tutorial and share the results, though. Thanks. :)

EDIT: That was the tutorial I used. The only discrepancies between my process and the one listed is I'm using Ubuntu 10.10, not 10.04. I also didn't have to do anything manual with the dkms package, as that was fixed in 10.10.

---

