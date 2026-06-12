---
title: "Mythtv GUI over sized on new tv"
date: 2015-06-07
forum: Mythbuntu
---

### Post by benlyboy on 2015-06-07
I'm hoping someone can help.
 I just got a new larger TV, but when go to myth on it the GUI for both the front and back ends is to large. I'm losing the edge all the way around. Video playback seems ok.
I found a screen setup wizard on the myth configuration page but when I go into it it just seems to show the background image but nothing else happen, and it also seems to lock up the front end.
I'm using mythbuntu 14.04. 
Any help or ideas would be great thank

---

### Post by blm-ubunet on 2015-06-07
The mythtv screen setup wizard may just have the "corner handles" of screen overscanned so can't see them.
There is a settings tab "Playback/Video" where you can set size with actual numbers in textbox.

Video playback could seem okay because it is shot with overscan in mind &/or doesn't matter if you cut the margins off.
Could also be because the video playback is using a different video playback mode &/or screen size. 

Lots of TVs have default overscan for external inputs.
Best soln is the change the TV settings for the external input you have used.
All TV manufacturers have use different obscure terms for the same thing (justscan - Samsung?).

Need to have a search of the input menus on TV..

Some TVs require the input to have a specific name to get 1-to-1 pixel mapping & no internal scaling.

If all that fails then you have to use over/underscan viewport settings for your nVidia card.
The GUI for this only appears in later drivers, so for your old card you need to use nvidia-settings from cmd line or use xorg.conf. This is not a pleasant experience.

---

### Post by hollywoodpete on 2015-06-07
I have had similar problems in the past. Is you desktop on Ubuntu fine? Which TV and video card are you using? Usually for me it has been an aspect ratio on the TV that fixed my issue

---

### Post by benlyboy on 2015-06-07
Now I have really got my self in to to trouble, hope someone can help. I went in and changed the settings in settings appearance, I changed one of the setting from 0 now I can't see my front end I tried mythfrontend --reset but it didn't help is there any fixing this?
Editing this to let all know I was able to fix my screw up, I came up with the idea of using an old very low resolution monitor I had this made the image large enough so that I was able to navigate back and fix my screw up

---

### Post by blm-ubunet on 2015-06-08
Assuming you are using mythbuntu auto-spawning scripts ..
Try starting mythtv from terminal (not console) with:
```
mythfrontend.real --geometry 1280x1024
```
I use that when run mythfrontend over ssh on netbook size screen.

Is it possible that the mythbuntu mythfrontend "script" accepts cmd line options as well.

other useless overrides are
[https://www.mythtv.org/wiki/Override_settings](https://www.mythtv.org/wiki/Override_settings)

---

### Post by benlyboy on 2015-06-10
Thanks for the info.
I have fix my problem.
I took another look and realized that everything including the desk top was over scanning, so I decided to take a different approach. I went to google and googled my tv ( a Samsung) and over scanning and there it was had to change the name of the device connected to the HTMI port, and it just worked, that simple. 
feel kinda silly that it was that simple but there you go.. :-)
Thanks again for all the help

---

### Post by Lester_Burnham on 2015-06-11
Hi,

Did you have to change the "device type" connected or just edit the name of the device connected.
I've found selecting "just scan" in the aspect ratio menu on previous Samsungs fixed overscan.

Lester

---

