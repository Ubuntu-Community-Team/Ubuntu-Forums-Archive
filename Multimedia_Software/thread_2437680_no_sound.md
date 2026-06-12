---
title: "no sound"
date: 2020-02-27
forum: Multimedia Software
---

### Post by medphys17 on 2020-02-27
Hi all, I am running ubuntu version 18.04 and have a problem with sound.  My sound card is a realtek alc 889 and when I go to pluls audio control the only output that is seen is hdmi/displayport-built-in audio.nothing else is recognized.  Been playing with it for a few hours and nothing I see on the internet works.

Any suggestions as to resolve the issue and get sound?

Thanks in advance

---

### Post by gnusci on 2020-02-28
Please post the output of:

$ dmesg | grep audio

and check:

$ alsamixer

---

