---
title: "Weird Weird video problem.."
date: 2011-10-11
forum: Multimedia Software
---

### Post by Druegan on 2011-10-11
Hi folks.

I have a very strange video problem..screen flicker/strange redrawing, and I need some help with it.

To start, I'm running Ubuntu 10.10 64 bit, nVidia GeForce GTX 460 video card, Acer P235H widescreen monitor, Biostar A770E3 mainboard, 8 gigs of memory, 650w PSU.. AMD Phenom II X6 1055T Processor.  Also using the latest nVidia proprietary drivers (version 280.13) 

This problem first cropped up a few weeks ago, around the time the latest Compiz update came down the pipe through the Update Manager. System had been running just fine for 6 months prior.

Basically what happens is that upon visiting certain web pages, or (and this is weird) viewing certain .png images with a specific shade of blue in them... (told you it was weird..)   My entire destop display develops a flicker.  On certain very bad websites, a horizontal line develops across the center of my screen, and begins to "bleach out" along that line, then it flashes to black, then re-displays and begins again.  Other web pages produce an effect where the top half of the display is replicated down over the bottom half amidst a good deal of flickering.

I'd posted about this in general help a week ago, and thought I'd resolved it.. I wound up installing the 280.13 nVidia drivers and reinstalling Compiz, and it seemed to fix it till my next reboot.. now the issue is back as if nothing ever had changed.

Here's a link to the previous thread with details on what I've tried to fix it with.. [http://ubuntuforums.org/showthread.php?t=1855153]("http://ubuntuforums.org/showthread.php?t=1855153")

Previously, I just thought it was a problem with certain web page code.. but today I discovered a .png file that produces the same effect, but only when a certain shade of blue is attempted to be rendered.. (as in, if I look at the file through EOG, and the blue patch is visible, the screen flickers.. if I zoom in on the blue patch, it flickers *badly*.. but if I zoom in on the non-blue part, it stops.)  Flicker also occurs, as I mentioned in the other thread, when certain elements of websites are visible.. but not if I scroll down past them.  Disabling javascript via noscript has no effect, neither does having a flash plugin installed or not, as far as I can tell.  

And this new thing with the blue image is just.. weird.

It is apparently sensitive enough to the color that just having it up on the GIMP color selection palate is enough to trigger a small degree of screen flicker.  RGB values: R: 0 G:255 B: 255, with Hue of 180, and Saturation and Value both of 100.   And minimizing the window with the color in it causes the flickering to stop.

Has anybody ever had any similar problems, or might somebody be able to advise me on how to start troubleshooting what this could be?  I've run through everything I know how to do with Linux graphics.. which, admittedly, isn't much.

Is there any more information I can provide that might be of help?

Any assistance at all would be greatly appreciated.. this is beginning to drive me batty.

Regards, 
   Druegan

---

### Post by WasMeHere on 2011-10-11
> This problem first cropped up a few weeks ago, around the time the latest Compiz update came down the pipe through the Update Manager. System had been running just fine for 6 months prior.


I suggest you do some testing to find out if it related to software (as you suspect) or if it could be a hardware problem.

-What about different screen resolutions?
-What if you view files with that colour from a live system booted from CD or USB? What about different screen resolutions?

Have fun finding out :-)
Olle

---

### Post by Druegan on 2011-10-12
Ran the "System Testing" applet.. did video and monitor..  everything went swimmingly.  

So on a Lark, I uninstalled Compiz completely through Synaptic.. and rebooted, just to be sure.  

And lo, everything was fine for a bit.. I was looking at the offending picture on full zoom, and the most problem causing webpage at the same time, and nothing was amiss.. not a hint of flicker..

Now about 5 minutes have passed, and I go to the tab on the problem webpage, and all of a sudden it starts to do the flicker problem again.. with no Compiz installed on the machine. So I'm pretty sure now it's not Compiz.. may be a hardware issue.. but also may be some of this "adaptive clocking" nonsense with nvidia.. gonna try to find a way to kill PowerMizer functions and see where that takes me.

---

### Post by WasMeHere on 2011-10-12
Yes, it could be the Powermizer, but it could also be some electronic component failing when it is getting warm after a few minutes.

-What if you view files with that colour *from a live system* booted from CD or USB? Without nvidia's graphics driver.

- What about different screen resolutions?

- Test another video output on your card! I guess you have at least two connectors!

- Can you borrow another monitor screen to test if the screen might be failing?

- Do you have another graphics card (from an old computer or from a friend's computer)?

---

