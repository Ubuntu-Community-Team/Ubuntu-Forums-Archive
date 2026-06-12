---
title: "How can I get real ALSA and not pulseaudio-alsa-plugin ?"
date: 2009-11-07
forum: Multimedia Software
---

### Post by scotty64 on 2009-11-07
I notice that every attempt to make some of my apps use ALSA gets intercepted by pulseaudios ALSA plugin and the sound goes to pulse.
Pasuspender does not work and there is no .asoundrc or /etc/asound.conf that tells the system to behave like this. I tried with these configuration files but the system still wants to impose pulseaudio on me.
I discovered that when I kill pulse all ALSA devices and plugins become available. This is different from 8.04: On my "Hardy" installation pulseaudio and ALSA coexisted. Even with pulse running I could use those devices that had no pulse-streams connected.
Can anyone tell me how stop pulse hijacking ALSA and to enable real ALSA on Karmic without having to remove pulse?

---

### Post by scotty64 on 2009-11-08
> **scotty64 said:**
> I notice that every attempt to make some of my apps use ALSA gets intercepted by pulseaudios ALSA plugin and the sound goes to pulse.
Pasuspender does not work and there is no .asoundrc or /etc/asound.conf that tells the system to behave like this. I tried with these configuration files but the system still wants to impose pulseaudio on me.
I discovered that when I kill pulse all ALSA devices and plugins become available. This is different from 8.04: On my "Hardy" installation pulseaudio and ALSA coexisted. Even with pulse running I could use those devices that had no pulse-streams connected.
Can anyone tell me how stop pulse hijacking ALSA and to enable real ALSA on Karmic without having to remove pulse?

Well, this is not really "Solved", but as I could not work with this buggy sound system any longer I decided to move from Gnome to KDE.
I am happy and everything works now.
Goodbye Gnome, goodbye Pulseaudio - Welcome KDE !

---

