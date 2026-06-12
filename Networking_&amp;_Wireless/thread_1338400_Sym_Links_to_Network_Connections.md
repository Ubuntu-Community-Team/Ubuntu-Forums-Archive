---
title: "Sym Links to Network Connections"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by justinmiller87 on 2009-11-26
Just wondering if this was possible. I tried that, and I also tried mounting it to no avail. I think I might have missed a step on the latter however. The tutorial I was trying to follow was a bit confusing.

---

### Post by solar george on 2009-11-26
Not possible i'm afraid unless you mount the network share first (you are talking about shared folders aren't you).
What kind of shares were you trying to mount?

---

### Post by justinmiller87 on 2009-11-26
> **solar george said:**
> Not possible i'm afraid unless you mount the network share first (you are talking about shared folders aren't you).
What kind of shares were you trying to mount?

I have a Windows shared network called Millers and the PC with the shared data is called tv-pc so I would have thought going to //Millers/tv-pc/ would have worked, but when I tried to mount it, it couldn't find it.

---

### Post by solar george on 2009-11-26
> I have a Windows shared network called Millers and the PC with the shared data is called tv-pc so I would have thought going to //Millers/tv-pc/ would have worked, but when I tried to mount it, it couldn't find it.

Yeah, tis a bit more complicated than that, you see gnome(/kde) hides the difference between local and remote directories, the downside of which is that and network shared mounted in gnome are unavailable to command line apps.

For windows shares (smb) you can try installing [apt://fusesmb]("apt://fusesmb") which should allow you to browse all network shares by directing and file browser to its mount point.
```
fusesmb *path/to/mountpoint*
```

---

### Post by justinmiller87 on 2009-11-26
I was actually able to mount it by its ip address, so I was able to do it at least. Would have been nice if I didn't have to look up though.

---

### Post by solar george on 2009-11-26
fusesmb should let you do that (i don't use any smb machines myself tho so can't say how well it works).

---

