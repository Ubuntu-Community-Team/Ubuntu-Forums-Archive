---
title: "Abit KV7 Surround Sound (Vt8235/8237)"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by mystro on 2006-06-07
Hello, 

I am using the onboard sound controller (6 channel max) with my 4 channel speakers. This setup has worked for me for the past ~6 months in Windows and having taken the plunge (yet again ;-)) to Linux I've been in the process of setting up sound again, however without much luck.

Currently, only the front left speaker plays any sound through any music player. This corresponds with the sound test I ran through
```

speaker-test surround51 -c4

```
Where only the front left speaker gave me any noise... 

The 
```

lspci -v

``` command produces the following output:

```

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ABIT Computer Corp.: Unknown device 141d
        Flags: medium devsel, IRQ 193
        I/O ports at eb00 [size=256]
        Capabilities: [c0] Power Management version 2

```

Any help would be greatly appreciated :-)

Cheers,

Mystro.

---

### Post by mystro on 2006-06-07
bump?

---

