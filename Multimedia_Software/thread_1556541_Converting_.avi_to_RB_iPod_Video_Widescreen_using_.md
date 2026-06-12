---
title: "Converting .avi to RB iPod Video Widescreen using ffmpeg and winff"
date: 2010-08-19
forum: Multimedia Software
---

### Post by jackbuntu-common on 2010-08-19
Every time I try to convert an AVI video to "RB iPod Video Widescreen" video using winff, this is what I get: 

```
[NULL @ 0xa8343e0] [Eval @ 0xbfc3c1ac] Invalid chars 'b' at the end of expression '128kb'
[NULL @ 0xa8343e0] Unable to parse option value "128kb"
Invalid value '128kb' for option 'ab'

```

How do I fix this, or is there another way to convert AVI to an iPod-compatible format?

Thanks in advance,
Jack

---

### Post by ron999 on 2010-08-19
Hi
The commands have changed with newer versions of ffmpeg.
Instead of saying **kb** we now use just **k**.

Back up your **presets.xml** file that's in the **.winff** folder.
(Save it as presets_old.xml).
Then download a new presets file from this guy here:-[http://www.biggmatt.com/forums/index.php?topic=859.0]("http://www.biggmatt.com/forums/index.php?topic=859.0")

---

### Post by jackbuntu-common on 2010-08-19
> **ron999 said:**
> Hi
The commands have changed with newer versions of ffmpeg.
Instead of saying **kb** we now use just **k**.

Back up your **presets.xml** file that's in the **.winff** folder.
(Save it as presets_old.xml).
Then download a new presets file from this guy here:-[http://www.biggmatt.com/forums/index.php?topic=859.0](http://www.biggmatt.com/forums/index.php?topic=859.0)

Where is the .winff folder?

---

### Post by jackbuntu-common on 2010-08-19
> **jackbuntu-common said:**
> Where is the .winff folder?

Never mind. I found it.

---

