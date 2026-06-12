---
title: "Default to SPDIF output"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by xxcite81 on 2007-09-27
I had a lot of problems defaulting to SPDIF. when i used the sound program i go ck809-iac958 (spdif ) to work in some of the programs but programs like flash in firefox still went through the normal 3.5mm jack. i seached and searched and made a lot of chages all  not working until i found this

```
pcm.!default {
type plug
slave {
rate 48000
pcm "spdif"
}
}
```

It work seamlessly on Fiesty Fawn
just place it in your .asoundrc file in your home directory.

---

### Post by buntmebaby on 2007-10-09
Man I hope this works!  Thanks, I'll give it a try.
I have an old Gigabyte mobo with nforce2 chipset sound.
The SPDIF output works fine from in Winblows XP, but I can't seem to get it to go yet from Kubuntu, which is annoying cos my speakers are digital.

---

