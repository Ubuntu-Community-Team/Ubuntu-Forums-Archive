---
title: "Nvidia twinview, dual monitors, and switching one monitor to landscape/portrait"
date: 2010-07-25
forum: Multimedia Software
---

### Post by Lepy on 2010-07-25
Hi, I currently have a dual monitor setup with one 4:3 monitor and a 90 degree pivoting 16:9. I currently have two simple scripts to rotate to and from landscape and portrait modes as the need arises. 

```
#!/bin/sh

xrandr -o right

```

and

```
#!/bin/sh

xrandr -o normal
```

While in twinview these scripts rotate both monitors. I would like only the 16:9 to rotate though, no matter the performance impact. I'm sure there is a simple line missing in the script, I'm just not sure what is it. Any help? Thanks!

---

