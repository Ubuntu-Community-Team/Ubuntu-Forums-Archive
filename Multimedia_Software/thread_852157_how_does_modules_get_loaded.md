---
title: "how does modules get loaded?"
date: 2008-07-07
forum: Multimedia Software
---

### Post by amba on 2008-07-07
Hi all,
some time ago i bought an HP laptop, and managed to get sound working (including headphone) by adding this line to /etc/modprobe.d/alsa-base:
```

options snd-hda-intel model=hp

```

Then i tricked a bit whole distro in order to get wlan/wacom tablet/ecc to work.
Now headphone works no more, but laptop sound is fine.
Just to be sure that distro updates didn't break smthing, i reinstalled whole kubuntu in other partition, edited ONLY alsa-base with below line, installed all the updated and it still worked.

My question is:
What the hell did touch in the configs? Which config files may be overriding my custom option in alsa-base at boot?

Note: 
/etc/modules here is same as the new fresh working install. Must look somewhere else.

Thank you very much for patience with a chaotic newbie :)
I would like to fix this in the old ubuntu partition, rather than get the new install ready for complete use...

---

