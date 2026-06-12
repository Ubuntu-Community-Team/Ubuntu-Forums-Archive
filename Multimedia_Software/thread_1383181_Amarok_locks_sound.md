---
title: "Amarok locks sound??"
date: 2010-01-16
forum: Multimedia Software
---

### Post by Roasted on 2010-01-16
With Kubuntu, using a range of KDE versions... 4.2.2, 4.3.2, and 4.4 RC1, I have had the same issue.

When Amarok or Dragon Player is running, it locks all system sounds. If I go to YouTube and play a video, I have no audio from it. If I close Amarok/Dragon Player, as well as Firefox, restart Firefox to the YouTube page, suddenly I have sound. But Amarok/Dragon Player cannot co-exist with other sound devices. It's one or the other, more or less.

I installed Mandriva Free 2010 to mess around with, as well as openSUSE 11.2. Both KDE installs on those distros did NOT have this problem. I fire up Ubuntu on here, install the KDE desktop, upgrade to the 4.4 RC1 PPA, and blam - problem is back.

It's something specific to KDE with *buntu, yet I don't know what it is.

My sound backend is xine. I'm not sure what else I can do. :(

---

### Post by Roasted on 2010-01-17
Yay for pulse audio sucking.

apt-get remove --purge pulseaudio
apt-get install alsa alsa-oss

fixed.

win.

---

### Post by Roasted on 2010-01-17
Bumping for new problem:

Just redid my laptop and desktop today. Kubuntu 9.10 64 bit. Same CD for both systems.

My desktop will not let Amarok and other music applications (YouTube, etc) play at the same time.

My laptop will.

This inconsistency is starting to piss me off. I did the same thing on both systems, yet I'm getting different results.

Both backends are xine.

Looking for an answer... and removing pulse audio isn't a valid one considering one system works fine...

---

### Post by sports.car.guy on 2010-01-17
You might have done everything the same between the two systems but comparing the two is apples and oranges. For starters one is a tower and the other is a laptop. The hardware is going to be totally different.

Removing pulseaudio is a valid response in all honesty. This inconsistency is due to it, not KDE or Ubuntu. If you remove it and everything works it is pulseaudio. You can't say it isn't a valid response if it walks like a duck, quacks like a duck, it probably is a duck.

Pulseaudio is being put in a roll it was truly not designed for, real time audio playback by the makers of distributions. Kubuntu does not use it. You have to install it in order to get it up and running on Kubuntu. It is not installed by default.

---

### Post by Roasted on 2010-01-18
The bottom line is, I need my system to work. I had no issues in Ubuntu. But I have issues in Kubuntu. KDE or not, this is a red flag.

What do I need to do to get things running? Do I need to install pulse audio, or remove it? 

Very tempted to just throw Ubuntu back on here. I just need things to work. I'm sick of fighting. :(

Currently I have NO audio through youtube - and this is with a fresh boot and opening no other applications...

sigh...

EDIT - removed pulseaudio with --purge, installed alsa and alsa-oss. Same deal...

---

### Post by Roasted on 2010-01-18
Okay, I have since put Ubuntu back on my laptop. As a little test, I installed Amarok.

Amarok + YouTube = Don't work well together (meaning only 1 can play sound at once).
RhythmBox + YouTube = Fine.
VLC + YouTube = Fine.
Exaile + YouTube = Fine.

So it's clear it's something KDE related, since Amarok is a KDE application.

Can anybody shed some light?

---

### Post by Yellow Pasque on 2010-01-18
Since it seems that gstreamer apps (exaile, rbox) + youtube work well, then my guess is that xine is locking the audio (xine is the default backend to phonon/KDE). Try the phonon-gstreamer backend.

---

### Post by Roasted on 2010-01-18
> **Temüjin said:**
> Since it seems that gstreamer apps (exaile, rbox) + youtube work well, then my guess is that xine is locking the audio (xine is the default backend to phonon/KDE). Try the phonon-gstreamer backend.

How do I install it? The only option I had (that I remember on Kubuntu) was xine.

In fact, now that you mentioned it it sounds familiar to what someone told me to do on the Mandriva forums when I was running Mandriva last month....

---

### Post by Yellow Pasque on 2010-01-18
Search Synaptic for phonon-gstreamer
Also, this command may help:
```
qtconfig
```

---

### Post by Roasted on 2010-01-18
Is there a difference in quality between gstreamer and xine?

---

### Post by Yellow Pasque on 2010-01-19
> **Roasted said:**
> Is there a difference in quality between gstreamer and xine?
IDK. I always use foobar2000 (through WINE, with Noise Sharpening plugin/foo_dsp_delta), OSS4, and the hardware mixer of my M-Audio Revolution 5.1 card. Best analog audio quality without doing anything expensive/custom (external DAC's, replacing op-amps) IMHO.

---

### Post by Roasted on 2010-01-19
> **Temüjin said:**
> IDK. I always use foobar2000 (through WINE, with Noise Sharpening plugin/foo_dsp_delta), OSS4, and the hardware mixer of my M-Audio Revolution 5.1 card. Best analog audio quality without doing anything expensive/custom (external DAC's, replacing op-amps) IMHO.

Well, if KDE uses Xine, and Gnome uses GStreamer, then that's evident enough there's no noticeable difference. I have quite a few boxes here, all mixed up between Ubuntu and Kubuntu. No noticeable differences here.

---

