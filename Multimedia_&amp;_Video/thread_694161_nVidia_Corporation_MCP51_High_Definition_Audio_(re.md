---
title: "nVidia Corporation MCP51 High Definition Audio (rev a2) headphones"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by TorchlightJay on 2008-02-11
Hey everyone. 

I am running Hardy Alpha 4 on my new tx2000z and it uses nVidia Corporation MCP51 High Definition Audio (rev a2) for audio. I installed alsa-1.0.16 and tried that one bug fix hda-generic-hp-fix.diff and I tried a few other things too. I went into /etc/modprobe.d/alsa-base and put in 
"options snd-hda-intel model=3stack". By putting that line in, that's the only way I get any sound. However, i do not get anything from the headphones. Mic and Line seem to work fine but nothing from the headphones. It is really irritating. Anyone have this problem and solve it yet? Thanks all.

---

