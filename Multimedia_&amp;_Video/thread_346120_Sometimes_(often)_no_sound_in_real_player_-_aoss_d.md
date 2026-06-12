---
title: "Sometimes (often) no sound in real player - aoss doesen't work as well"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by AllesMeins on 2007-01-25
Hi,

i've read some posts regarding real player sound problems. Basicly all came to the conclusion that it is fixed by using "aoss ./realplay" or adding the aoss to the realplay-start-script. What i'm getting is:

```

$ aoss ./realplay
Warning: LD_PRELOAD="/usr/$LIB/libaoss.so"
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

(realplay.bin:6108): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

```

After that i read a little more and tried adding

```

LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD

```

to the realplayer-startup-script, like it is described [here]("http://www.ubuntuforums.org/showpost.php?p=80827&postcount=48"). That removed the "Warning" but the "ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded" still remains and i still have no sound.

Other sound just works fine. I'm using the 64bit edition of edgy.

Can anybody help me?

---

