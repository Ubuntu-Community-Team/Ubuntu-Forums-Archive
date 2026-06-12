---
title: "Noisy audio on Dell Latitude 5480"
date: 2021-02-28
forum: Multimedia Software
---

### Post by lukejaeger2 on 2021-02-28
I'm using a Latitude 5480 with Ubuntu Desktop 20.04 as a Spotify player. The headphone audio is super noisy -- sounds like the roar of the ocean, or an overdriven amp. I tried it with a DAC (PreSonus AudioBox) and it was better, but still noisy. 
Any recommendations?

---

### Post by lukejaeger2 on 2021-03-01
OMG this appears to have fixed it:
nano /etc/modprobe.d/alsa-base.conf

insert this line at end of file --> options snd-hda-intel model=dell-bios

[https://www.dell.com/community/Linux-Developer-Systems/alsa-base-conf-and-noise-headphones/td-p/5115568](https://www.dell.com/community/Linux-Developer-Systems/alsa-base-conf-and-noise-headphones/td-p/5115568)

---

### Post by DuckHook on 2021-03-01
Congrats on finding the answer through your own perseverance and initiative. Also, many thanks for posting back your solution. It may help someone else in similar straits. =d>

To that end, I've marked your thread "solved" which you can also do next time using the "Thread Tools" at top of first thread.

---

