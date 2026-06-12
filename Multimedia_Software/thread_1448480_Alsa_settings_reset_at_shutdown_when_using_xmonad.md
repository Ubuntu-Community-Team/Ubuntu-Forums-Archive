---
title: "Alsa settings reset at shutdown when using xmonad"
date: 2010-04-06
forum: Multimedia Software
---

### Post by Kodpoet on 2010-04-06
Hi,

Since I switched to xmonad I seem to always have to manually raise the master, headphone, PCM and speaker in alsamixer manually after rebooting my computer. I tried saving the settings with

```

sudo alsactl store 0

```but that only gave me the output:

"Home directory /home/myNick not ours."

Can I make a script that sets the volume to my desired levels, is there a configuration file somewhere I can simply edit or just tweak the code above?

I'm thankful for any help. ^^

---

