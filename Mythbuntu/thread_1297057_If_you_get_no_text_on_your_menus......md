---
title: "If you get no text on your menus....."
date: 2009-10-21
forum: Mythbuntu
---

### Post by jakev383 on 2009-10-21
I searched around for this one for a while. I had a fresh install, and when the first mythfrontend screen came up (where you normally select your language), all I had were blue boxes. No text whatsoever. After much Googling, I came across this link:
[http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg21460.html](http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg21460.html)

That states that if you put 
```

export XLIB_SKIP_ARGB_VISUALS="1"

```

At the end of your /etc/mythtv/session-settings file, this will then allow you to see the text. At least, it worked for me. Hopefully it will help someone else, and I posted it here to hopefully save someone else all the searching to find it.
Side note: This issue is supposed to be fixed in Karmic

---

