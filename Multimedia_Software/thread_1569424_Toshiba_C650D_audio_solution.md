---
title: "Toshiba C650D audio solution"
date: 2010-09-06
forum: Multimedia Software
---

### Post by jaddle on 2010-09-06
This is a solved problem - I'm just posting it here in case someone else has the same trouble, since it wasn't at all easy to find the answer through google!

I just set up Lucid on a Toshiba C650D for a friend. We ran into some ACPI issues, but following the instructions at [https://bugs.launchpad.net/ubuntu/+bug/612341](https://bugs.launchpad.net/ubuntu/+bug/612341) solved those.

However, then we had an issue show up where audio input wasn't working - everything looked like it worked, but despite the mixer being set up, no audio data ever came in, either with the internal mic, or and external one through the 3.5mm jack.

The solution was to add
```
options snd-hda-intel model=ideapad
```

To a /etc/modprobe.d/sound.conf file (I just created this file). Apparently the ideapads use the same sound chip (Conexant CX20585), so their option also works for the Toshiba!

Hopefully this will be helpful for someone else.

---

