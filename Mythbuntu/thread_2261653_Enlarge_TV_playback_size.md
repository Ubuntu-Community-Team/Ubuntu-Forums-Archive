---
title: "Enlarge TV playback size"
date: 2015-01-20
forum: Mythbuntu
---

### Post by davefor2 on 2015-01-20
Mythbuntu 14.04
Nvidia GeForce GT 610

Is there a way to enlarge tv playback size

I have my mythfrontend connected to a TV.
It is detected my nvidia settings as 1360x768
It looks great but noticed that the top and the bottom have
about 1" black bar on top and bottom. The sides are ok.
Is there a way to enlarge the image to remove the borders?
I tried using GUI size for TV playback size but didn't seem to do anything.

Thanks

---

### Post by SeijiSensei on 2015-01-20
What if you choose 1280x720 as the display resolution rather than 1360x768?  Do the bars go away?  That's the resolution of the "720p" standard for television.  1360x768 might work with monitors, but TVs often prefer the standard resolutions like 720p or 1080p, 1920x1080.  Can your display adapter go to 1920x1080?  How does that look?

If the bars persist, take a look at the display options for the TV itself.  Choose the "full pixel" or similar setting if it's available.

---

### Post by davefor2 on 2015-01-21
I tried 1280x720 but the size between 1360x768 didn't change much. I also tried 1920x1080 but the image was horrible,
there were white lines through anything dark like black letters. Is there a way to zoom the size a little to remove the bars?
I found underscan under nvidia settings but this only seemed to make things smaller.
I have read about viewport setting but most people use this to correct for overscan issues.
Also my current TV doesn't have any advanced video settings.

---

### Post by SeijiSensei on 2015-01-21
> **davefor2 said:**
> Also my current TV doesn't have any advanced video settings.

You sure it doesn't have a zoom option?  Most HDTVs do.

---

### Post by davefor2 on 2015-01-21
I checked the users manual and only thing I can change is wide or normal.

---

### Post by tylersontag on 2015-01-22
I have a similar problem.  After upgrading from 12.04 to 14.04 my NVidia driers needed updating.  After doing so 1900x1080 was no longer listed for my VGA out...  it looks like it was no longer recognizing my TV.  After trying to manually add my old resolution and failing I decided to try out my video card's HDMI out (which had previously never worked right w/ sound)

To my surprise it worked great, HOWEVER, the HDMI out signal is overscanned on my TV, I loose about 50 pixels all the way around.    My TV doesn't have any way to adjust the overscan so i'm curious if anyone has any other suggestions for my situation?

---

### Post by khPWXxF on 2015-01-22
Any clues here?
 
[http://ubuntuforums.org/showthread.php?t=2258886](http://ubuntuforums.org/showthread.php?t=2258886)
 
xrandr performed magic!
 
Phil

---

### Post by tgm4883 on 2015-01-22
> **tylersontag said:**
> I have a similar problem.  After upgrading from 12.04 to 14.04 my NVidia driers needed updating.  After doing so 1900x1080 was no longer listed for my VGA out...  it looks like it was no longer recognizing my TV.  After trying to manually add my old resolution and failing I decided to try out my video card's HDMI out (which had previously never worked right w/ sound)

To my surprise it worked great, HOWEVER, the HDMI out signal is overscanned on my TV, I loose about 50 pixels all the way around.    My TV doesn't have any way to adjust the overscan so i'm curious if anyone has any other suggestions for my situation?

Does your TV have multiple HDMI modes? Mine does the same thing and doesn't call it overscan. It calls it HDMI mode 1 and HDMI mode 2 (mode 2 gets rid of the overscan). If neither of those work, you can go into the frontend and do the screen setup wizard.

---

### Post by davefor2 on 2015-01-22
My TV doesn't have HDMI modes. I will try xrandr and the screen setup wizard.
Thanks for the help and if this doesn't work it may be time to buy a new TV.

---

### Post by Lester_Burnham on 2015-01-22
Hi,
What is the Brand/model of TV.
Lester

---

### Post by davefor2 on 2015-01-23
I was able to get the video resized to fit the screen. 
What I changed was in Setup > Appearance > Video Mode Settings
I checked off Separate video modes for GUI and TV playback
Change default to:
GUI: 1360X768 Video Output: 1360x768 Rate:Auto Aspect:16x9
Not sure why nvidia settings at 1360x768 wouldn't do the same.
I am going to play around a little more because when I change the 
above settings the picture doesn't look a sharp as it did before.

Also I would have to check the model number but the brand is AOC and I think is 32" LCD.

---

### Post by Lester_Burnham on 2015-01-23
Hi,

What do you get when you run ```
xrandr
```
It should tell you what resolutions your TV can do.
From what I've read, it looks like 1366x768 (native) & 1280x720

Lester

---

### Post by khPWXxF on 2015-01-27
Davefor2:
After you altered the settings in frontend > setup > appearance, did you see any signs of the bug whereby you have the xfce menu bar across the top of the screen?
Phil

---

### Post by davefor2 on 2015-01-28
Hi Phil

No, haven't had any issues with the menu bar at all. I have been using this setup for a few days now and
everything is working fine. In my previous post I said that things didn't look as sharp, but after rebooting it looks
ok now.

---

