---
title: "Upgrade to alsa 1.0.15"
date: 2008-02-13
forum: Mythbuntu
---

### Post by jakep_82 on 2008-02-13
I have an Asus M2V motherboard.  Support for the coxial digital output (iec958 ) wasn't added to alsa until 1.0.15.  Is it possible for me to upgrade without messing up the rest of my system?

---

### Post by david.birch on 2008-02-13
Yes, though after any kernel updates you will need to re-install alsa. I have Asus P5B-VM (ICH8 AD1988 Chip) & spdif now works fine with alsa 1.0.15 built from source. 

I left the default ubuntu alsa driver & utils packages installed & then just built & installed 1.0.15 over the top (make && make install).

I had to add the following options to /etc/modprobe.d/alsa-base

options snd-hda-intel model=6stack-dig
options snd-pcm-oss dsp_map=1

---

### Post by jakep_82 on 2008-02-13
Ugh, my whole reason for switching to Mythbuntu is to avoid building from source.  I have a functional setup with Arch Linux, but it's too much work to maintain.  Maybe I'll just wait for 8.04 :(

---

