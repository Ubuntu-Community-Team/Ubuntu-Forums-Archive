---
title: "Videos cause blank screen"
date: 2008-07-31
forum: Multimedia Software
---

### Post by Garrulousbrevity on 2008-07-31
So, I don't know exactly when this started, but when I try to play any movie file, in any player, the player will open up, and start the video, but, regardless of whether or not the video was in full screen, blank the entire screen to one entire color.  Usually blue or green or white.  The color seems slightly random, as the same video can cause a different color with different attempts. 

When the screen is blank, the keyboard stops responding, but the sound from the video continues.  If I hit Ctrl+alt+backspace, the sound stops... but that's about it. 

I'm guessing the problem is either the codec or my video drivers, but I'm not sure what to do with them.  

I have a macbook, so the video card is an Intel onboard card.  I never had this problem with my desktop, which has a nVidia card, yet I largely treat the two computers the same.  So I suspect that the driver has something to do with it. 

Any help would be appreciated.

---

### Post by tuxxy on 2008-07-31
You are not likely to run into any problems with your nvidia card, your problem does sound like it could be the onboard chip.

---

### Post by Garrulousbrevity on 2008-07-31
So, I was fooling around... and instead of having the default xorg.conf that's new to Gutsy, I went and put in my driver, i810, and that got it working, but messed up my resolution.  I then got 915resolution from the repo and the resolution was fine. 

So, now I can play movies, but I can't do anything that involves changing the resolution... Most notably running Starcraft through Wine.  I admit that I don't do that as often, but I do from time to time.  

Anyway to get both going at the same time?

---

### Post by Garrulousbrevity on 2008-07-31
Update: This fix for videos just broke suspend.  After coming out, the brightness is much lower than it can get while working normally.  I can see faint shadows of the proper windows, but the brightness adjustment buttons do squat.  Bah.

---

### Post by Garrulousbrevity on 2008-08-01
Right.  Um.  So after purging all codec related objects, I reinstalled totem-gstreamer and only totem-gstreamer.  I then tried to play a movie, and it autodetected what it needed from the repo, and then things started working.  

I'm not... exactly sure why... but I'll take it.

---

### Post by Garrulousbrevity on 2008-08-05
So restarting my computer brought it back to square one.  If I do the same things again I can get it working... again... but only until another restart. 

Which is irritating.

---

### Post by vanquishedangel on 2008-11-22
I hope this is not too late but I have been tirelessly looking to get my webcam to work in ubuntu intrepid 8.10 to the point of pulling my hair out but I didn't give up and if this doesn't help you then maybe it will help someone like me but I found this on another web page and compiled it from others and it worked like a dream, I will copy and paste the article

The only way I have managed to make totem show the videos was to set the output on the video tab of gstreamer-properties to "X Window System (No Xv)".

How to change the properties in gstreamer: press alt, f2. Then type gstreamer-properties, then go to the video tab and under default imput change the plugin to "x window system ( no xv)" Now start cheese.

No videos worked in totem before incuding webcams but now all of them work the problem was totem. since theese other programs use totem.

---

