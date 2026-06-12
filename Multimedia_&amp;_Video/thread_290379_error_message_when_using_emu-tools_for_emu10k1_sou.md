---
title: "error message when using emu-tools for emu10k1 sound card driver"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by mental_drummer on 2006-11-01
Hello everyone,
I have been stuggling trying to get icontrol to work with my sound blaster live! drive. My problem is addressed on the first questiong of the icontrol faq [http://icontrol.sourceforge.net/faq.html]("http://icontrol.sourceforge.net/faq.html")
However when I run emu-config -i i get this error
```
SOUND_MIXER_PRIVATE3: Input/output error

```
and when I run emu-dspmgr I get
```
SOUND_MIXER_PRIVATE3: You're probably using an older incompatible driver: Input/output error

```

it seems unlikely that the driver is old seeing as only just downloaded both of them.
Any help would be great
Thanks in advance

---

### Post by yabbadabbadont on 2006-11-01
Are you using sudo to run those commands?  If not, try it and see if it helps.

---

### Post by mental_drummer on 2006-11-01
just sudoed it but it gave the same error message...

---

