---
title: "Sound Indicator irritant"
date: 2011-02-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-02-22
I notice that now when you use the scroll wheel over the sound indicator icon to change volume, up comes an ugly display showing the level. When you tweak your volume, you are left with this ugly thing for 10 seconds (I assume it's being put up using notify-osd). How can I either eliminate this annoying popup, and/or at least reduce the hang-time for all notify-osd popups?

I know it's possible, because there was a utility in one of the distros I've tried lately that can do it.

---

### Post by ronacc on 2011-02-22
ah but if they let you change it you would have less time to look at their wonderful innovations .:lolflag:

---

### Post by sgage on 2011-02-22
> **ronacc said:**
> ah but if they let you change it you would have less time to look at their wonderful innovations .:lolflag:

Thanks for that :KS  I don't know why, but it irritates me that there isn't an obvious preference tweak to deal with it. I was trying out some other Ubuntu-derived distro recently, and they had a menu item under accessories or system tools or some such that among other things allowed you to set the notify-osd hang-time. That's all I ask!

---

### Post by Killigrew on 2011-02-22
hi, there is a tweaked version of notify-osd out there.

[http://ppa.launchpad.net/leolik/leolik/ubuntu](http://ppa.launchpad.net/leolik/leolik/ubuntu)

The one in ubuntu doesn't allow a change of the display time...

greetings :)

---

### Post by sgage on 2011-02-22
> **Killigrew said:**
> hi, there is a tweaked version of notify-osd out there.

[http://ppa.launchpad.net/leolik/leolik/ubuntu](http://ppa.launchpad.net/leolik/leolik/ubuntu)

The one in ubuntu doesn't allow a change of the display time...

greetings :)

Oh thank you thank you thank you! I've installed it and it works a treat! You can tweak more than just the hang time - colors, size, positioning.

If anyone wants to try it, create a file in your home directory called .notify-osd, and put something like this in it:

```
slot-allocation = dynamic
bubble-expire-timeout = 10sec
bubble-vertical-gap = 10px
bubble-horizontal-gap = 10px
bubble-corner-radius = 50,5%
bubble-icon-size = 36px
bubble-gauge-size = 5px
bubble-width = 320px
bubble-background-color = e0d6ba
bubble-background-opacity = 100%
text-margin-size = 15px
text-title-size = 100%
text-title-weight = bold
text-title-color = 008000
text-title-opacity = 100%
text-body-size = 100%
text-body-weight = normal
text-body-color = 152114
text-body-opacity = 100%
text-shadow-opacity = 25%
```

I set my bubble-expire-timeout to 2 seconds. I think you need to log out and back in for it to take effect. Ah, relief! 

Thanks again Killigrew! I thought I had done due-google-diligence, but I didn't turn this up in my search.

---

