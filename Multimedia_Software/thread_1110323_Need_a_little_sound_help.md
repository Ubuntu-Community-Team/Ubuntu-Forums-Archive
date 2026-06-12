---
title: "Need a little sound help"
date: 2009-03-29
forum: Multimedia Software
---

### Post by gundam1965 on 2009-03-29
I just threw ubuntu 8.04 on my desktop, dual boot with vista, and I have no sound.  Been looking around and all i found was dependent on brand. My mobo is [http://www.evga.com/products/moreInfo.asp?pn=132-CK-NF78-A1](http://www.evga.com/products/moreInfo.asp?pn=132-CK-NF78-A1) .  I also have an XFI card, but i'm fairly sure that won't work(yet).  Gotta go do some homework, I'll check back later.

lspci | grep -i audio
```
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
05:09.0 Multimedia audio controller: Creative Labs SB X-Fi

```

---

### Post by Taus on 2009-03-29
hi bro,

the x-fi works in ubuntu. or at least the analog outputs does, i'm still stuck at getting S/PDIF to work. but anyways, if u want your x-fi card up and running use this guide:

[http://ubuntuforums.org/showthread.php?t=870001&highlight=xfi](http://ubuntuforums.org/showthread.php?t=870001&highlight=xfi)

i used it again last night and it still works like a charm.

cheers

---

### Post by gundam1965 on 2009-03-30
yeah, i just did that and now linux is dead.  I can't boot into linux, and recovery mode gets stuck at "loading manual drivers".  Is there a way to rollback?

---

