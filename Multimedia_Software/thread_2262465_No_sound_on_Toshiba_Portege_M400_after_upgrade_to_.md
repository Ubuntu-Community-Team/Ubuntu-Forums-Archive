---
title: "No sound on Toshiba Portege M400 after upgrade to 14.10"
date: 2015-01-25
forum: Multimedia Software
---

### Post by Joseph_Tortorello on 2015-01-25
I have a Toshiba Portege M400. I originally installed Xubuntu 14.04 on it and the sound worked fine, but after upgrading to 14.10 I can't get any sound at all. When I upgraded, I reinstalled from a disk rather than using the upgrade tool.

Some more info:
My sound card, according to lspci:
```
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
```

When you try to open alsamixer:
```
cannot open mixer: No such file or directory
```

/dev/snd is eerily empty:
```
seq  timer
```

Has anyone had problems with this particular sound card before? Does anyone know how to get it working again?

---

