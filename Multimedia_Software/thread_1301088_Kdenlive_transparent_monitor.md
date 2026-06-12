---
title: "Kdenlive transparent monitor"
date: 2009-10-25
forum: Multimedia Software
---

### Post by owenll on 2009-10-25
Hi, I have a problem with kdenlive that when I try to play back a clip in the monitor (project or clip monitor) it is transparent, even though when I scroll through the clip I see the frames correctly. This solution has been provided: run kdenlive from terminal with:

```
env XLIB_SKIP_ARGB_VISUALS=1 kdenlive
```

This works fine - is there anyway of making a change to any file in kdenlive so that I incorporate the above and don't have to run it through a terminal?

---

### Post by owenll on 2009-10-25
Sorry - really simple - just place that code in the launcher. :)

---

### Post by jaygo on 2009-11-06
does that have something to do with using compiz?

---

