---
title: "Linux 2.6.38 vs. 2.6.39-rc5"
date: 2011-04-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by amauk on 2011-04-27
Just thought I'd post here regarding performance problems I've been having with Linux 2.6.38 under Natty

System:
- Intel core2 Duo (dual core)
- 4 GB RAM
- Nvidia GeForce 9500 GT

Symptoms:
- Programs that hit the disk a lot stalling for multiple seconds (compiz dimmed) then coming back
- Very choppy (slideshow) Hi-def video
- General sluggishness of UI

Compiled Linux 2.6.39-rc5, just to test
and all these issues are gone

I'm going to post to one of the ubuntu mailing lists, and hopefully whatever has changed in .39 to solve these performance issues can be cherrypicked into the natty .38 kernel
But thought I'd post here as well

Can anyone else with performance issues confirm that .39 is a vast improvement?

---

### Post by Harry33 on 2011-04-27
Well I haven't experienced those issues with my Nvidia setup:

Gigabyte GA-MA790XT-UD4-P (AM3)
AMD Phenom II 955 X4 Black Edition (4 x 3,2 GHz)
4 GB RAM Kingston HyperX DDR3 (1600 MHz)
Nvidia GTX285 (1Gb)

I use Ubuntu kernel 2.6.38-8 and nvidia-current_270.41.06 driver.

---

### Post by amauk on 2011-04-27
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2011-April/012598.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2011-April/012598.html)

---

### Post by KegHead on 2011-04-27
Hi!

When I was on the bleeding edge of kernels I had huge video problems.

Now I stay a few back.

KegHead

---

