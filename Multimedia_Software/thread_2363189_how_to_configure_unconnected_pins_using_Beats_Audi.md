---
title: "how to configure unconnected pins using Beats Audio"
date: 2017-06-07
forum: Multimedia Software
---

### Post by seifdune on 2017-06-07
[center]*********** split off from [https://ubuntuforums.org/showthread.php?t=2333786](https://ubuntuforums.org/showthread.php?t=2333786) ***********[/center]


> **the_hardy_kid said:**
> I fixed a problem on my HP Pavilion 15 Notebook with built-in Beats Audio (Realtek ALC3241), where the audio would make constant hissing noise. This is running **Ubuntu Mate 16.04**.

[LIST]
[*]I installed Alsa and disabled PulseAudio, but that didn't solve it. 
[*]I tried the power-save settings given [here]("http://askubuntu.com/questions/632306/hissing-noise-over-headphones-only-in-ubuntu"), that didn't work. 
[*]I tried messing with my *alsa-base.conf* in various ways, but to no avail. 
[/LIST]

So finally what did work was installing ```
sudo apt-get install alsa-tools-gui
``` and running ```
hdajackretask
```
I checked "Advanced Override" and changed pin 0x15's Jack from 6.5mm to 3.5mm and Installed Boot override - restart and all fixed!

Hopefully this helps someone out in future.

how to configure unconnected pins using Beats Audio (Realtek ALC3241). i tried many time to find solution but not yet, many people solution based on  IDT 92HD91BXX codec configuration.

---

