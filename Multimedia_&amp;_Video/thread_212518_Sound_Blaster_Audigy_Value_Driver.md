---
title: "Sound Blaster Audigy Value Driver"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by krazykirk on 2006-07-10
Hi everyone,

I was trying to get sound to work with more than one app at once by following a guide, and I installed a Alsa driver, but I installed the wrong one! I accidentally installed the one for Sound blaster Live value! (emu10k1)

I was looking for the right driver on the website, (Sound blaster audigy value driver) and It's not there!

So does anyone know what the driver is for that card?

Or a way to revert to my old driver?

Thanks!

---

### Post by crispy_420 on 2006-07-10
Who's website are you getting them from? I have the Sound Blaster Live 5.1 and it works right at install. All of my drivers are already part of the install. And I think I can play multiple sounds from different apps. But if you think you messed up a driver install try a reinstall through apt-get/synaptic. I think alsa is all you need. Good Luck

---

### Post by krazykirk on 2006-07-10
Yeah my sound card worked fine after install, but then I installed the alsa drivers and now they don't work :(

---

### Post by krazykirk on 2006-07-10
Woohoo!! FIXED!!!

I figured out that the right driver is ca0106, and i also removed alsa from synaptic, (i don't know if that did anything though) =D

---

