---
title: "What video cards are WELL supported?"
date: 2009-12-31
forum: Multimedia Software
---

### Post by fwiffo on 2009-12-31
What brands of video cards are well supported in current versions of ubuntu/kubuntu?

I need support for multiple large monitors, including rotation. I would like to be able to use desktop effects and get reasonably good performance.

My current nVidia card does not do the job. In order to be able to rotate my second monitor, I have to use Xinerama which means no desktop effects and lousy performance. It does not support XRANDR. I want to throw it out and get a new card, but I want to be sure I'm getting one that will actually work.

I don't mind using binary or third-party drivers as long as I don't have to kill myself to get them working.

*Edit: I got an ATI card and it works perfectly.*

---

### Post by fwiffo on 2010-01-04
*bump*

---

### Post by inobe on 2010-01-04
you have to add the line

```
Option "RandRRotation" "true"
```

in your xorg.conf and log off/ reboot.

then when your back up again run these commands to 

```
xrandr -o normal

```

```
xrandr -o invert
```

```
xrandr -o right
```

```
xrandr -o left
```

if you have a kde desktop you can use the display utility.

---

### Post by inobe on 2010-01-04
just tried it, works perfectly with my nvidia card, had to turn my head sideways to run the normal command :lolflag:

---

### Post by fwiffo on 2010-01-04
Do you have two monitors?

---

### Post by inobe on 2010-01-04
> **fwiffo said:**
> Do you have two monitors?

yes, i am not home now, when i get there i can hook the second one up.

are you implying that it doesn't work for both monitors ?

---

### Post by fwiffo on 2010-01-04
Correct. You can get a reasonable dual-head setup OR XRANDR but not both.

I've gotten close by using Xinerama, but that is incompatible with XRANDR, you don't get compositing (desktop effects) and performance is poor. I can rotate the second monitor by specifying it manually in the xorg.conf, which is fine, but would rather have full support. Xinerama is deprecated anyway.

I've also tried nVidia's proprietary Twinview, but that craps out on X startup because the two monitors collectively have a width > 4096 pixels.

I've really been through a lot just to get to get to limping, and I have given up on nVidia. I'm reasonably certain there is no solution currently for nVidia cards. Even if there is, I don't care any more. I just want a card that works.

**In short: I have no interest in trying to get this nVidia card working any more. I'm committed to throwing it away. I just want to know what brands of cards actually *do work* without going through the trials of Job before I go and buy a replacement.**

I've asked this question a number of times before when I was originally trying to get the nVidia card working, but can never get an answer. Either nobody else in the world has a setup similar to mine, or there are no video cards which work properly under linux with this setup.

---

### Post by inobe on 2010-01-04
i just got in and have yet to hook up the second monitor.

in nvidia settings under rotation settings' do you see one or more monitors listed ?

btw i feel your frustration and if i find a solution i will most definitely bump this thread.

---

### Post by fwiffo on 2010-01-05
Yes, when running in Xinerama I can see both monitors (though I can only change the rotation by editing my xorg.conf manually). But if I choose not to use Xinerama, nvidia-settings will either produce an xorg.conf that won't boot, or one that won't let me use the second monitor.

---

### Post by fwiffo on 2010-01-06
*bump*

Once again, I'm not looking to fix my current setup. I just want to what video cards are well supported (not nVidia).

---

### Post by markbuntu on 2010-01-06
The latest ati proprietary driver seems to support rotation with multiple monitors  with newish single cards with multiple monitors according to their release notes and some posts I have seen at the phoronix forums but to be sure you should do a search or look/ask in the phoronix forums where some of the ati devs and many bleeding edge users hang out. 

For multiple cards with multiple monitors you will still need xinerama which is only available with nvidia and ati proprietary drivers. This is a limitation of randr that has just recently been resolved. Do not expect to see this new randr version until at least the next round of distribution releases this spring but maybe later than that.

The latest 5xxx cards from ati can run 3 large monitors from a single card.

---

### Post by fwiffo on 2010-01-07
Thank you, I'll check the phoronix forums.

---

