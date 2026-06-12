---
title: "How do I set a default audio volume above 100%?"
date: 2011-04-25
forum: Multimedia Software
---

### Post by OneSeventeen on 2011-04-25
When I go into Sound Preferences I can crank up the output volume above 100%, making it audible from my monitor's built in speakers.  (this is for a kiosk that doesn't have room for extra powered speakers)

Every time I reboot it resets output volume to 100%.

Is there a way to change the volume back to 125% or whatever max is so the general public can hear the video that is played after a reboot?  (this is to be a permanent installation that won't even have a keyboard or mouse attached, so automating this is a must)

Thanks in advance, I'm sure this is user error but I'd love to learn how to script around it.

---

### Post by OneSeventeen on 2011-04-26
The command line method is to type:
```
pacmd set-sink-volume 0 100000
pacmd set-sink-volume 0 100000
```

Typing this via command line after everything has started works great.  typing this in Startup Applications or rc.local has no effect.

I'm also at a loss as to where in /etc/pulse/ I could set default volumes.  Surely I can't be the only one who wants 150% volume as default?

---

### Post by lidex on 2011-04-27
I think it (pulse) should be restoring your volume levels on restart but if it has stored the wrong values, you need to reset.
```

rm -r ~/.pulse ~/.pulse-cookie 

```
Now set your levels and
**Reboot**

---

