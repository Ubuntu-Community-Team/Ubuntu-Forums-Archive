---
title: "Force Resolutions?"
date: 2008-08-12
forum: Multimedia Software
---

### Post by Feezus on 2008-08-12
Good morning world,
I am currently wrestling with getting Fallout (run through Wine) to work properly on my laptop.  I finally was able to trick it into installing on my laptop, but I am now running into some pretty annoyoying resolution issues.  The issues is that Fallout, being a dated game, automatically runs in a low 4:3 resolution. 

 This wouldn't be an issues if it behaved like most 4:3 resolution applications on my 16:10 display.  Instead of distorting the image to make it fit the display or fitting it in a 4:3 in the middle of the monitor, leaving the left and right edges of the screen unused, the application fits the top edge pixel-for-pixel across the top of my screen, then maintains the resolution on the vertical axis, placing the lower ~20% of the screen off of my viewable area. 

Now, my cursor is able to go past the bottom of my screen and interact with the parts of the application that I can't see, but that's not very helpful as I have no idea what's down there.

Is there any way to force an application (not sure if running the application through Wine will affect the outcome) to run in a resolution that will fit on my screen or force the application to run windowed?

---

### Post by Feezus on 2008-08-15
bump

---

### Post by Feezus on 2008-08-18
As it turns out, I'm having this issue with ALL applications that chose to operate in full-screen mode.

---

### Post by Kinrah on 2009-03-22
You may want to try telling WINE to emulate a virtual desktop. It's an option on the Graphics tab of the WINE configuration (which you can get to by typing winecfg in terminal). You can tell it what size to make the virtual desktop, I'd suggest for your purposes to pick the resolution the game runs at.

---

