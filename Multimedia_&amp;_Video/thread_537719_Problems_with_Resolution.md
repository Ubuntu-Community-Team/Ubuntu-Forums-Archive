---
title: "Problems with Resolution"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by DocHolliday2006 on 2007-08-29
Hi. I've got a dell flat screen monitor (don't have the model number on hand). Under windows, it always was able to have high resolutions, but it seems to be stuck at 1024 x 768 or lower in Ubuntu. I have Nvidia drivers installed. The Screen Res screen will not let me set it higher. Anyone know how I could make it higher?

Thanks.

---

### Post by renzokuken on 2007-08-29
run

```
sudo dpkg-reconfigure xserver-xorg
```

and run through all the screens selecting everything as default till you get to the resolutions sections, add in any new res' you want and continue on keeping the defaults for everything else.

restart X and see if it allows your new resoltuions

---

### Post by DocHolliday2006 on 2007-08-29
> **renzokuken said:**
> run

```
sudo dpkg-reconfigure xserver-xorg
```

and run through all the screens selecting everything as default till you get to the resolutions sections, add in any new res' you want and continue on keeping the defaults for everything else.

restart X and see if it allows your new resoltuions

When I do that The GUI will not load. It tells me there is an error and it brings me to some text based console. 

Any other ways to do it? Drivers?

---

