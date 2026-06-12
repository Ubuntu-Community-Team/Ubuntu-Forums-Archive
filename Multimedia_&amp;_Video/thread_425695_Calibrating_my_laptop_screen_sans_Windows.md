---
title: "Calibrating my laptop screen sans Windows"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by samppi on 2007-04-27
Hello everybody,

I'm not very knowledgable about computers, but I've been happily using Ubuntu for about two years now on my aging laptop. However, my eyes have always hurt when I look at the monitor for too long, and now I realize it's because of its calibration.

However, I'm having trouble figuring out how to fix this. When I tried to find information on calibrating my monitor, I could only find methods involving Windows and Windows calibration programs in the same computer--and I don't have Windows in this laptop. Also, since it's a laptop, the screen is built in and lacks any adjustment buttons except a limited brightness control, so I can't adjust the contrast.

So does anyone have any way of adjusting my monitor without Windows (and built-in contrast buttons)? :confused: 

(By the way, here are the details of my monitor's colors--I'm using [this page]("http://epaperpress.com/monitorcal/index.html"):

When the laptop's brightness adjustment is set to highest:
Pure black is displayed too bright, but dark grays are still distinguishable.
Pure white looks like white; light grays, however, are almost indistinguishable from each other--I have to look at the screen from an angle to see a difference.

When the laptop's brightness adjustment is set to lowest:
Pure black looks more like black, but is still too bright; dark grays are still distinguishable.
Pure white looks like a bright gray; light grays are even more indistinguishable from one another. As a result, everything looks murky.)

Using [Norman Koren's gamma/black-level chart]("http://www.normankoren.com/Gamma_black_new.png"), it looks like its gamma is also messed up too. It doesn't match anywhere on the chart.)

---

### Post by Yettie on 2007-05-04
I am having similar problems. Having just come from a Windows setup where I was used to having a utility, called 'Quick Gamma', to adjust the settings of my laptop LCD I was looking for something like it for Linux. Norman Koren, in his web-site, mentions [COLOR="Red"]'Monica'[/COLOR] which is now available in a version called [COLOR="Red"]'GammaPage'[/COLOR] ([http://www.pcbypaul.com/software/GAMMApage.html)](http://www.pcbypaul.com/software/GAMMApage.html)). I have tried it and it works quite well. It has an option to save the settings on rebooting, although I haven't been able to get this to work yet. I get this error message - 

Logon type cannot be determined,
therefore GAMMApage does not know
where to save the gamma-adjusting 
command to be run on X-startup.

The "Save" button will be disabled.
In its place, the "Exit" button will close the program but keep your gamma adjustments until your X-session ends.

See the "HELP" pages for further instructions.

I'm sure there must be a way around this but I haven't found it yet.[PHP][/PHP]

---

### Post by Pixtu on 2007-05-29
It seems that GammaPage only expects certain .rc files. If you have one that is not included, such as .bashrc, then you get this problem. However, all it really does is set the values for the xgamma utility. Unless GammaPage is changed the only 'fix' for it is to use it to work out the values that work for you, then set them yourself with xgamma. If you put the xgamma settings into .bashrc then they will be used every time you login.

.bashrc can be found in your Home folder but you will need to show hidden files - press Ctrl H to show them. Then open .bashrc to edit it add add the following to the end :-

[I]xgamma -gamma X.X 2> /dev/null
[/I]
This works where X.X is the value for all RGB values according to GammaPage. If GammaPage indicates a colour cast and you require different values then use :-

[I]xgamma -rgamma X.X -ggamma Y.Y -bgamma Z.Z
[/I]
where X, Y and Z represent the RGB values respectively.

For those that don't know the *2> /dev/null* part just redirects all the output messages to the null device (it throws them away).

---

