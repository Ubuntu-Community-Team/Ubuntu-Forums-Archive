---
title: "Firefox blocking the sound from VLC player and vice versa"
date: 2012-01-12
forum: Multimedia Software
---

### Post by Lektorvis on 2012-01-12
I can not get sound from VLC Player if have started a streaming in Firefox first, Or the other way round I get no sound from Firefox if I started up VLC first.

I have ALSA and PulsAudio installed.

---

### Post by lidex on 2012-01-12
Make sure you have installed libasound2-plugins and vlc-plugin-pulse and select pulse audio output in vlc preferences.

---

### Post by Lektorvis on 2012-01-13
ThankYou lidex

That did the trick:
> **lidex said:**
> Make sure you have installed libasound2-plugins and vlc-plugin-pulse and select pulse audio output in vlc preferences.

I reinstalled both plugins, but the real fault probably was the missing settings in VLC ;)

---

