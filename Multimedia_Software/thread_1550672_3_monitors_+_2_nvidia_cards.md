---
title: "3 monitors + 2 nvidia cards?"
date: 2010-08-11
forum: Multimedia Software
---

### Post by janz84 on 2010-08-11
Hi,

Is it possible to run ubuntu with 3 monitors on 2x8400gs?

What I have tried:

Installed 10.04, enabled latest nvidia drivers. Enabled and arranged each monitor as a separate x window. However, when I did this configuration I couldn't move the programs from the (primary monitor) to the ones plugged to the other 8400gs.

What I plan to use ubuntu for:

Mainly work in eclipse, firefox, and evolution. I have no interest in games since this machine is my workstation.

---

### Post by 0004tom on 2010-08-11
Off the top of my head, you;ll need to set a virtual desktop size in your XOrg.conf and disable the separate x windows, and enable twinview. I can't remember how to properly do it, as I know longer use nVidia cards.

---

### Post by janz84 on 2010-08-11
> **0004tom said:**
> Off the top of my head, you;ll need to set a virtual desktop size in your XOrg.conf and disable the separate x windows, and enable twinview. I can't remember how to properly do it, as I know longer use nVidia cards.

Wouldn't Twinview trick XWin into thinking that one monitor is connected? [I think] this only works on a per GPU basis. What I'm looking for is a way to actually have 3 independent monitors on the 2 GPUs where I can arrange my tasks as necessary. So far it's working for 1 GPU however there is some kind of block when moving tasks between monitors on the [other] GPU. 

* GPU is referencing to my 8400gs graphics processor units.

---

### Post by 0004tom on 2010-08-11
[http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

Have you seen this? 6 screens on 4 GFX cards. Using twinview and xinerama.

Is this something your trying to do?

---

### Post by janz84 on 2010-08-11
> **0004tom said:**
> [http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

Have you seen this? 6 screens on 4 GFX cards. Using twinview and xinerama.

Is this something your trying to do?

It's similar except I don't need tasks spanning across multiple displays. 

Basically something like this

Monitor 0: Maximized task A

Monitor 1: Maximized task B

Monitor 2: Maximized task C

The forum thread you mentioned is a way to make all monitors appear as one, which means they are not independent of each other. 

My monitor config is as follows:

Monitor 0: GPU 0

Monitor 1: GPU 0

Monitor 2: GPU 1

---

### Post by RTrev on 2010-08-11
The first thing I would try, which you may have already, is

```
gksudo nvidia-settings
```

You probably have it, but if not it's in the repos.

I've never had multiple display cards, but this has a reasonable chance of working and is easy to do.

---

