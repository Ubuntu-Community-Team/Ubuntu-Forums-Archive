---
title: "Gigabyte's MA78GM thermal issues - solved?"
date: 2009-03-16
forum: Multimedia Software
---

### Post by clubsoda on 2009-03-16
I went looking for an MA78GM-S2H motherboard on the strength of techreport's [AMD 780G chipset review](http://techreport.com/articles.x/14261/1) of a year ago.  The combination of "best 3D performance (from integrated graphics)" with a total system power of only 47W at idle looked pretty good.  Techreport didn't mention that the passively cooled northbridge runs pretty hot on that board, with some people claiming temperatures in the 70's-80's.([1](http://forums.whirlpool.net.au/forum-replies-archive.cfm/975966.html),[2](http://www.avforums.com/forums/home-cinema-pcs/933719-north-bridge-fan-header-help-ga-ma78gm-s2h.html))

Maybe I was lucky that the S2H was sold out and I ended up with a newer MA78GM-US2H instead.  However, I soon noticed that the northbridge was running hot.  The three temperature sensors on the it8718-228 all showed less than 40 degrees so I set out to do some measurements of my own.

[img]http://ubuntuforums.org/attachment.php?attachmentid=106596&stc=1&d=1237216629[/img]

What I found is that the northbridge heatsink runs at 49 degrees Celcius or 24 degrees above ambient.  The temperature doesn't change significantly by running glxgears.  The **VGA Core Clock** in BIOS can be cut back to 250MHz (from 500MHz default) to run the northbridge 4 degrees cooler.

I'm no thermodynamicist but the heatsink looks wrong in a few ways:
 - To promote convection the fins should be vertical, not horizontal.
 - The logo cover plate obstructs airflow.
 - There is nowhere to attach a fan.
The board has an NB_FAN connector and the BIOS can warn if the fan fails.  This is begging for an aftermarket replacement heatsink done properly.  Even a passive design could extend beyond the current 13-26mm fins.

It would appear that Gigabyte has moved the third onboard temperature sensor away from this hottest component... a cover-up?  Also it seems strange that while this board boasts "50,000 hrs. Japanese Solid Cap.", the capacitors next to this heatsink are common electrolytics.  Maybe I'm over-estimating the risk, but the reason I bought this motherboard was the failure of an AGP graphics card, presumably due to heat.

Finally, given that TDP is so important in the CPU market, how is it that graphics chip makers manage to keep their TDPs secret?

---

### Post by clubsoda on 2009-03-24
> **clubsoda said:**
> ...how is it that graphics chip makers manage to keep their TDPs secret?

[http://ht4u.net/reviews/2009/power_consumption_graphics/index13.php](http://ht4u.net/reviews/2009/power_consumption_graphics/index13.php)

---

