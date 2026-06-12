---
title: "Problem with ATI radeon 3200 and Samsung SyncMaster 2494HS"
date: 2009-07-30
forum: Multimedia Software
---

### Post by jaaylwar on 2009-07-30
Has anybody else met problems with this combination?

ATI radeon 3200HD and Samsung SyncMaster 2494HS.
(Ubuntu 9.04)

I can't get the ATI driver to fit the screen properly on it's native resolution of 1920x1080. It's too tall for the screen, although exactly the right width, and text is a bit fuzzy, so it's obviously not quite hitting the right resolution.

It works ok on the ubuntu driver, but then you lose all the special effects.

thanks in advance
Jamie Aylward

---

### Post by markbuntu on 2009-07-30
Are you using the latest driver from ati?

---

### Post by jaaylwar on 2009-07-31
Thanks, but yes.

---

### Post by jaaylwar on 2009-08-01
Problem sorted.
In case this happens to someone else, I restored my system from a back up.
I'm not sure if the problem was caused by trying out a different 24 inch monitor, and perhaps it remembered the configuration for this.

but very happy now - and it's a lovely monitor!


> **jaaylwar said:**
> Has anybody else met problems with this combination?

ATI radeon 3200HD and Samsung SyncMaster 2494HS.
(Ubuntu 9.04)

I can't get the ATI driver to fit the screen properly on it's native resolution of 1920x1080. It's too tall for the screen, although exactly the right width, and text is a bit fuzzy, so it's obviously not quite hitting the right resolution.

It works ok on the ubuntu driver, but then you lose all the special effects.

thanks in advance
Jamie Aylward

---

### Post by svaens on 2009-11-01
Actually, I have a very similar situation ( HD3470 with syncmaster 2494HS, Ubuntu jaunty) and my problem is that I cannot get it to fill the whole screen. There ends up a black border around (around 1 - 2 cm in width) the actual image. 

It does recognize it as the correct resolution (1920x1080) but still it does this..... 
I tried a few different setups.. 

First I tried a very simple output via HDMI, exactly mirroring that which is on my laptop lcd. Same black border. 
Now i've got a virtual screen thing happening so I can have a dual monitor setup (but i have the same exact sized black monitor). 

Here is my xorg file

```


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	3520 1080
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


```

What i've had to do to get even this far is 

1. first configure using ubuntus display preferences
2. Then (because Ubuntu incorrectly and unasked changes the resolution to my laptop screen) I go into the configurations again and re-set the resolution to the laptop monitor, (setup and screen freezes up a bit at this point, but it recovers and I am able to log out)
3. log back in, basically all correct (laptop screen resolution, monitor reported resolution) except for the black border. 

any ideas?

---

### Post by svaens on 2010-10-25
some time has passed.. 

I did eventually get rid of the black border, but at the expense of a clear screen. I stretched it. Not sure if it was clear to start with though, so I put up with it. Unless I am viewing clear pictures or particular patterns does it really cause me problems... 

I am wondering if anyone else out there with an ATI card and this monitor has had any luck ... for instance with maverick?
 I haven't upgraded yet, and didn't want to if none of the bugs which affect me still exist;

1. brasero broken (general bug, not just me)
2. monitor stretch

---

### Post by svaens on 2010-12-13
actually, 

its been a while... but now I have a slightly different problem.

I would have liked to use the radeonhd driver for this now, instead of the ati proprietary.

problem is with the radeonhd driver, with the second screen, ubuntu seems to 'think' the monitor is physically larger than it is.

That is, it accepts the resolution fine .... but when I maximize a window in that monitor, the whole of the titlebar is hidden outside of the viewable screen. 

any idea how I can fix this?

(p.s. i'm connected via HDMI)

---

### Post by Wartickler on 2010-12-13
Not for nothing but didn't you say you stretched your screen in the previous post?

---

### Post by svaens on 2010-12-13
Hi, 

yes, sorry, I was probably not clear;

In my previous post I was using the proprietary ati driver.

With the proprietary driver, I get the situation where the second monitor is slightly fussy, and also not fully stretched out to fit the screen (even though it reports that the resolution is correct, I "think" it is not). This I made a bit better by stretching it out, as I could do that with the catalyst configuration software for ATI. But there was no way to remedy the fussy look of the graphics. It is usable, but not quite nice.


In the free radeonhd driver, I have a different problem;

I wanted to try that driver to get around the fussy monitor problem. Using the free driver, it is not fussy.
But then I have the problem that the 'desktop' is larger than the physical monitor screen size. Resolution reports fine. 

I get none of these problems when I use my girlfriends computer which is using the proprietary nvidia driver (as it has an nvidia card).

---

