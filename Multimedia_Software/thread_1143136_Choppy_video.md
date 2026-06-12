---
title: "Choppy video"
date: 2009-04-29
forum: Multimedia Software
---

### Post by yoginatural on 2009-04-29
Just installed Jaunty and I gotta say "I LOVE IT"l. I have some video issues which after following one of the threads from ubuntu freak was able to fix most of them. I am still however having a problem with choppy video. I have read a couple of threads with the same issue but haven't discovered a cure for the issue. Anyone have a suggestion?

---

### Post by VMC on 2009-04-29
What's the ouput of this:
```
lspci -nn|grep VGA
```

If it's in Intel chip, there's at least three fixes

[[COLOR="Lime"]Fix#1[/COLOR]]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") (This for sure is the only fix for integreated Intel 82865G chip)

[[COLOR="Lime"]Fix#2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1130582")

[[COLOR="Lime"]Fix#3[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1136738")

---

