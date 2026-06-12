---
title: "A bit frazzled..."
date: 2008-02-25
forum: Mythbuntu
---

### Post by Mythical Proportions on 2008-02-25
Over the past few weeks I read up on building a HTPC and decided on building a myth box.  I took a look at what everyone was using and decided on the gigabyte ga-ma69gm motherboard because it was so feature rich.  Well,  I have hit a snag that wasn't apparent when I made my purchase.  It seems that as long as you want to use the board to power a monitor it will work fine as I have been configuring mine with an old 14 inch lcd, but my goal is for it to run my Mitsubishi rear projection HDTV which will accept component video.  This is my biggest problem.

If anyone has enabled the Component Video out with this card I'd like to know how they configured it. 


As an aside to this post:  If I cannot get this working I need suggestions on a good Nvideo alternative with Component video.   I don't plan on overtaxing the video so I don't think I need a 8800 series card and an inexpensive card that works is all I really need.

Dan Sommerfeld

---

### Post by majoridiot on 2008-02-26
i think the component out issues you are having are due to the ATI drivers.  it looks like you
are not alone and that there is no easy fix for the situation right now.  with luck maybe a fellow
ATI user will chime in with more info.

in the meantime, if you are looking for an nvidia solution, the 7600 series would work well and is affordable,
or you could step up to the 8600GT, if your wallet allows.  i run both cards and 720p over component out
works well and looks great with each.

here's a comparison of the 7600 series vs. what you have now- it may help with a decision:

[http://www.techspot.com/review/31-radeon-x1650xt-vs-geforce-7600gt/](http://www.techspot.com/review/31-radeon-x1650xt-vs-geforce-7600gt/)

---

### Post by volkswagner on 2008-02-26
Have you enabled the restricted drivers?  Have you tried installing the propriatory drivers?  I am running Mythbuntu 7.10 AMD64 with ATI 1250 onboard.  I am 90% satisfied after running Envy.  I am using s-vid out, which is on the same header/breakout bracket on my setup.  My only current issue is when viewing live TV, entering the guide does not properly display TV window.

---

### Post by Mythical Proportions on 2008-02-26
I enabled the restricted driver.  I followed the instructions for installing the ATI proprietary drivers.  Everything worked, but I couldn't find information on what the next step was.  

Here is where it gets weird:  I brought my system into work to mess around with it and in the process of hooking it up to another monitor the xorg.conf file was modified and I lost the ATI driver.  I tried to reinstall it but the:
sudo aticonfig --initial 
- aborts and erases the xorg.config file.  I have recopied the file over and over again now, but the same thing happens everytime I try to reinstall.  

So,  I didn't know anything about ENVY, and I have installed it on my system.

Okay...

I ran the ATI install from ENVY's GUI and rebooted the computer after installation.  The computer (I didn't mention this earlier) is still coming up with a display warning every time I reboot. 

The restricted driver now shows the "ATI accelerated graphics driver" as enabled and "in use".  The AMDCCCLE still doesn't work.  The Xorg Config is using "vesa - Generic..." in the graphics card section and the screen is set at 800x600 at 85Hz.

I ran "fglrxinfo" and it gives me
Xlib:  extension "GLX" missing on display ":0.0"
Xlib:  extension "GLX" missing on display ":0.0"
Error:  couldn't find RGB GLX visual

What is my next step as this doesn't seem right.

Thanks,

Dan S

---

