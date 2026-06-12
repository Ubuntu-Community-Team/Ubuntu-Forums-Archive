---
title: "How to fix totem-xine."
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by justinjstark on 2007-04-26
Totem-xine in feisty has serious problems with wmv files and some other formats.  It worked fine in edgy.

So, I figured, why not just use the version from edgy?

Add this line to your repository list.

```
deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
```

Open synaptic and do a search for xine.  Click on libxine1 and go to package->force version.  Then, select the package from the edgy repo.  Do the same with libxine-extracodecs and totem-xine.  Don't worry if it wants to remove libxine1-ffmpeg and some other things.  Those were all part of libxine-extracodecs in edgy and are not needed with the older version.

Fire up totem and there you go.  A working totem-xine.  You can play wmvs, dvds, and everything and it is rock solid.  Hooray.  :guitar: 

The only problem I have is that it keeps nagging me to update the packages.  I wish I could make it shut up.

---

### Post by WorLord on 2007-04-29
Use Synaptic to Lock the version you have.  It won't ask you to upgrade pinned packages.

---

### Post by justinjstark on 2007-04-29
> **WorLord said:**
> Use Synaptic to Lock the version you have.  It won't ask you to upgrade pinned packages.

Yep, I figured that out.  Thanks.

---

