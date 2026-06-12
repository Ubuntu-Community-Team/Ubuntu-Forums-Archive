---
title: "Hardware GLX on 3D Rage Pro (Breezy)?"
date: 2005-11-04
forum: Multimedia &amp; Video
---

### Post by fuzzix on 2005-11-04
This was originally going to be a reply in [this thread](http://ubuntuforums.org/showthread.php?t=55136&highlight=ati+rage+pro+glx) but it was on the Hoary forum :) ...

I'd be interested to find out what sort of frames are possible from this card - I'm at my brother's machine right now (I installed Breezy here yesterday) which has a 2x AGP 4MB ATi 3D Rage Pro Turbo on board. The PSU isn't beefy enough to power the spare PCI GeForce 2 I have (damn you, Dell :-x) so we're stuck with it. Is there an Xorg driver I should be using besides "ati" in the "Device" section?

When I run glxgears it goes very smoothly for about 2 seconds, then the cogs slow down and stutter badly - this is at 1024x768x32@85Hz, 640x480x16@85Hz and everything in between. There's no fps info echoed at all.

Here's xorg.conf and output of glxinfo:

[http://pastebin.com/417137](http://pastebin.com/417137)

I'm wondering about the "client glx vendor string" in glxinfo - should that be "ati" or is that just the case with proprietary modules like fglrx? If more info is required please ask.

Thanks.

---

### Post by John.Michael.Kane on 2005-11-04
You may want to post in the Thread you listed and see if anyone has more info from what i can see it may have to do with your card having 4megs of mem.

---

### Post by fuzzix on 2005-11-04
I know the RAM is a severe limitation which is why I tried glxgears at a low res/bpp. I know I'm not going to get a good Q3A session going on this thing :)

I'll throw this at the other thread and see if anyone has further info.

I was looking at [http://gatos.sourceforge.net/ati.2.php](http://gatos.sourceforge.net/ati.2.php) which mentions GLX support for a Rage 128...

---

### Post by Navyblue on 2005-11-04
I have an ATI Rage pro on a P2 400 MHz 384 MB RAM (it's a Dell too btw :)), If my memory serves, I think it used to run smoothly at about 150 fps. But I just tried it ust now and for some reason it moves jerkily at around 95 fps. (this reading would probably shock those 3D freak out there :p)

---

### Post by fuzzix on 2005-11-04
I came across this the other day...

[http://utah-glx.sourceforge.net/](http://utah-glx.sourceforge.net/) / [http://sourceforge.net/projects/utah-glx](http://sourceforge.net/projects/utah-glx)

...but it looks like it hasn't been updaten in a long time... I'm wary about trying it on Xorg. I'm not too keen on compiling code on that box at all, truth be told - it's not mine so if stuff goes wrong I'm not always there to fix it. Stability is the priority.

---

### Post by holomate on 2005-11-27
I have a Dell GX1 (pentium 3 I believe) with onboard video, which happens to be a Rage Pro chipset. It is also running the glxgears very slowly and I've noticed other degrading performance while running the included screensavers, etc. I'm not sure how to get a fps from glxgears (I keep interrupting it before it finishes because it's taking 2-seconds per gear turn)

I'm no expert, but it almost seems as if the included driver isn't running any kind of hardware acceleration or something. I'll take a look inside to see if I can add any additional memory, however it's an onboard chipset for me, so probably not. This same system on a flavor of windows can run the OpenGL screensavers at a much better speed.

I reduced the screen from 1024x768 to 800x600 and the perfomance on glxgears got substantially better for about 9 seconds and then began lagging again.

I also have a 2nd computer that's a K6-2/450mhz machine and has an ATI All In Wonder Pro, which would also use the Rage Pro Chipset. It is not currently running Ubuntu because I've been experimenting with it, but it *had* Breezy on it a couple of weeks ago and the video performance was really really terrible.

---

