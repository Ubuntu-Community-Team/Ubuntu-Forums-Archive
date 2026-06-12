---
title: "Dual Desktop with fglrx"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by exoren22 on 2007-09-20
Ok, I guess I kind of want the best of both worlds. I set up the fglrx driver and cimpiz+emerald, and it all works quite wonderfully. My next step was to get my 24" acer set up in dual monitor mode. I wanted somethign akin to "extended desktop" in windows. 
So, I ran sudo aticonfig --initial=dual-head, and I got two monitors, but one was black with the black X cursor you get in xgl before everything losds. I  expected this, and I then tried sudo aticonfig --dtop=horizontal and restarted the xserver. 
Alas, I thought I had it! Except it had the taskbar across the bottom of both monitors, and when I maximize a window it stretches across both monitors. I am pretty sure this is the normal, and expected, mode of operation. 
I have heard of a way of setting up both displays as different desktops, which is basically what I want,but then I wouldn't be ablt to drag windows between them, would I? I would, of course, prefer two separate desktops to this stretched thing, and I would appreciate a point in the right direction towards whatever you think would be the best solution to this dual monitor peculiarity

ps. Also, as a weird side effect of smart window placement, some windows get put directly in the middle of the monitors, splitting the window in half. It's just weird, and this is the stuff I am looking for a fix for. 

Thanks in advance to everyone who will undoubtedly help me in my foray into cool linux workspaces. :guitar:

---

### Post by HaoTian on 2007-09-21
Yup... that was as far as I could get it to go using the fglrx driver.  I could either get it working without Beryl/Compiz perfectly as dual screen, or I could run it with Beryl/Compiz in that big desktop mode... it was annoying enough that I just went to the dual head display without.

There is a new driver with AIGLX support due out next month from ATI for Linux.  I'm hoping that Ubuntu will include it early on, as I'm very eager to get dual head + Beryl working with this :)

---

