---
title: "Radeon 2400 drivers are glitchy, want to revert to generic drivers"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by MaxIBoy on 2007-12-25
My computer isn't the best in the world. It has 512 MB of PC3200 RAM, 128 MB of which is gobbled up by the SiS 760 integrated graphics card. I was fed up, so I went out and bought another 512 MB of ram and an ATI Radeon HD 2400 Pro graphics card. The RAM stick works perfectly. The card has 256 MB of DDR2 RAM, two HD outputs and an S-Video output, as well as an HD-to-VGA adapter. It fit into the AGP slot just fine, and it worked when I booted it up. Then I tried to get the right drivers in order to actually be able to use 3D acceleration.

First I found one that (I think) changed the display to 256 colors. Then I found one that worked, until I tried a game that had previously always resulted in a black screen of death. It also had a black screen of death, but after the desktop came back the display was on 256 colors. Then I looked on the ATI website and found the official driver. I installed it, and then when I tried to open the Catalyst Control Center it said I didn't have a functioning driver. I tried using aticonfig, still nothing. Then, somewhere down the line, something happened. I think the monitor was getting a mixed-up signal. I'm pretty sure the "color" value wasn't lined up with the "position" value, with the end result that the scanlines weren't lined up on the monitor, and everything was broken up into stripes. Completely unreadable.

At one point, it would boot up in low graphics mode, which had a way-too-small resolution but it worked. Now it won't even do that anymore. It works just fine when booting off a CD, so I think it's the actual driver. 

I tried using different monitors and I tried taking out the graphics card altogether. Same result. As soon as I get past text-only, it's all white noise on the screen. How can I, booting up in recovery mode and using only the command line, reinstall the generic drivers and restore the computer to its original state? I can work on getting the graphics card to work later, but I at least need a functioning computer.

---

