---
title: "Skype and Lucid (10.04) and sound - solved"
date: 2010-12-09
forum: Multimedia Software
---

### Post by fjm03 on 2010-12-09
Running the Skype 2.1.0.81 beta on Lucid, the on-board microphone for several inexpensive video cams would not play nice until the following single adjustment was made:

start Skype >>open Options >> open Sound Devives >> UNtick the box (remove the default) "Allow Skype to automatically adjust mixer levels"

That simple. Apparently the auto adjust under PulseAudio reduces the USB microphone output to 0.

---

