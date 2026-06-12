---
title: "nVidia GTS250 running hot - can't change fan speed."
date: 2010-06-28
forum: Multimedia Software
---

### Post by jantz on 2010-06-28
Hey guys,

Was wondering if anyone (i'm sure someone has the same problem :) has found a solution to this.
I'm running a XFX Nvidia GTS 250 512MB card. I have installed Ubuntu 10.04 and so far I'm loving it - apart from one small issue.  Using 195.36.24 drivers, I cannot control the fan speed - it keeps running the card pretty hot - hitting 75 deg. C when one OpenGL game is running. The fan barely goes over 60% speed - I'd rather have it run at 80% constantly to keep the temps under control. 

There are drivers on nvidia website which "seem" to be a lot newer : 256.35 (using 64bit Linux) - are those "direct replacement" for the 195.36 which Ubuntu installs by default?

I have a well ventilated case (1x120mm pulling air, 1x120mm pushing out, neat cabling, etc).
I have found nvclock but no joy - even with -force it doesn't want to change fan speed.

Any other suggestions ?

John

---

### Post by Dugger5688 on 2010-06-28
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Try that repository, it should provide the newest drivers and they're working beautifully for me. I had some issues with the 195.x as well (like the slowdown threshold being at 255 C).

To add the repo do: 

```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

```

Good luck!

---

### Post by jantz on 2010-06-28
Hey,

thanks for that info. I've found information about adding that repository and indeed, now I'm running 256.35. Card still running hot and there is no option for slowdown threshold :(

Also no option for changing / forcing fan speed.

---

### Post by mattman on 2010-06-29
I'm having the same problem with the same card. I even tried compiling nvclock from source, but fan control is not yet supported from this card. I have found that if I set the card to run in adaptive mode in nvidia-settings that it runs about 5 degrees cooler when idling.

---

