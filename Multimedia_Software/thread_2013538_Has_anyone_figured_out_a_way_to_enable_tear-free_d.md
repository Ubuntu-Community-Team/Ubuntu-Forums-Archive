---
title: "Has anyone figured out a way to enable tear-free desktop on hybrid setup?"
date: 2012-07-01
forum: Multimedia Software
---

### Post by framebuffer on 2012-07-01
Hi!

On non-hybrid AMD cards on Catalyst 11.5, there use to be an option called "Tear-free desktop".

On catalyst 12.6 / Ubuntu 12.04, on Intel HD3000 / AMD 6630M on laptops, this option is nowhere to be found. (Display -> Tear-free desktop)

If you try to set tear free desktop to 1 using command line, the desktop doesnt show and you have to re-initialize the aticonfig using terminal to get the desktop back.

aticonfig --set-pcs-u32=DDX,EnableTearFreeDesktop,1 (This doesnt work)

Has anyone figured out a way to enable tear-free desktop on hybrid setup?

I have set sync to vblank in on in compiz. The refresh rate has been set to 60

It is unbelieveable that after all these years the problem still comes and goes. (I am not blaming Linux, the driver manufacturers)

I remember struggling with it forever:

[http://ubuntuforums.org/showthread.php?t=1780525](http://ubuntuforums.org/showthread.php?t=1780525)

The only thing preventimg me from using linux. I try it every 6 months, and sometimes it there, something its not. This is really frustrating.

---

### Post by Kreaninw on 2012-07-02
After installed ATI/AMD driver from system > additional drivers. AMD CCC should work fine, no command line needed. It's there in AMD CCC.

---

### Post by framebuffer on 2012-07-03
I have switchable graphics.

One gpu is Intel HD 3000 and AMD 6630M HD (This is a very common configuration)

As you can see, there is no display option. Tearing is relatively less on Intel, but its still there. 

On dedicated, its obvios. Anything that moves like Google earth, Movies etc tears.

---

### Post by yochaigal on 2012-07-09
I have the same problem ATI 672G2 on an ASUS A53T, running Ubuntu 12.04 using propriatary graphics.

---

### Post by apochry on 2012-08-21
I have the same hardware (Intel HD 3000 and AMD 6630M HD) and I couldn&#8217;t find a solution for this issue (and I was digging a lot). The open source drivers are not an option too, because they make the laptop's fan run as crazy. 
At the end I gave up and I'm living with tearing... It's really sad how hardware manufacturers simply don't care about Linux users.

---

### Post by ScottDeagan on 2012-10-08
I agree with the general feeling here. All these "little issues" add up and deter many people from adopting Linux as their primary desktop OS. Don't get me wrong, Linux is great and all that, but when very common use-cases (such as perfect dual monitor support - something considered "the norm" in this day and age) don't exist, it forces people into using other options (i.e. other OSes).

I use Ubuntu 12.04 at home and in the office, and I've never seen the perfect dual-monitor setup where both monitors haven't been identical. For some reason, on Linux it's not possible to vsync on monitors that are different (i.e. 59.85Hz and 59.95Hz). I have found that this seems to hold true for both AMD and nVidia hardware. In all cases where I've managed to get dual-monitors working in the first place, there's always this slow tearing on the secondary monitor that moves from the top slowly to the bottom. It's a little strange that the exact same problem manifests on both AMD and nVidia hardware (using the proprietary drivers).

I guess our options are:

1. Start some kind of donation scheme so that someone in the know can resolve this issue (the folks producing these proprietary drivers).

2. Learn to live with tearing if we want dual monitor support (as apochry has done).

3. Don't use dual-monitors in Linux.

4. Use another OS.

5. Wait for Wayland: [http://www.phoronix.com/scan.php?page=news_item&px=MTE3MTU](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MTU)

---

