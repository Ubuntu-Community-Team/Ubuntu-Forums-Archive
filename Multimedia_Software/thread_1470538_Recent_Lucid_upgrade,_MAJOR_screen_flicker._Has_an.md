---
title: "Recent Lucid upgrade, MAJOR screen flicker. Has anyone else witnessed this?"
date: 2010-05-02
forum: Multimedia Software
---

### Post by vik_2010 on 2010-05-02
I upgraded to Lucid this morning - and since then I've noticed that my monitor is flickering a lot. Usually, something suddenly flashes across the length of the bottom of the screen, like a small firecracker suddenly bursting. Once, however, it lasted for about a second. It's obviously some sort of display issue.

I'm wondering if anyone else has had this issue, and if so, have they been able to solve it? Any advice would be appreciated.

---

### Post by benbeel on 2010-05-02
Also noticed that. I get what appears to be some discolored bars on the lower 1/3 of the screen. I am running 10.04 on an asus UL30A. Otherwise, Lucid runs like a champ.

---

### Post by GreatestGravity on 2010-05-03
Thirded. Dell Inspiron laptop. Not very common, but once every several minutes or so.

---

### Post by Arne Caspari on 2010-05-05
I too see this flicker with an Dell Inspiron 13z. Is there a bug report for it?

---

### Post by JS36 on 2010-05-05
Don't know if this helps but maybe worth a try.
> If you have an Intel Corporation Mobile 915GM/GMS/910GML card, your screen may flicker every 5-10 seconds. To prevent this:

    * System -> Administration -> Advanced -> Service Manager
    * Uncheck "Detect RANDR (monitor) changes" 
From [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

I haven't tried this yet but when installing the server lucid it's almost giving me epilepsy :P

---

### Post by Arne Caspari on 2010-05-05
Unfortunately, there is no System->Administration->Advanced or similar entry, at least on my Lucid installation :-(

---

### Post by Arne Caspari on 2010-05-05
This is a matching bug report. It also contains a workaround ( testing it now ): 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648)

---

