---
title: "Resolution correct, but only showing half of the desktop"
date: 2008-08-11
forum: Multimedia Software
---

### Post by gggerard on 2008-08-11
Hi there,

I have two displays connected on my ubuntu 8.04. The first has a 1280x1024 resolution. The second is a plasma with a resolution of 1280x720. This is the native resolution of the display and this is what ubuntu 8.04 has detected for it with the provided tool (it has a native 1024x768 resolution, but from what I've read, in plasma the pixels are not squared, so it is like a squared 1280x720 resolution).

When I use this 1280x720 resolution with WinXP, the whole desktop is observed in the panasonic. However, in ubuntu I can only observe half of the desktop.

What do I have to do??

Thxs!

---

### Post by gggerard on 2008-08-12
No one might give any idea? I am totally lost in this issue, and I do not think that the 8.10 ubuntu is going to fix it ...

---

### Post by susanw on 2008-08-12
I wonder if you have the driver for your graphics card installed? I just installed the correct one for my nvidia card and the screen correctly lined up. I had been looking all over linux for a way of realigning the screen (as it was an inch to the left before) but found no solution except this. (I'm still pretty new to linux and the way I installed the correct driver by going into appearance and turning on the 'normal' graphics instead of 'none'). 

Good luck

---

### Post by gggerard on 2008-08-12
Thanks for your reply

Since I have an ATI 9250, the unique driver available is that proportioned by ubuntu (the ATI driver is for newer cards).

However, that driver works ok with my monitor acer. The problem is with the plasma panasonic of 42".

I ignore who has the problem. The panasonic has a native resolution (non-squared) of 1024x768, but this corresponds to a squared resolution of 1280x720. This is the resolution that worked with windows for the display, and is the resolution that ubuntu catches for the panasonic.

Options:

a) the resolution is incorrect. I don't think so since in winxp it works (google also gives support here).
b) there is some problem with panasonic configuration. I don't think so again cause in winxp this resolution works.
c) there is a problem with the ubuntu manager. I have to test to solely connect the panasonic at the start. Perhaps there is a mess here?
d) there is a problem with the driver and dual displays. I simply do not know.

Indeed, I am sure that somebody in the world posses a plasma panasonic and uses an ubuntu distribution. She/he has the answer!

Thanks four your reply again.

---

### Post by Ubuntaqua on 2008-08-12
I don't see in what way the ATI driver (I suppose you are reffering to fglrx) is limited to newer cards. It adds tons of stuff to newers cards, ok, but it probably is by far a better option for dual screens and other things like that than the free radeon driver, even for your card.

My 2c

---

### Post by gggerard on 2008-08-12
Here, [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), you can read:

> Make sure the following things are true about your video card:

    * It is a 'Radeon' card
    * The model of the card is in the 9xxx series, **9500 or higher**, or it is in the X series (e.g. X300), or it has TV-Out capability. **The 'fglrx' driver does not support cards earlier than the 9500.**

Here, [BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto"), you can read:

> ATI (fglrx)

If you have an ATI Radeon 9500 or newer (including thx X-series, such as x300, x1600, etc, an Xpress 200, or a Radeon HD card), then you can use the restricted fglrx drivers: BinaryDriverHowto/ATI.

    * Radeon HD support is currently limited, but rapidly improving. 

If you are using an ATI Radeon card that is **older than above**, you need the open source drivers: RadeonDriver (NOT fglrx).

Here, [ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=764633") you can read:

> Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. **Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.** A more technical explanation is offered in RAOF's post, linked above.

In the spanish guide (I guess in the english version is the same), [guia-ubuntu.org]("http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%B3n_gr%C3%A1fica_ATI") you can read the same.

I remember to read that the problem was that the binary driver for <9500 ATI cards is not presently actualised by ATI, and although it worked in older ubuntues, in the 8.04 it causes some problems.

So I have no choice here ...

---

### Post by Ubuntaqua on 2008-08-12
> **gggerard said:**
> So I have no choice here ...My mistake. 

The only option I see is the all new open source driver being developped thanks to ATI opening up part of their specification. I know they focus on newer cards, just like fglrx, but maybe they can do something for you. The driver name is radeonhd.
good luck.

---

### Post by syms on 2008-08-12
i dont understand ur question good, but try this: open terminal, type sudo gedit /etc/X11/xorg.conf and find line somethink like:
virtual screen    xxxx     xxxx and change this resolution to correct.

---

### Post by gggerard on 2008-08-14
syms, the problem is that theoretically the resolution of 1280x720 is the correct, but in practice, I do not see the whole desktop in the panasonic.

Why do I think that the resolution is correct? Three reasons:

1- Plasma has not squared pixels. From what I've read, the panasonic plasma native resolution of 1024x768 indeed corresponds to a "squared" 1280x720 resolution. I have read this in several places.

2- In Windows XP, when I put (with ATI app) the resolution of 1280x720, and then I connect the panasonic, I can see correctly the desktop.

3- Ubuntu only detects one available resolution for the panasonic, and this is the 1280x720 (ergo this is the correct, isn't it?).

But, from what I see now with ubuntu, it is like the 1280x720 resolution is too high for the panasonic. Indeed, I suspect that perhaps a 1024x768 resolution would be better.

Questions:

1- Is the ubuntu resolution of 1280x720 not squared?? Is that possible??
2- How could I test other resolutions with ubuntu?? The xorg.conf file is quite empty in ubuntu 8.04
3- What the hell, the resolution of 1280x720 is the correct. What is the problem then??

So answering to your purpose, in the xorg.conf file I cannot find anything of virtual screen, not in the file version of ubuntu 8.04.

---

### Post by gggerard on 2008-08-15
More information: 

When I unplug the acer display and restart the graphics of ubuntu (control alt backspace), the resolution shown in panasonic is very close to be the right, the desktop is slightly higher and the top, bottom, left and right sides are little cut.

If I plug the acer display and restart the graphic server, then the panasonic is showing quite less desktop (the half). 

So there is some problem here with ubuntu ...

Is this information of utility??

---

