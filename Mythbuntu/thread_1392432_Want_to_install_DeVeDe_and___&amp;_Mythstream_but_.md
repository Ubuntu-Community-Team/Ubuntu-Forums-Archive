---
title: "Want to install DeVeDe and   &amp; Mythstream but afraid of breaking mythbuntu"
date: 2010-01-28
forum: Mythbuntu
---

### Post by ubnewbie2 on 2010-01-28
I tried to install DeVeDe using synaptic, but the list of things it is going to remove, and install, looks a bit worrying.

For example, it is proposing to remove

```
libavcodec52
libavformat52
libavutil49
libpostproc51
libswscale0
```

and install many things, some of which are

```
libavcodec-extra-52
libavformat-extra-52

mplayer-nogui
mencoder
```

As for mythstream, it seemed to be proposing to uninstall ALL the other mythtv plugins already on the computer (and not putting them back either)!  

What's the chance of mythtv (mythbuntu 9.10) being broken by installing some things like this?

---

### Post by ubnewbie2 on 2010-01-30
Nobody has any experience installing extra stuff into mythbuntu using synaptic and knows if it is likely to break?

---

### Post by superm1 on 2010-01-31
mythstream is not gonna work.  Doesn't support 0.22 in the archive.

---

### Post by azmyth on 2010-01-31
The mythstream you see is for .21 so if you try to install it'll remove your 0.22 install. You can actually compile mythstream and make it work for 0.22. I use it for Shoutcast which works so I can't comment on if the video parts work.

---

### Post by ubnewbie2 on 2010-01-31
> **azmyth said:**
> The mythstream you see is for .21 so if you try to install it'll remove your 0.22 install. You can actually compile mythstream and make it work for 0.22. I use it for Shoutcast which works so I can't comment on if the video parts work.

I wasn't aware that parts of the old mythtv have been left behind with the version in the latest mythbuntu.  Thanks for the info.

DeVeDe otoh is a separate program.  Will it break mythbuntu 9.10 ?

---

### Post by superm1 on 2010-01-31
> **ubnewbie2 said:**
> I wasn't aware that parts of the old mythtv have been left behind with the version in the latest mythbuntu.  Thanks for the info.

DeVeDe otoh is a separate program.  Will it break mythbuntu 9.10 ?

mythstream was never part of the official mythtv distribution.  At the time the archive froze, it wasn't 0.22 compatible.

As for Devede, you can try it and see what happens.  Worst comes to worst, you just need to reinstall any packages that were removed.

---

### Post by ubnewbie2 on 2010-01-31
> **superm1 said:**
> 
As for Devede, you can try it and see what happens.  Worst comes to worst, you just need to reinstall any packages that were removed.

OK thanks.  If that's all I will need to do, then I might try it.

---

