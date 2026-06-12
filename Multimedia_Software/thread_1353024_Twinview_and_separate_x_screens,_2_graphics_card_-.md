---
title: "Twinview and separate x screens, 2 graphics card - 3 monitor setup"
date: 2009-12-12
forum: Multimedia Software
---

### Post by n8wish on 2009-12-12
Hi everybody,
I'm trying to build a three monitor setup while two of them are running on a Nvidia Card ( GeForce 9500 GT) with Twinview (2x1280x1024), and a third monitor shall use the second ATI card (Mobility Radeon HD 3450) running as a separate X Screen in 1680x1050.

The Twinview was easy enough to accomplish, this is the current setup. Now the second Card and third monitor is added.

I tried

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" rightof "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
```

as well as introducing a second Layout:

```
Section "ServerLayout"
    Identifier     "Layout1"
    Screen      1  "Screen1"
EndSection
```

the third monitor on the ATI card stayed dark so far...
any hints?

regards Jens

---

### Post by osarusan on 2009-12-25
I'm having the same problem -- an nvidia card and an ati card, the monitor on the ati card doesn't show anything.

I think this has to do with the fact that the kernel is either compiled with the nvidia driver or the ati driver, but not both.

I have no idea how to fix this, or if it can... :-( Nowhere have I been able to find a decent answer.

edit:
I did find this: [http://en.gentoo-wiki.com/wiki/HOWTO_Dual_Monitors](http://en.gentoo-wiki.com/wiki/HOWTO_Dual_Monitors)
I'm going to give it a try...

---

### Post by Seinfeld on 2011-05-11
Hi.. 

My problem is somehow similar. I am using 2 Nvidia 9600 and 8600 cards. I have two monitors running in TwinView with no problem on the first card. 
I added a third monitor to use as a separate x screen connected to the second card. The monitor worked fine as a separate xscreen. However, no TwinView on the other two, 
The  first card sees the first two screens as one spread on two monitors. Isn't that Xinerama?? I did disable xinerma from nvidia settings, restarted xserver but, no way. 
I Just need two monitors working in a TwinView on the first card and the third one connected to the second card as a separate screen.. 
Any help please is much appreciated..

Thank you very much

---

