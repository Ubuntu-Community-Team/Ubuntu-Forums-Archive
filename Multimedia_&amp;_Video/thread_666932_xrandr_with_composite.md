---
title: "xrandr with composite"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by Mateo on 2008-01-13
i read that xrandr is supposed to support tv-out with s-video and composite, but i can't find any instructions for using it with composite.  any ideas how it works?  I try this:

```
xrandr --addmode Composite 800x600
```

but then it says:

```
xrandr: cannot find output "Composite"
```

any help would be appreciated.

---

### Post by agent8131 on 2008-05-24
Did you ever have any luck with this.  I tried:

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

But got nothing.

---

