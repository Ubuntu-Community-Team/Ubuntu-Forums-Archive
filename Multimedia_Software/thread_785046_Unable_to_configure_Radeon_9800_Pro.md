---
title: "Unable to configure Radeon 9800 Pro"
date: 2008-05-07
forum: Multimedia Software
---

### Post by Puff0rx on 2008-05-07
Hi everyone, I'm a new poster on here and first time user of linux. I moved over to Ubuntu with the release of Hardy Heron, and after it froze a few seconds after start-up finished, I frustratedly used Windows XP until I could figure out what was wrong. It turns out it was the ATI Drivers I was using, so I installed the fglrx and everything seemed to be running fine. I realised after a while that I was running only the default drivers, and that everything was actually running very badly (I'd assumed Ubuntu is just a resource hog :P)

So I researched a bit more and found out that there's a lovely script called "Envy" that'd solve all my problems, so I installed and ran that. It detected my hardware all right (Radeon 9800 Pro outputting to Acer AL511) and rebooted, looking all official-like. Unfortunately, after it was done rebooting this happens in the following order:

1. I get a few flashes of my monitor (going from a blank screen, to my "No Input" sign, and repeating)

2. I get a very strange screen with a really glitchy ubuntu logo and a few green horizontal lines. This lasts for a few seconds.

3. I get the "Ubuntu is running in low-graphics mode" dialog box.

I try to put it my hardware, but every time I do it gives me this awful "Configuration test failed" error. How do I set the computer to use my proper video card? Help!

---

### Post by primlinOS on 2008-05-18
I have the same card, and am having some fairly serious problems with video as well.  I run glxgears and am getting framerates around 100FPS (not good).  I think this has something to do with this post as well:

[http://ubuntuforums.org/showthread.php?t=781839](http://ubuntuforums.org/showthread.php?t=781839)

I'll let you know if I figure anything out.  For the time being, go into admin -> hardware drivers and select the proprietary ati driver, and restart.  This should undo whatever problem envy has caused.

---

