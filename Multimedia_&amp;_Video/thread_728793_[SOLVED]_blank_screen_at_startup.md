---
title: "[SOLVED] blank screen at startup?"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by darth.k on 2008-03-19
Hi.

I've just installed 7.10 on my machine. Everything went fine on the live cd. However on first boot up, it said my grfx card was not recoqnised so it ran in low grfx mode. I enabled my drivers in the restricted drivers area for the card but now when boot i just get a blank screen.

The os is working because I can hear the log in screen prompt and can enter my username and password but I can't see anything!!

I'm using an ATI Radeon X1950. I have no idea what to do here because I can't actually see anything in the destop environment, although it is running.

Please help me!

---

### Post by GrammatonCleric on 2008-03-19
Sounds like the default screen resolution may be outside what your monitor can do.  Try this...

1. Press ALT+F1. This should drop you to a command line login screen.

2. Log in.

3. Type....

```


sudo -i


```and type your password.

5. Now to reconfigure Xorg...

```


dpkg-reconfigure xserver-xorg


```follow steps selecting your graphics card and a resolution that you know that your monitor can do.

-GC

---

### Post by darth.k on 2008-03-19
Thank you very much.  This worked a treat :)

---

