---
title: "Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by troynel on 2007-09-09
I've been trying to get this sound card working for a while now under feisty. I finally have and decided to share how my solution. 

The first thing is the card is not actually what it appears to be from lspci. From lspci I get:

"Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)"

Looking at my motherboard book (motherboard is NF61S) shows that the card is actually a RealTek ALC861. To make this card work, add the following to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

I got this from a bug report. I don't have the URL anymore. Anyway, hope that helps some people get their sound working. Just remember to look closer at what your card actually is and don't waste time on the generic bus name given from lspci.

---

