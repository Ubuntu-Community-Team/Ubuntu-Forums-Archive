---
title: "No Sound Output"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by falexge on 2006-10-19
I installed Kubuntu on my Dell Optiplex GX1 machine yesterday but just as with other versions of linux that I have installed, there was no sound.
Can anyone help me out? I'm beginning to get pissed off with linux.

I checked with windows and found the sound card to be Crystal WDM

---

### Post by Kateikyoushi on 2006-10-19
Follow this guide and in a few steps you can install your sounds card. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")
If you need help copy these commands to the terminal and post the output here.

```
aplay -l
lspci -v
```

---

