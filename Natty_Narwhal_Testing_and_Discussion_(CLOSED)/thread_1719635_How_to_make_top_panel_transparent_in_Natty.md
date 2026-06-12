---
title: "How to make top panel transparent in Natty?"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2011-04-02
Hi, I just installed Beta 1 of 11.04 today and was wondering how I could make the top panel transparent. I seen it on OMGUbuntu's site and it amazed me how good it looked transparently. 

Thanks.

---

### Post by VinDSL on 2011-04-02
> **TheNerdAL said:**
> Hi, I just installed Beta 1 of 11.04 today and was wondering how I could make the top panel transparent. I seen it on OMGUbuntu's site and it amazed me how good it looked transparently. 

Thanks.

Install CCSM.

Adjust "Panel Opacity" in the Unity Plugin  ;)

[IMG]http://vindsl.com/images/unity-experimental.png[/IMG]

---

### Post by TheNerdAL on 2011-04-02
Thanks! :D

---

### Post by VinDSL on 2011-04-02
> **TheNerdAL said:**
> Thanks! :D
You're welcome!

BTW, I just realized the hideous "drop shadow" (below the top panel) is back.  Must have happened on the last update.  It wasn't there last night.

This shadow, of course, makes it impossible to have true transparency.

I thought that %@$! shadow was gone for good!  It disappeared for a couple of months -- now it's back. :(

Oh, well. When I figure out a workaround, I'll post the fix.

Here's how it looked, before they wrecked it...


**[COLOR="Red"]BEFORE[/COLOR]**:
[INDENT]**Ubuntu 11.04 / Conky 1.8.0 / Lua / Unity / Metric Weather Stats** (Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-1-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-apr-2011.png")[/INDENT]


**[COLOR="red"]AFTER[/COLOR]**:
[INDENT]**Ubuntu 11.04 / Conky 1.8.0 / Lua / Unity / Imperial Weather Stats** (Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-2-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-apr-2011.png")[/INDENT]

---

### Post by VinDSL on 2011-04-02
**Bug Report**:   [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682)

Feel free to pile on, if this re-enabled "drop shadow" bugs you as much as it does me.

The more, the merrier...  ;)

---

### Post by Quackers on 2011-04-02
> **VinDSL said:**
> **Bug Report**:   [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682)

Feel free to pile on, if this re-enabled "drop shadow" bugs you as much as it does me.

The more, the merrier...  ;)

Done!

---

### Post by kansasnoob on 2011-04-02
I wonder if that can be done in unity-2d?

I've only begun playing with awn to create a lower dock/panel to replace some of the goodies I miss at the bottom of my screen, and making the top panel transparent would really improve the overall appearance.

I'm far from having things figured out but there's certainly no rush :)

---

### Post by coffeecat on 2011-04-02
> **VinDSL said:**
> BTW, I just realized the hideous "drop shadow" (below the top panel) is back.  Must have happened on the last update.  It wasn't there last night.

Tbh, I'm in two minds about this one. I can see where the designers are coming from with this. I find your first screenshot rather disconcerting - there's a functional panel there but I can't see it. I prefer your second screenshot. :) The drop shadow defines a feature of the desktop, but the panel is transparent allowing the details of the wallpaper to continue into it. I like it!

Perhaps if we had the ability to switch the drop-shadow on and off to cater for all tastes.

---

### Post by VinDSL on 2011-04-02
> **coffeecat said:**
> Perhaps if we had the ability to switch the drop-shadow on and off to cater for all tastes.
Yes, absolutely!  I totally agree...

That's what I suggested, in the bug report:

> [...] Personally, I would like to see a check-box option for disabling the hideous drop shadow entirely, regardless of the Panel Opacity.

This could be placed in either the CCSM Ubuntu Unity Plugin or Window Decoration module. [...]

---

### Post by mc4man on 2011-04-02
If there is one thing for sure it is the shadow is here to stay. If any allowance is created to control/disable, who knows, at best it probably won't be high on any list.

Overall I could see getting used to and it works/doesn't work depending on the background
Here I'm happier without the shadow so have created a patch to remove, though unity must be rebuilt. Additionally any patch would likely have be be adjusted with each unity upgrade, there are likely to be several more.

Intend to keep the patch updated thru release, can be posted for those that desire
(also anticipate the could be some ppa spins on unity that  may arise

---

### Post by VinDSL on 2011-04-03
> **mc4man said:**
> Here I'm happier without the shadow so have created a patch to remove, though unity must be rebuilt.[...]
Not even that. LoL!

I can 'fix' the problem in 18.2 seconds...  :D


[INDENT]**Ubuntu 11.04 / Conky 1.8.0 / Lua / Classic Mode / Imperial Weather Stats** (Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-2-apr-2011(3)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-apr-2011(3).png")[/INDENT]


Well, let's see how they respond.  I'm a patient man!

Everything else can be manipulated in CCSM.

Why not the drop shadow, you know?  ;)

---

