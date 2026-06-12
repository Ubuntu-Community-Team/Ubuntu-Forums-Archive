---
title: "I can have either my left monitor, or my right, but not both."
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by oscartheduck on 2007-10-19
Hi folks,

I just performed a fresh install of 7.10 to create a dual boot system with Windows XP installed on the other partiiton. Ubuntu did a great job of automatigically partitioning evreything without a hitch.

When I first booted up, my *left* monitor was displaying just fine. It uses an intel 910 onboard graphics card; my *right* monitor, using a Radeon 7000 graphics card, was not displaying. Both monitors are Dell E173FP monitors.

I opened system/administration/screen&graphics

there were *three* monitors listed: screen1, screen 2, and screen 1.

I looked at the first screen 1: it was running at 1280x1024, my preferred resolution. Ubuntu had autodetected the monitor fine, it had autodetected the graphics card fine. Everything was good.

I looked at the second card; Ubuntu had autodetected the graphics card fine, but had not selected the driver. The monitor was disabled.

The third monitor was also disabled, and I don't remember what the graphics card was set to. I *think* the generic vesa, but I'm uncertain.

Anyway.

I tried to activate the second monitor, the Radeon 7000 card. But I only had the option to either disable it or to make it the default monitor. I tried making it the default monitor, but the only result was that my left hand monitor, the one connected to the intel card, flickered.

I rebooted. I had my left hand monitor and my right hand monitor. The left was still active, the right hand one dead.

So I rebooted again, to make sure that my windows partition was okay. It needed to perform a chkdsk, so I went home so it could do that without me wasting my time watching it.

When I came back to work the computer had rebooted into Ubuntu, as expected. But the monitor had an error message that it was running in safe-default mode. I checked the screen and graphics tool and the intel graphic card was listed as a vesa grpahics card. I figured "That's weird, but it's great that bulletproof X works."

I tried setting it back to an intel 910 graphics card, and X failed. Stardted restarting itself repeatedly, and after ten minutes I became convinced it wouldn't failover to the vesa driver. I alt+F1ed into the virtual terminal there, logged in and rebooted.

I was back into safe defaults mode. I logged in. I checked screen and graphics again. I decided to see if I could start the right hand monitor, the Radeon7000. I wanted to make sure I had the screen model right, so I started turning the monitor. As I was doing that, I noticed that from angles that weren't at 90 degrees, I could see some very faded text on the monitor.

Anyway, I was able to get the radeon card working by selecting the appropriate driver, but it's slow as hell, and I was only able to get it running by telling it that it was the primary monitor, so I lost the other monitor. Screen refresh is glitchy and text refresh rate is slower than I can type. But at least it *works*.

I'm hoping that we can get the intel card functioning again first. It was able to support all the nice graphics features that Ubuntu has by default these days, and then if we can a dual screen setup, great.

---

### Post by oscartheduck on 2007-10-19
Ubuntu appears to have heard my grunting and cooperated.

The left hand monitor, my intel monitor, is now functioning again. I glared at it in the correct way, I suppose, because I didn't touch the driver settings, I just asked it politely through the screen & graphics manager to please use the left screen at the correct resolution, logged out, and everything was fine.

Although the right hand monitor is now black as sin. If I look at it from odd angles, though, it appears to be displaying white dots across the entire thing.

Curioser and curioser.

---

