---
title: "ALSA: Force mono (single channel) output"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by pop1280 on 2007-06-09
For my system, I need to force ALSA to downmix everything to one channel.  Back on my old ubuntu setup, I used ESD and esdfilt to do this, but since the upgrade, I've switched to ALSA and dmix.  Unfortunately, a google search that includes the word "mono" tends to get a lot of hits for a certain open source project.

---

### Post by pop1280 on 2008-01-10
Since this thread is pretty high on a google search, I thought I would post my workaround.  The goal of downmixing was to get mpd to output in mono.  It turns out that I could get that using the /etc/mpd.conf file and setting the audio_output_format to 1 channel instead of 2.

---

