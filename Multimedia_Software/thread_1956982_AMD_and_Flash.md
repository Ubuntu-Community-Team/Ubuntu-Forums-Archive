---
title: "AMD and Flash"
date: 2012-04-11
forum: Multimedia Software
---

### Post by Gannin on 2012-04-11
Has there been any progress on getting accelerated Flash video using ATI / AMD graphics cards?

---

### Post by Yellow Pasque on 2012-04-12
Unfortunately, no. Even nvidia's acceleration got broken by the latest Flash. If you want to watch Flash video in Linux, get a really fast CPU or find a way to work around playing Flash through the plugin (search flashvideoreplacer).

---

### Post by Gannin on 2012-04-12
For me on my nVidia card, video acceleration still works with the latest Flash (11.2) but it's also really unstable and usually crashes if I try to use any of the video controls, such as moving the slider to change position in the video.

---

### Post by lovinglinux on 2012-04-13
> **Gannin said:**
> For me on my nVidia card, video acceleration still works with the latest Flash (11.2) but it's also really unstable and usually crashes if I try to use any of the video controls, such as moving the slider to change position in the video.

Most likely that you have EnableLinuxHWVideoDecode set to 1 in your mms.cfg. Using that avoids disabling hardware acceleration, but causes such instability.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Gannin on 2012-04-13
> **lovinglinux said:**
> Most likely that you have EnableLinuxHWVideoDecode set to 1 in your mms.cfg. Using that avoids disabling hardware acceleration, but causes such instability.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

You are correct good sir, indeed I do.

I also recently read that 11.2 is the last normal release of Flash Adobe is making for Linux, and any future releases will only be bundled with Chrome.

---

### Post by lovinglinux on 2012-04-13
> **Gannin said:**
> You are correct good sir, indeed I do.

I also recently read that 11.2 is the last normal release of Flash Adobe is making for Linux, and any future releases will only be bundled with Chrome.

Yes, that is correct. Form now on, Adobe will only release security patches for 5 years, but not bug fixes. Only Chrome will have the latest flash version, implemented through Pepper API, which nobody wants.

---

### Post by QIII on 2012-04-13
Alas.

But you know, ll, if you have nothing better to do with your free time, you could cobble together some way to make Pepper work with Firefox, right?

I mean, you have tons of free time, don't you?

---

### Post by Gannin on 2012-04-13
> **QIII said:**
> Alas.

But you know, ll, if you have nothing better to do with your free time, you could cobble together some way to make Pepper work with Firefox, right?

I mean, you have tons of free time, don't you?

I imagine when it comes to this, one of two things will happen:

Either Pepper will become very popular and widespread and Mozilla will eventually give in to it just like they did with H.264, or Pepper will largely be ignored and the focus will return to regular style plugins.

---

