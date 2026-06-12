---
title: "[FIX] Strange hissing noise on HP Beats Laptop"
date: 2016-08-13
forum: Multimedia Software
---

### Post by the_hardy_kid on 2016-08-13
I fixed a problem on my HP Pavilion 15 Notebook with built-in Beats Audio (Realtek ALC3241), where the audio would make constant hissing noise. This is running **Ubuntu Mate 16.04**.

[LIST]
[*]I installed Alsa and disabled PulseAudio, but that didn't solve it. 
[*]I tried the power-save settings given [here]("http://askubuntu.com/questions/632306/hissing-noise-over-headphones-only-in-ubuntu"), that didn't work.
[*]I tried messing with my *alsa-base.conf* in various ways, but to no avail.
[*]
[/LIST]

So finally what did work was installing ```
sudo apt-get install alsa-tools-gui
``` and running ```
hdajackretask
```
I checked "Advanced Override" and changed pin 0x15's Jack from 6.5mm to 3.5mm and Installed Boot override - restart and all fixed!

Hopefully this helps someone out in future.

---

