---
title: "Toshiba U845W/U800W screen scrambled"
date: 2012-11-11
forum: Multimedia Software
---

### Post by fixture on 2012-11-11
Have recently come into the possession of a Toshiba U845W/U800W laptop. This wouldn't be my first choice on laptops, but wtf it is free. I jumped through a bunch of hoops to delete windows and the software raid, but only to find the screen completely scrambled in ubuntu.

I am a somewhat seasoned ubuntu user. Tried to insert a new mode through xrandr, and tried to install the bleeding edge intel drivers through the xorg-video crack pusher ppa. But these efforts don't seem to fix the problem. Any help here? I am not that well versed in X11, so my attempt at inserting the new mode with xrandr might be wrong. So, I am open to suggestions. Thanks,

---

### Post by fixture on 2012-11-21
Please see a Fedora bug, this seems to be a kernel issue

[https://bugzilla.redhat.com/show_bug.cgi?id=868729](https://bugzilla.redhat.com/show_bug.cgi?id=868729)

---

### Post by fixture on 2012-11-22
In fact, I rolled back to Ubuntu 12.04.1, it worked out of the box with kernel 3.2.0-29, but when I did an apt-get dist-upgrade the kernel got updated to 3.2.0-33, and it's all scrambled again. If I choose to boot 3.2.0-29, it still all works. So, it's definitely in the kernel.

---

### Post by tg2018 on 2012-11-24
> **fixture said:**
> In fact, I rolled back to Ubuntu 12.04.1, it worked out of the box with kernel 3.2.0-29, but when I did an apt-get dist-upgrade the kernel got updated to 3.2.0-33, and it's all scrambled again. If I choose to boot 3.2.0-29, it still all works. So, it's definitely in the kernel.




hey, i think it's the kernel's bug. I tried kernel 3.5.2 & 3.5.N (n > 2) & 3.6.*, all work out of box except 3.5.2. finally, i tried 3.7.rc6, and it works again.


so i suggest you compile the 3.7 kernel by yourself, or use the old one.



btw, i'm using the toshiba u800w too, and meet some issues:

1. Some Fn key not working (brightness, lcd switch, touchpad onoff, wireless onoff)
2. ath9k wlan break easily(phy0: Unable to reset channel, reset status -22): i found many in the internet about this issue, some says it's fix in the new kernel, but i still have the issue using the 3.7.rc6

---

### Post by linuxslate on 2013-01-25
I know you don't "Vote" for bugs here, but I also have one of these (Toshiba u845W), and I have exactly the same problem.

12.04 install went fine (momentary problem getting the SSD and HDD set up the way I wanted).

1st update got me to the 3.2.0.36.43 kernel, and .... Screen distortion.

I have just been picking the old kernel (...0.29, I believe), in GRUB every time I boot, and it is fine.

I didn't get my u845w for free, but I got an open box for less than 1/2 price.

I like the machine.  Everything works fine (12.04 is the only OS on it), and I like the ultra wide screen.

Not only that, but when it dies, I'm going to bolt some wheels to it, and I'll have a cool skateboard.

---

### Post by macintuxman on 2013-02-15
I see that kernel 3.2.0-37 is out now. I just got one of these laptops recently and saw the posts, so I did not upgrade the kernel. Was just curious if this issue was fixed yet. Everything else seems to be working great.

---

### Post by Javier Martinez on 2013-07-14
> **fixture said:**
> Have recently come into the possession of a Toshiba U845W/U800W laptop. This wouldn't be my first choice on laptops, but wtf it is free. I jumped through a bunch of hoops to delete windows and the software raid, but only to find the screen completely scrambled in ubuntu.

I am a somewhat seasoned ubuntu user. Tried to insert a new mode through xrandr, and tried to install the bleeding edge intel drivers through the xorg-video crack pusher ppa. But these efforts don't seem to fix the problem. Any help here? I am not that well versed in X11, so my attempt at inserting the new mode with xrandr might be wrong. So, I am open to suggestions. Thanks,



Man, can you tell me how do you install ubuntu in the u845w?? I want to keep the both OS (W7 & Ubuntu 13.04) in the laptop... but with an usb with ubuntu they don't recognize any HDD on it to install, Can yu tell me how put ubuntu in the laptop??

---

