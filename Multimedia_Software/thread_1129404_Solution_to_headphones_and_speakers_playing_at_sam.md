---
title: "Solution to headphones and speakers playing at same time"
date: 2009-04-18
forum: Multimedia Software
---

### Post by Guy_AD on 2009-04-18
Hi all. It seems that a lot of people have been having the same issue as I used to - the headphones and speakers play at the same time in a lot of systems with the Intel HDA (ALCxxx) sound cards and the ICH8/ICH8M chipsets. I managed to get this fixed by adding

```
options snd-hda-intel model=auto
```

to my /etc/modprobe.d/alsa-base file.

If this doesn't work for you, you can try going to [http://ubuntuforums.org/showthread.php?t=588089](http://ubuntuforums.org/showthread.php?t=588089) to expand on this solution.

---

