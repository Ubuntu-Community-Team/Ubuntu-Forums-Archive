---
title: "ATI Drivers Flicker, Freeze and Overheat System"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Day Tripper on 2008-11-04
Hi all,

Recently switched to 8.10 -- So far so good.

-However:

Upon installing the ATI/AMD proprietary FLGLRX graphics driver I began to notice some detrimental effects.

1: When playing video or 3D applications (Google Earth, Screensavers etc) the image flickers violently -- Turning off Compiz (Normal effects) seems to resolve this issue.
2: My system regularly overheats.
3: My system (perhaps as a result of 2) crashes again, again and again during moments of heavy processing -- sometimes even just randomly.

Please, if you could offer any advice as to how I might solve this issues I would be ENORMOUSLY grateful. I do not plan to return to Vista; however, if these problems persist, I may have no choice.

ATI Radeon X1900
Intel Core2 @ 1.8ghz
2GB DDR2

Many thanks!

---

### Post by Day Tripper on 2008-11-05
Bump

---

### Post by krazyd on 2008-11-05
I'm not sure what the crashing/overheating issue is about, but your graphics card is supported by the open-source radeon driver. This driver works much better than fglrx especially for video (though it is a bit slower for 3d). It should be enabled automatically on installing ubuntu.

---

### Post by Day Tripper on 2008-11-06
The open source drivers are pretty slow.

Scrolling down pages is jittery and makes everything other application (eg. music) stutter.

Also, whenever I try to play videos without the fglrx drivers, the player (Totem as well as VLC) just closes immediately.

Is Envy worth a shot?

Please, anybody who knows ANYTHING on the matter, post your suggestions. I'm desperate for advice.

Thanks!

---

### Post by krazyd on 2008-11-06
ah yes the open source drivers need ```
Option "AccelMethod" "exa"
``` added to the device section of your xorg.conf for video to work properly.

---

