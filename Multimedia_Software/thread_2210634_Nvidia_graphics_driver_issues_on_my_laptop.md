---
title: "Nvidia graphics driver issues on my laptop"
date: 2014-03-11
forum: Multimedia Software
---

### Post by halfwet on 2014-03-11
Hi all,


I have dual graphics card on my laptop, nvidia gtx 765m and intel 4600hd.
I installed the latest driver from nvidia. 
But now I can't control the backlight brightness, or the resolution of the display, or use multiple displays.
What should I do with it? Thanks.


Weipeng

---

### Post by Bashing-om on 2014-03-13
halfwet; Hi !

Your graphics are an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See this link here for some background on installing the drivers: Switchable laptop graphics issues on Ubuntu 12.04?
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)
Then there is the BumbleBee open source project:
[https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee)

And alternately there is Nvidia-prime:
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

And more from open source means:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Before pursuing any of these courses, one must purge any proprietary drivers presently installed.

[INDENT][INDENT]just pass'n it on
[/INDENT][/INDENT]

---

### Post by halfwet on 2014-03-29
Thanks. I solved this by:
Install the lts-raring stack ("linux-generic-lts-raring" and "xserver-xorg-lts-raring")

---

