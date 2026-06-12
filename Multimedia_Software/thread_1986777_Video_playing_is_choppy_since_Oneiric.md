---
title: "Video playing is choppy since Oneiric"
date: 2012-05-25
forum: Multimedia Software
---

### Post by smartbei on 2012-05-25
Hello,
Since I upgraded to Oneiric several months ago, video playing on my machine has been choppy. I have a reletively crappy graphics card, but I could always play non-hd movies on full screen (1920x1280). Since I upgraded, it doesn't keep up anymore, and i am forced to play the videos windowed on a smaller part of the screen, where they are faster.

Upgrading to preciese didn't help the problem.

I am using VLC. System specs in sig. Any ides?

Thanks!

---

### Post by sudodus on 2012-05-25
I think that your problem is because the newer Ubuntu systems need more powerful cpu and or graphics processors.

I have a similar problem using old hardware, and I solved it running a desktop environment with lighter foot-print. Lubuntu 12.04 LTS makes my video experience even better than Ubuntu 10.04 LTS.

So I suggest that you try
- Xubuntu with XFCE (light foot-print DE)
- Lubuntu with LXDE (ultra-light foot-print DE)

You can do it either by testing from a live CD or USB drive and installing the flavour you like or install the desktop(s) into your current Ubuntu system with
```
sudo apt-get install xubuntu-desktop
``` and/or
```
sudo apt-get install lubuntu-desktop
```
and select which DE to run at the log in screen.

---

### Post by lukeiamyourfather on 2012-05-25
If you haven't already try installing the proprietary graphics drivers if they exist for your setup. They can be found in the "Hardware Drivers" or "Additional Drivers" utility that comes with Ubuntu.

---

### Post by smartbei on 2012-05-25
Thanks for the responses. Sorry - I guess i forgot to write that I am already using xubuntu. I will try lubuntu.

And yes, I am using the nvidia driver.

Thanks!

---

