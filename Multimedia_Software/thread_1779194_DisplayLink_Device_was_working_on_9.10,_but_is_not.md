---
title: "DisplayLink Device was working on 9.10, but is not on 11.04"
date: 2011-06-10
forum: Multimedia Software
---

### Post by xaej806 on 2011-06-10
Hello, as my title suggests, I have recently upgraded from Ubuntu 9.10 up to 11.04. 

While using 9.10 I, through much trial and difficulty, successfully got my DisplayLink USB device working, establishing dual monitor goodness. 

Problem, however, was that the two monitors existed entirely separately of one another with no interaction between the two being allowed whatsoever (no windows being moved between each other and things like that). I could move the cursor between the two, but that was it. Through my web crawling, I have established a belief that this has something to do with the lack of "Xinerama" functionality available, though I'm hardly an expert.

It was my hope that, if I upgraded my Ubuntu version, I may have more luck in locating a fix for this problem. Instead, and entirely contrary to my purpose, what I know have is my DisplayLink monitor returning "Not Support!" as its message on-screen, no longer even establishing the much-famed "Green Screen", much less actually working.

I'm using the exact same /etc/X11/xorg.conf file that I was using in my 9.10 version, so I'm not sure what the problem is. My one thought is that, during the upgrade process, ubuntu seems to have created other xorg.conf files in the X11 folder as well, titled "xorg.conf.dist-upgrade-201106091937", "xorg.conf.dist-upgrade-201106100052", and "xorg.conf.dist-upgrade201106100240"

Any insight as to whether the problem preventing my previous basic functionality of the DisplayLink device is these extra "dist-upgrade" configuration files or something else?

Thanks for taking the time to read my post, and thanks in advance for any potential help you give!

---

