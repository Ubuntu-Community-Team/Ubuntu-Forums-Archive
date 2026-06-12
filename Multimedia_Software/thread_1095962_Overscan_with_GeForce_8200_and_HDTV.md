---
title: "Overscan with GeForce 8200 and HDTV"
date: 2009-03-14
forum: Multimedia Software
---

### Post by daveisfera on 2009-03-14
I just installed Mythbuntu 8.10 on a MSI K9N2GM and hooked it up to my HDTV. It appears that there is a significant amount of overscan going on so I can't see the Gnome toolbar at the top of the screen (or anything from the sides or bottom either) when I exit the MythTV frontend.

I tried updating to the 180 NVidia driver and it didn't fix the problem, and I don't see anything in the nvidia-settings options to fix this. Does anyone have any ideas on what I can do to be able to see everything on my TV?

Thanks,
Dave

---

### Post by bobqwerty on 2009-04-16
[http://ubuntuforums.org/showthread.php?t=395101]("http://ubuntuforums.org/showthread.php?t=395101")

It might be worth looking at the thread above, I am going to try it tonight looks like you down grade the resolution on your display to get it to fit and get rid of the overscan. I have the same issue with a Phillips 32inch LCD..

So hope that helps...

Cheers

Glenn

Sorry I tried this tonight and had no joy it seems to ignore the custom resolution.... Does anyone know how to fix this overscan problem, there seems to be a lot of people suffering due to this problem..

HELP!!!!

---

### Post by daveisfera on 2009-04-16
I actually found [these instructions](http://ubuntuforums.org/showthread.php?t=1003099&page=2), but it didn't do what the person said it would (I never saw I gray screen with an X). I don't know if that's because it's xfce instead of Gnome, because of the upgrade to X.org 1.6, or something else completely.

---

### Post by bobqwerty on 2009-04-17
> **daveisfera said:**
> I actually found [these instructions](http://ubuntuforums.org/showthread.php?t=1003099&page=2), but it didn't do what the person said it would (I never saw I gray screen with an X). I don't know if that's because it's xfce instead of Gnome, because of the upgrade to X.org 1.6, or something else completely.



daveisfera

I am going to try it tonight. It is interesting because i noticed that the display in the log states "Building ModePool for Philips FTV (DFP-0)" which is the same name my Television gets detected as. So I will go home tonight and have another go. It is really pissing me off I have gone home from work for lunch the last 3 days trying something new each time with no success.


Hopefully this one works..

Cheers

Glenn

---

### Post by bobqwerty on 2009-04-17
> **daveisfera said:**
> I actually found [these instructions](http://ubuntuforums.org/showthread.php?t=1003099&page=2), but it didn't do what the person said it would (I never saw I gray screen with an X). I don't know if that's because it's xfce instead of Gnome, because of the upgrade to X.org 1.6, or something else completely.
I tried the intructions you sent me and I am up and running with no more overscan. The instruction do work, give it another try. Overscan fixed now need to get rid of some flickering lines though the screen every so often i think it is the nvidia driver though but going to have a look around..

Cheers

Glenn

---

### Post by bobqwerty on 2009-04-18
> **daveisfera said:**
> I just installed Mythbuntu 8.10 on a MSI K9N2GM and hooked it up to my HDTV. It appears that there is a significant amount of overscan going on so I can't see the Gnome toolbar at the top of the screen (or anything from the sides or bottom either) when I exit the MythTV frontend.

I tried updating to the 180 NVidia driver and it didn't fix the problem, and I don't see anything in the nvidia-settings options to fix this. Does anyone have any ideas on what I can do to be able to see everything on my TV?

Thanks,
Dave
You can actually use the technique in the instructions without the gray X. You just have to start and stop X windows instead of typing X. The only reason you type X is to get a X windows screen up to show you how you have moved the screen each time.   So what ever distribution you have as long as you can start and top X windows and check the screen movement you should be able to get it to work..

Cheers

Glenn

---

### Post by bobqwerty on 2009-04-18
> **daveisfera said:**
> I actually found [these instructions](http://ubuntuforums.org/showthread.php?t=1003099&page=2), but it didn't do what the person said it would (I never saw I gray screen with an X). I don't know if that's because it's xfce instead of Gnome, because of the upgrade to X.org 1.6, or something else completely.
You can actually use the technique in the instructions without the gray X. You just have to start and stop X windows instead of typing X. The only reason you type X is to get a X windows screen up to show you how you have moved the screen each time. So what ever distribution you have as long as you can start and top X windows and check the screen movement you should be able to get it to work..

Cheers

Glenn

---

### Post by mrouija4201 on 2009-04-19
I just did the instructions to remove overscan on my setup (Quadro FX 3450 and Panasonic 720p TV) and now my display is nearly perfect. This may not be the right place to ask, but rather than necro the other thread I'll put it here.

There is a slight amount of whitespace left/right of the display and getting rid of it is proving to be quite a pain. Currently, this is what my modeline reads:
```
ModeLine       "1280x720" 74.18 1200 1355 1495 1650 685 710 715 750 +hsync +vsync
```
My problem is this: If I change H1 to 1205 or even 1210, which would get rid of the whitespace, when I start X it comes up 1024x768 even without a modeline for that resolution. I've tried toying with it a bit, but getting this far has me pleased enough to set down the keyboard awhile and pick someone else's brain.

Any suggestions?

---

### Post by David Valentine on 2009-04-27
The posted instructions worked for me, but there's a way to circumvent the iterations needed to get the right screen size if you're running mythtv.  The following works for Mythbuntu 9.04.

1.  Follow the directions up through generating the new modelines in /etc/X11/xorg.conf.  You can probably skip the low resolution modeline as we won't use it.  
2.  Start MythTV.  From the top menu, navigate to Utilities/Setup, then Setup, then Screen Setup Wizards.  
3.  Use down and right arrows while watching the upper left corner of your screen.  A shaded right triangle will appear, with the right angle highlighted in white.  Use your arrows to position the point of the right angle at the upper left corner of your screen.  Hit enter, then do the same thing for the lower right corner of your screen.
4.  Write down the Size and Offset numbers.  
5.  Edit /etc/X11/xorg.conf.  The two Size numbers become your new H1 and V1 in your high resolution modeline.  Then subtract the first offset number from both H2 and H3 to get your new H2 and H3 values.  Finally, subtract the second offset number from both V2 and V3 to get your new V2 and V3 values.  Save xorg.conf.
6.  Restart, and enjoy your right-sized screen.

---

