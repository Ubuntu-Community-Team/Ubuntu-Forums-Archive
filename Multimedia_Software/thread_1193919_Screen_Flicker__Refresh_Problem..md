---
title: "Screen Flicker / Refresh Problem."
date: 2009-06-22
forum: Multimedia Software
---

### Post by Shibblet on 2009-06-22
Well, I've been observing this for some time now, and I really don't know what is causing it.

Start from the top.  When I scroll down a web page, or email, I can observe what would be a "dividing line" on two different portions of the screen.  Now the line is it different locations, depending on what I am looking at.

It also shows up horizontally when I am watching video.  However, it goes away when I switch smplayer (my favorite player) to full screen.  I think when I switch to full screen, Nvidia's (Geforce 8600) VDPAU kicks in.  But if I move the mouse to the bottom of the screen, and the hud comes up, the lines come back.

To me, it looks like a slow refresh rate, but I don't know.  When I am scrolling down websites, it goes away really fast, like the refresh is trying to catch up.  It's not "hurting" anything, but I can see it, and it's annoying.

Here is a "simulated" screenshot of what it looks like.  But you have to think of it in motion...  This is what you can see as the screen scrolls down.

[ATTACH]118552[/ATTACH]

Any help would be greatly appreciated.

---

### Post by overdrank on 2009-06-22
What nvidia driver are you using in Jaunty? Have you tried the new 185.xx driver?

---

### Post by Shibblet on 2009-06-22
Yes, I am.  It happens on my Laptop as well, that's an Intel Video Card.

---

### Post by Shibblet on 2009-06-22
Bump.

---

### Post by Shibblet on 2009-06-23
I'm inscrutable, huh?

---

### Post by LKjell on 2009-06-23
Hi left click on the desktop and click on change the desktop background. Under Visual Effect make sure it says none.

---

### Post by Shibblet on 2009-06-23
Tried that already.  It only seems to happen when there are graphics on the screen.  Like photos or video.

---

### Post by Shibblet on 2009-06-24
I'm still inscrutable, huh?

---

### Post by Shibblet on 2009-08-08
I think I've finally figured out what the issue was.  I downloaded the Compiz-Fusion icon, and turned on Metacity Windows manager instead of Compiz.  all of the flicker and weird refresh issues went away.

My guess is that it was something to do with the way Compiz handles the screen drawing.

So it's great flipping windows around, but not so good for video playback.

---

