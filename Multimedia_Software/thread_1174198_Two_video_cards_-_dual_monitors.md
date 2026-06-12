---
title: "Two video cards - dual monitors?"
date: 2009-05-30
forum: Multimedia Software
---

### Post by AgentWiggles on 2009-05-30
So a friend gave me a very old computer and monitor. I gutted the computer, and found it had an old 16mb video card in it. I had a spare PCI slot so I popped it in and hooked up the monitor to see if I could get dual monitors running. 

However, right now, the new monitor (which is actually an old monitor) is hooked up, and it has the little orange led that indicates it has power, but it isn't showing anything, just a black screen. Now it's very possible that either the new video card (which, again is actually very old) or the new monitor is broken, but I don't know how to check that. 

1) is it possible to have a dual monitor setup that utilizes two video cards, like mine?
2) if yes, how can I do that?
3) is there a way to see if the system is recognizing the video card I just put in? If it's not recognizing it, that's a pretty good sign that the card is broken.

Actually, I just found out that the new monitor is broken by conencting it to my main video card. However, if all this stuff would work, I could just leave the video card in until a functional monitor comes my way...

---

### Post by MasterJS on 2009-05-30
You can test by pulling the video cards out one by one. You pull one out, leave on in, and then turn it on to see if it works. If not, try the other one. If both do not work, it might inface be the monitor

---

### Post by AgentWiggles on 2009-05-30
Hmm. Well I connected the functional monitor to the new video card - no dice. So either both the new monitor and the new video card are broken, which is sad, or the computer just doesn't know what to do with that second video card and therefore isn't sending anything to it.

---

### Post by corncob on 2009-05-30
I set up my daughters computer for dual monitors.  The video card had two ports, a VGA and a DVI.  I connected monitors to each of these.  I was told to have the Nividia drive installed from the Linux restricted modules package (which it was).  The book (Ubuntu Hacks) then gave be the code to run in Terminal:

sudo nvidia-xconfig -twinview

This installed TwinView in /etc/X11/xorg.conf and the second monitor sprang to life.  I can't send you a copy of the file as I'm not on that computer.

---

### Post by AgentWiggles on 2009-05-31
I think this is different because I have two video cards, not one with two monitor ports on it.

---

