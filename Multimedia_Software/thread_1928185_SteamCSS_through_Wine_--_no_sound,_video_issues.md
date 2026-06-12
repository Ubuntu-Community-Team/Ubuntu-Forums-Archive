---
title: "Steam/CS:S through Wine -- no sound, video issues"
date: 2012-02-19
forum: Multimedia Software
---

### Post by matbluvenger on 2012-02-19
So I got Steam and Counter-Strike: Source running through Wine (finally) and I get the Valve loading screen just fine, sometimes with and sometimes without sound.

But once I got to the menu screen the background was all black and the resolution on the text was so awful it was nearly impossible to read. (Image 1)

So I selected a server I frequent and the screen is still black during loading (Image 2). But once it joined the server it got stuck on the welcome screen that it didn't even load (Image 3.)

Computer information:
- Ubuntu 11.10
- 3.0GHz Pentium 4 (Socket 775)
- 2x1GB DDR2 DIMM RAM
- 512MB DDR2 Geforce 8400GS (PCI-E)
- Wine 1.3


Image 1
[IMG]http://www.homebrewtalk.com/gallery/data/500/medium/Screenshot_at_2012-02-19_12:21:30.png[/IMG]


Image 2
[IMG]http://www.homebrewtalk.com/gallery/data/500/medium/Screenshot_at_2012-02-19_12:22:52.png[/IMG]


Image 3
[IMG]http://www.homebrewtalk.com/gallery/data/500/medium/Screenshot_at_2012-02-19_12:24:07.png[/IMG]

---

### Post by matbluvenger on 2012-02-21
*Bump*

Sound magically works now but I'm still getting the same as the images show above.

Any ideas?

---

### Post by matbluvenger on 2012-02-25
*Buuuump*

Any solutions? I promise I'm not a hardcore gamer that got in over his head with Ubuntu... I've just been playing CS for so long every now and then it's nice to go back.

---

### Post by lite1979 on 2012-03-08
Try this: Applications>Wine>Wine Configuration>Libraries (tab), add "gameoverlayrenderer.dll" and disable it

---

