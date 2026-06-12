---
title: "++ poor video &amp; texture quality, please help! ++"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by Che.SSL on 2008-03-07
Hello friends,

I have a serious problem with videos and moving graphics: any movement on my desktop from left to right (or the opposite way) causes very annoying distortions.
Here's a [Screenshot]("http://img212.imageshack.us/my.php?image=screenshotcp1.png").

This happens when I move a window horizontally. Vertical movements are ok.

I have the same effect while watching videos, which is quite disturbing and killing my eyes! I have found some other people with the same problem, but it seems there's no solution at all.

So here is some information about this issue:
I'm running Ubuntu 7.10 on a laptop with 2 GB RAM, a 2.0 GHz Dual Core and a 8400M GS Nvidia.
Gnome desktop, latest Nvidia driver through envy, compiz-fusion (compiz core 0.6.2), X11.

All compiz-fusion desktop effects are running correctly.

I have tried the restricted driver (Nvidia) which came out-of-the-box, too, but same problem.
Turning off compiz (3d desktop effect) results in a lower distortion, but the problem persists defintively. So that doesn't help either.
I've tried installing XGL, no improvment.
Edited nvidia-settings (with sudo & reboot, overriding anti-aliasing, etc), no improvement.

I suppose that it is no Nvidia driver problem, nor a compiz thing. But what else can it be?

I have the same problem on my 2nd laptop with an Intel GMA950 chipset.... makes me wondering, is that a bug of Ubuntu or even Linux at all?

I really love Ubuntu, but that graphic problem is killing me - I'm considering to reinstall Windows (even if I'd hate it), but if that's the only way to get graphics & videos look the way they are supposed to do, I will go that way.

However, I would really appreciate getting some help of you guys, so we could figure out this thing... and I could stay with Ubuntu =)

Thanks.

---

### Post by davarino on 2008-03-08
Two possible solutions:

Is your refresh rate set properly? This possibly can be changed in System > Preferences > Screen Resolution. Notice that your "bands" are equal depth.

Another possibility is that Ubuntu 7.10 is not compatible with your computer. Many people have had better luck with 7.04 and with 6.06LTS. A good way to test for this is to test for the same lousy video quality using the 7.10 Desktop disk as a Live CD. If it happens with Live CD, I'd look at another version's Live CD to see if the problem persists.

Good luck. With persistence, I am sure that you'll come to a solution to this problem.

---

### Post by steefjeqv on 2008-03-08
Hi,

If you're using the closed Nvidia driver you can try the following :

- in terminal : sudo nvidia-settings

In the menu "Xserver Xvideo settings", try changing the "Sync to Vblank" settings.

Greetings,
Steven

---

