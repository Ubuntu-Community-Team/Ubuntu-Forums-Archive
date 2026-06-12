---
title: "Force Tv-out detection Nvidia in Feisty"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by robbymaumau on 2007-04-16
Hey, im a bit of a beginner, but have been using Ubuntu for a year.

We have a HTPC in our apartment with a Geforce FX5500 card.  

I got the Nvidia drivers working fine with Feisty 7.04, but our tv is fairly old, and only has composite in.

There doesnt seem to be a Force TV detection feature in the nvidia-settings utility.

Does anyone know how i can force the detection of our tv? 

I tried one method explaining to change a setting in xorg.conf, but every time I try to open 

etc/x11/xorg.conf  a text editor opens but it is completely blank.

Help please!

---

### Post by SishGupta on 2007-04-16
> **robbymaumau said:**
> Hey, im a bit of a beginner, but have been using Ubuntu for a year.

We have a HTPC in our apartment with a Geforce FX5500 card.  

I got the Nvidia drivers working fine with Feisty 7.04, but our tv is fairly old, and only has composite in.

There doesnt seem to be a Force TV detection feature in the nvidia-settings utility.

Does anyone know how i can force the detection of our tv? 

I tried one method explaining to change a setting in xorg.conf, but every time I try to open 

etc/x11/xorg.conf  a text editor opens but it is completely blank.

Help please!

The reason xorg.conf blank is because you aren't actually opening it.

In linux filenames are case-sensitive. The actual file path is
```

/etc/X11/xorg.conf

```

As for forcing detection, open up nvidia-settings and on the "X server display configuration" page there should be a button at the bottom that says "detect displays"

Composite should detect automatically, odd that it doesn't. If forcing detection doesn't work check the cable (even again), and make sure the tv is on.

---

