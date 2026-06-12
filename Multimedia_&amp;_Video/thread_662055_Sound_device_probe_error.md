---
title: "Sound device probe error"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by npepinpe on 2008-01-08
Hi,

While trying to setup my sound card (a Creative Labs Audigy SB Live!) with the emu10k1 drivers, I ran into an annoying problem : the sound device is loaded successfully three times out of four.

I get the following error when doing a "dmesg | grep -i emu" :

> EMU10K1_Audigy: probe of 00:0e.0 failed with error -12

Now, I made sure using lspci that the sound card is found, the drivers are properly installed (considering it does work from time to time without a probe error).

I just found out, however, that a probe error of -12 might be caused by each devices fighting over which sound card number they want to be.

I tried a couple of "options snd-emu10k1 index=" configuration, but should I put a minus to it it simply doesn't load (no matter what the guide says). I tried giving them indexes (0, 1, 2, etc.), but now it simply doesn't load.

Anybody out there got a solution for me?

---

### Post by Yellow Pasque on 2008-01-08
If it's fighting with onboard sound, and you're not using the onboard sound, try disabling it in the BIOS. There's also a way to assign the default device in ALSA, but I can't recall how off the top of my head. Search around.

---

