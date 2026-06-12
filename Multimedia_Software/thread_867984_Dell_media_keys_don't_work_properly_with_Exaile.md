---
title: "Dell media keys don't work properly with Exaile"
date: 2008-07-23
forum: Multimedia Software
---

### Post by phenest on 2008-07-23
I just had to do a fresh install of Hardy (another story), and in doing so re-installed all my favourite software. For some reason, Exaile does not respond to the XF86AudioPrev button.

I have a Dell Precision M90 laptop and this was not an issue before I did the fresh install. The Ubuntu install before, was a standard install, as is this one.

Play/Pause, Stop, Next, all work except for Previous. Any ideas?

EDIT: I can use the Previous button to lower the volume in Gnome (or any other funtion), so it appears Exaile is ignoring it.

EDIT 2: In fact, I can use any other key combination *except* for XF86AudioPrev.

---

### Post by MyR on 2008-07-23
i'd report a bug in launchpad. i didn't see any regarding this issue.

[https://bugs.launchpad.net/exaile](https://bugs.launchpad.net/exaile)

peace

---

### Post by phenest on 2008-07-23
I think the issue might be with Gnome rather than Exaile. If I configure the keys in Exaile, they work. But if I configure them in Gnome through the Keyboard Shortcuts applet, XF86AudioPrev refuses to work.

I will file a bug.

---

### Post by phenest on 2008-07-23
Bug reported: [bug 251305]("https://bugs.launchpad.net/chromadesk/+bug/251305")

---

