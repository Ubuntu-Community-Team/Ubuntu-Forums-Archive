---
title: "nVidia NV15DDR [Geforce2 Ti] - Gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by aonrotar on 2007-10-19
Hello,

I recently upgraded from Feisty to Gutsy. In Feisty, my video card worked perfectly fine, with the correct resolution and so on.

However, after the upgrade, I've had a plethora of problems relating to (I think) the detection of my video card. When I boot up Gutsy, it starts failing at the USplash, where at this point an error message pops up on my screen saying:

```

OUT of Range

H: 63.9 KHz
V: 60.4 Hz
Max: 1024 X768

```

After waiting about a minute, the monitor flashes and Ubuntu goes into low-graphics mode.

I asked around on IRC, and I was told to edit my xorg.conf file. I did as asked, booted up into recovery mode, and I keyed in the correct refresh rates (V: 55-75Hz, H: 30-60kHZ, ProLite E380S monitor).

I rebooted, but to my disappointment it did not work.

Including this, I was told to install nvidia-glx-legacy drivers as opposed to nvidia-glx. Again, it didn't work.

My final resort was to boot up into recovery mode again and do sudo dpkg-reconfigure xserver-xorg, again it didn't work.

(By "it didn't work", I mean that the same error message popped up before).

So, is there any way for me to get it working? Or am I just unlucky to have a video card that doesn't work?

Thanks,

Haz.

---

