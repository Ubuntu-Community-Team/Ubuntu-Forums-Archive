---
title: "determining what display resolution my computer will support"
date: 2012-07-06
forum: Multimedia Software
---

### Post by danh-h on 2012-07-06
I'm thinking about getting a different monitor for my computer, perhaps 1920-by-1080.

However, perhaps my hardware won't support it (a few years ago, i did something like that and had to get a special card to drive the monitor).

So this time, i'd like to determine whether i need a different card before i get the monitor.

But how do you determine what display resolutions your computer can support?

I've ran xrandr, and sudo lshw -c video, and lspci | grep -i vga, and looked through my xorg.conf.d directory (after searching around to find it).   For me, the first line of xrandr says:
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192

But i don't know how to interpret that maximum number 8192 x 8192 (surely it doesn't mean that anything less than 8192 x 8192 will work).

I've also looked at
[https://wiki.ubuntu.com/X/Config/Resolution/](https://wiki.ubuntu.com/X/Config/Resolution/)
but i get the impression that that document mainly addresses what to do when you already have your monitor.  (???)

Thanks in advance for any pointers, especially any corrections where i just don't get the point.

dan

---

### Post by Cheesemill on 2012-07-06
What graphics card do you have?

---

### Post by danh-h on 2012-07-06
Hi Cheesemill,

It has onboard graphics (Radeon HD 3000, product RS780L, from Hynix [Hyundai]) according to sudo lshw -c video.

In fact, the complete specs for the computer are at
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883109058](http://www.newegg.com/Product/Product.aspx?Item=N82E16883109058)

It's a Compaq Presario CQ5720F PC, and the specs on that page seem to be right (except that i put in a different harddrive, and of course loaded ubuntu on it).

dan

---

