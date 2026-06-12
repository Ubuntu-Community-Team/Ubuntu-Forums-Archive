---
title: "[SOLVED] &amp;quot;Input not supported&amp;quot; on fullscreen applications"
date: 2008-06-18
forum: Multimedia Software
---

### Post by deinonychai on 2008-06-18
I recently clean-installed 8.04 on my desktop, and am unable to get any natively fullscreen application to display on my monitor (17-inch Acer, defaults to 1440x900 & 50Hz refresh) with a NVIDIA 7900GS video card, non-free drivers up to date.  I never had this problem while running 7.10, but now my screen will go black and flash an "Input not supported" every time I try to open up a fullscreen app.

I tried to install and run the Linux port of Neverwinter Nights on my desktop and received this error.  I tried a few games from the repository (like Tuxracer) to see if it was program specific, and I run into the same trouble there.  I'm sure it's probably a simple configuration problem at the moment, but I'm lost.  Any help would be appreciated.

---

### Post by Pjotr123 on 2008-06-18
Do this:

1. Disable visual effects
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

2. Check if you've really got all of the codecs:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

The 50 Hz thing:
The restricted Nvidia driver uses fake Hz values, in order to uniquely identify a screen: 50 or 51 Hz. The real Hz value is different and can be checked in the BIOS of the monitor itself (if you have a separate monitor and not a laptop). Use the physical buttons on the monitor for this. It's probably 60 or 75 Hz in reality.

So it's allright. But confusing it is: about a year ago, I've had an e-mail exchange with an Nvidia service employee about this. It appears that Nvidia blames Ubuntu. Whereas the Ubuntu developers blame Nvidia. Anyway, it's only a cosmetic issue and has no intrinsic importance.

Greeting, Pjotr.

---

### Post by deinonychai on 2008-06-20
Thanks for the reply.  I'd have responded earlier, but a new laptop of mine just gave up its ghost five days into its tenure with me (wouldn't boot past GRUB, 100% fail in memtest... sent it back and picked up something new) so I've been distracted.

Anyhow, back to business:

I followed the steps, and still can't load fullscreen applications without my input going awry.  When I'm in a regularly windowed application, I can go into fullscreen mode without a problem.  I just can't load anything that natively wants my entire screen without my monitor going black and bouncing its "Input not supported" at me.

Thanks, by the way, for clearing up the thing with the monitor Hz.  When I first bought this monitor of mine, the pamphlet gave me strict and loud warnings not to exceed or in any way deviate from a particular Hz setting (I believe it was 70).  When I didn't see that option whilst configuring my first Ubuntu machine a year ago, I thought it meant bad news.  But many moons later, my monitor lives, and I'm a bit less confused about one more thing.  

Now, if I could figure out what's causing this fullscreen problem, I'd be in business.  And it's an unusual one, because I had no trouble in 7.10 running all sorts of goofy stuff in compiz.  My hardware hasn't changed since then, so... who knows...

---

### Post by firfin on 2008-07-03
The problem is only game related? Or do you have other 'fullscreen' applications?  

To me it seems pretty obvious the videocards start outputting videosignals to the monitor is just can't handle (e.g. too high Hz, wierd resolution/Hz combinations.) For safety reasons the monitor says 'Input not supported' instead of blowing up in your face :-D

You might want to try different videosetting for the games.
Or try to run the games in windowed mode. 
I believe NWN has a config file you can edit to let you do just that. The results of these test should help clarify where the problem lies.

---

### Post by deinonychai on 2008-08-08
> **firfin said:**
> The problem is only game related? Or do you have other 'fullscreen' applications?  

To me it seems pretty obvious the videocards start outputting videosignals to the monitor is just can't handle (e.g. too high Hz, wierd resolution/Hz combinations.) For safety reasons the monitor says 'Input not supported' instead of blowing up in your face :-D

You might want to try different videosetting for the games.
Or try to run the games in windowed mode. 
I believe NWN has a config file you can edit to let you do just that. The results of these test should help clarify where the problem lies.

I wasn't able to determine whether or not the problem was exclusively game-related: the only applications I would ever run in full-screen mode were games.

Before upgrading to 8.04, all these applications ran just swimmingly.  I never had a problem one way or the other.  Running NWN in windowed-mode worked just fine too, so I wasn't entirely sure what was going on.

But... I kept on digging about on the forums here, and eventually came across the solution:

[http://ubuntuforums.org/showthread.php?t=765451](http://ubuntuforums.org/showthread.php?t=765451)

As it turns out, the problem is with the video driver package nvidia-glx-new.  As soon as I put nvidia-glx in its place, all of my problems were resolved.  And while I'm certain that there's probably some room to work with nvidia-glx-new to get it running properly, for the time being I'm just happy to be up and running.

Thanks for the input everybody!  NWN is pretty much the only game I play when I get the occasional chance, so I'm glad its working.  It runs abysmally in Windows due to some unorthodox hardware conflicts between the program and my processor, but seamlessly (long at last) here in Ubuntu.

---

