---
title: "Nvidia config detects dual displays but Unity doesn't?"
date: 2014-07-27
forum: Multimedia Software
---

### Post by gilgongo on 2014-07-27
Using Ubuntu 14.04 with these two cards (reported by lspci):

01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
02:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 620] (rev a1)

Running Nvidia binary driver 331.38 

Nvidia settings looks like this:

[http://bayimg.com/PAPKkAaFh](http://bayimg.com/PAPKkAaFh)

But display settings looks like this:

[http://bayimg.com/AapldaafH](http://bayimg.com/AapldaafH)

And all I get on the second display is a default "X" mouse cursor.

Does anyone have any clues?

---

### Post by gilgongo on 2014-07-27
After several hours of research on this - I think the situation is hopeless.

In theory, if you check "Enable Xinerama" (would it have killed them to call this "Use both displays" or something? Sheesh), you will get twin displays. However, in practise this is broken according to this [https://wiki.archlinux.org/index.php/multihead#TwinView](https://wiki.archlinux.org/index.php/multihead#TwinView)

If you check this the thread they refer to:

[https://bbs.archlinux.org/viewtopic.php?id=163319&p=1](https://bbs.archlinux.org/viewtopic.php?id=163319&p=1)

It seems like Nvidia aren't pursuing this. 

So people: if you have two Nvidia graphics cards, and want to run two monitors, you are out of luck.

Wow. It's not as if this is an amazingly rare thing to do either...

G

---

### Post by Vladlenin5000 on 2014-07-27
> **gilgongo said:**
> if you have two Nvidia graphics cards, and want to run two monitors, you are out of luck.


Actually, if you want to run two monitors you connect them both to the same card provided it has multiple ports.
You can't run two different cards at the same time unless with nVidia's SLI or AMD's CrossFire and in that scenario you would be using the master output ONLY, ie, although the two or more SLI GPUs may share the workload the output is the same (output as in the port or ports where the monitor or monitors are connected and only one in the master card).

---

### Post by gilgongo on 2014-07-28
Ah OK. I'll try that and see what happens. Thank Chris. I mean, Vlad.

---

