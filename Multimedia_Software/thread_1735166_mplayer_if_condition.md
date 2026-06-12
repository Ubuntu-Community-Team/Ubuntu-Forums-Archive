---
title: "mplayer if condition"
date: 2011-04-21
forum: Multimedia Software
---

### Post by denbeigh2000 on 2011-04-21
Hello,

I use mplayer for a variety of content, and I wish to use an equalizer for music only, and to change it according to bitrate.

Is there an "if" option in the ~/.mplayer/config that would allow me to do this?

For example:
```

if (bitrate > 256){
[INDENT]af=equalizer=(SOMEEQ)[/INDENT]
}

else (some other condition) {
[INDENT]af=equalizer=(SOMEOTHEREQ)[/INDENT]
}

```

---

