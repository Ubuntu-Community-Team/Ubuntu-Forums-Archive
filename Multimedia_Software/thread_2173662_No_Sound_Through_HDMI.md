---
title: "No Sound Through HDMI"
date: 2013-09-10
forum: Multimedia Software
---

### Post by Medic82 on 2013-09-10
So it have come to this and I have to suck up my pride and ask for help.

I am at the moment running Ubuntu 12.04 LTS on a USB stick and I want to install it on my HD. But I have the well known problem of no sound through my HDMI and that is a big issue for me since I have hocked my computer (Asus K51A) to my TV to use with Netflix. I have tried the solution in the second post [http://ubuntuforums.org/showthread.php?t=2141858](http://ubuntuforums.org/showthread.php?t=2141858) and some other solutions that I have come over but nothing helps and there is still no sound through HDMI.

Now, can one of the problems be that I am running Ubuntu in a USB stick? Is there a chance that the problem will be solved once installed on my HD? Does anyone have a solution for me or is this a lost cause? I am a big n00b when coming to Ubuntu so I need help.

---

### Post by Toz on 2013-09-10
Hello and welcome to the forums.

I've changed the title of your thread to make it more descriptive of the problem you are having. Hopefully this will better attract the people with knowledge of HDMI and sound to your aid.

---

### Post by Medic82 on 2013-09-13
Nobody can help me with this?

---

### Post by Bucky Ball on 2013-09-13
*Thread moved to **Multimedia & Video**.*

And the move might help.

---

### Post by pqwoerituytrueiwoq on 2013-09-13
open a terminal run [FONT=courier new]alsamizer[/FONT] and make sure hdmi is not muted
you may lean something from this old thread of mine
[http://ubuntuforums.org/showthread.php?t=1926721](http://ubuntuforums.org/showthread.php?t=1926721)

---

### Post by Yellow Pasque on 2013-09-14
If it's an AMD/ATI GPU, then "workaround 1" should fix you: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)
(Don't attempt "workaround 2" by yourself. fglrx/Catalyst may not work depending on what kernel/X you'rs using.)

EDIT: The command in the previous post should be:
```
alsamixer
```

---

