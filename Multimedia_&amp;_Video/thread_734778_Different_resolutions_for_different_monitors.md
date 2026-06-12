---
title: "Different resolutions for different monitors?"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by kombucha on 2008-03-25
A fairly popular topic, it seems, but I can't seem to find a simple answer.

I have my laptop screen and an external LCD, and I only ever use one at a time. My laptop screen runs at 1440x900 and my external runs at 1680x1050. That is, those are the resolutions they'd use if the world were a happy place. I'm getting close, but I'm not quite there yet.

I'm using the "nVidia X Server Settings" tool and writing changes to xorg.conf. Right now I've got it such that I can set the resolution of the laptop to 1440x900 or the resolution of the external to 1680x1050, but whenever I change one monitor's resolution and apply the changes, the other goes along with it.

That is, if I set my external to its resolution, then the next time I Fn-F8 to my laptop it is panning at 1680x1050x. Similarly, if I set my laptop to its resolution, then when I Fn-F8 to my external it looks large and blurry.

Both monitors are configured as separate X screens, so I don't know why it's making them the same. I got one message about certain values needing to be the same, but I don't see why this is the case.

Is there any workaround? It's pretty tedious to fix each time I want to change screens.

Thanks!

---

