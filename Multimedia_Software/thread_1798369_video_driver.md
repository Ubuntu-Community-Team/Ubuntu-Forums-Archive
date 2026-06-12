---
title: "video driver"
date: 2011-07-06
forum: Multimedia Software
---

### Post by Bobscrachy on 2011-07-06
How do I permanently set my video driver to generic? I have an ATI rage 128 pro video card that I just installed because my onboard video wasn't supported. But it will only work if i go through the recovery and run the session with the generic driver. I've tried to get it to run it permanently through the recovery console, but it won't let me select the option.

---

### Post by no2498 on 2011-07-06
i have looked for my self and this is what i seen
hope it helps you

[http://www.google.com/search?client=opera&rls=en&q=Physically+install+new+GPU+to+the+motherboard&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=Physically+install+new+GPU+to+the+motherboard&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

---

### Post by Bobscrachy on 2011-07-06
> **no2498 said:**
> i have looked for my self and this is what i seen
hope it helps you

[http://www.google.com/search?client=opera&rls=en&q=Physically+install+new+GPU+to+the+motherboard&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=Physically+install+new+GPU+to+the+motherboard&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

Installing the physical hardware isn't the problem. Changing the settings in ubuntu to get it to use the generic video driver is.

---

### Post by handy on 2011-07-07
You should be able to disable the onboard GPU in the machines BIOS.

After that as far as any OS you install on that machine is concerned the onboard GPU does not exist.

If you don't know how to access the BIOS on your machine have a look in the manual, or have a quick search & you'll come up with the keyboard, key combination required.

---

### Post by Bobscrachy on 2011-07-07
I DO NOT have any trouble installing the hardware. The video card is in there and I can get to the grub menu. What happens is the video cuts out when it tries to boot into ubunt normally. If i go through the grub menu and into the recovery partition it will boot on into ubuntu using the generic video settings. 

The original question was how do I set the permanent driver to be the generic driver? I believe it is still trying to use the old onboard nvidia driver with the new card.

---

### Post by handy on 2011-07-07
My previous post wasn't about installing the hardware so much as getting the correct driver to work.

Anyway, moving on, have you uninstalled the old nVidia driver?

---

### Post by Bobscrachy on 2011-07-07
> **handy said:**
> My previous post wasn't about installing the hardware so much as getting the correct driver to work.

Anyway, moving on, have you uninstalled the old nVidia driver?

.......

I can get to grub to use the recovery partition. Having the video card recognized by the bios is sort of a prerequisite for getting to grub.

How do i uninstall the old driver?

---

### Post by handy on 2011-07-07
> **Bobscrachy said:**
> .......

I can get to grub to use the recovery partition. Having the video card recognized by the bios is sort of a prerequisite for getting to grub.

My understanding is that you have an onboard (built in non-removable nVidia GPU) that has failed & you have since installed an ATi GPU equipped graphics card.

Is that correct?

---

### Post by Yellow Pasque on 2011-07-08
```
gksu gedit /etc/X11/xorg.conf
```
Copy/paste this:
```
Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
Save. Quit.

---

