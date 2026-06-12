---
title: "Artifacts in Ubuntu"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by Karant on 2006-07-31
I am a previous user of Ubuntu and had just decided to reinstall it. This time everything on my system is identical as before, I just have a new video-card, BFG6600GT OC AGP8x/128MB running on the 93.31 Forceware drivers. When ubuntu loads up, it's filled with artifacts and is impossible to navigate. Why's it doing this and how do I fix it?

---

### Post by tseliot on 2006-07-31
**1) Get the Xserver to work properly:**

boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine
[B]
2) Install the Nvidia driver so as to make the most of your card:[/B]
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Use Method 1 of my guide

---

