---
title: "Dell Latitude D610 docking station dual monitor problems"
date: 2005-12-13
forum: Multimedia &amp; Video
---

### Post by minneyar on 2005-12-13
I have a Dell Latitude D610 with a docking station that I use as my computer at work.  I have installed Kubuntu 5.10 on it, and for the most part, it works fine.  However, my docking station has both a DVI and a VGA output, and I can't get them both to work at the same time.  My desktop spans across them perfectly in Windows, so I'm sure that it's possible.

When the computer first boots up, it seems to use the monitor attached to the DVI port as the primary display; as long as it remains in text mode, everything displays on that monitor.  However, when X starts, the DVI monitor goes blank and the display switches to the VGA monitor.  If I switch back to text mode, the text appears on both monitors at once.

Any ideas? I've tried all of the Xorg.conf options I can think of, and nothing has helped.  I've attached my current xorg.conf; a sample startup log can be found at [http://speed.sakabatou.net/Xorg.0.log]("http://speed.sakabatou.net/Xorg.0.log"), it's too large to attach here.  I think this may be the most interesting part of the log, but I don't know what it means:
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=35000; xclk=21700
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled

Surely if Linux will display text modes on that monitor, there must be a way to get X to recognize it...

---

### Post by stuporglue on 2005-12-13
You need to look into Xinerama. It will let you set up two (or more) monitors in spanning or mirroring mode. I don't think there's a GUI tool for it though, so get ready to enjoy manually editing your xorg.conf. :-) 

I used to have a dual screen setup, but have since sold that computer, so I don't have any example xorg.confs arround anymore. Sorry!

---

### Post by minneyar on 2005-12-14
I'm fairly familiar with Xinerama, and I'm pretty sure that this problem has nothing to do with it.  The DVI display is never even being intialized by X.

However, after messing around with it for a while more, I've eventually managed to get it to work with ATI's proprietary binaries.  I had to force it to disable the laptop display and enable the first DVI and first VGA display, and then force the correct video modes on the two displays, as at first it attempted to use the settings it detected for the laptop display as the settings for the DVI display.  I'll attach my xorg.conf for anybody else who has a similar problem...

Of course, now I have a problem where the display drivers lock up if the display mode changes.. for example, if I switch to a text console and then switch back, or if I log out.  Very annoying, but at least I can use both monitors now...

---

