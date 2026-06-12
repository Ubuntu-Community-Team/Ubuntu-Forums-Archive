---
title: "Problem w/ Nvidia Video Card and graphical glitching"
date: 2009-03-14
forum: Multimedia Software
---

### Post by lordofduct on 2009-03-14
So a couple days ago the worst thing happened. Both my computers overheated to unbarable temperatures. One of them hit 110C... holy crap!

This machine here was sitting in the mid 80s both in the GPU and CPU. The main problem was one of the little bits that hold the heatsink down broke and it created some air space... and well to make a long story short... I had to pull apart everything and reseat all the heatsinks.

I did my videocard as a fair measure as well as the temperature of it was rather high as well.



Now I restart and I am greeted with this weird issue where one of my two monitors has these weird vertical lines through it. It's like every other vertical column of pixels has to much blue, and if say I have a window open over a white window it is like haloed on the left and right with these repeating blue vertical lines that pulsate.

CRAP, I broke my card... so I thought. BUT I'm running dual monitor. And my left screen is working just fine! I swap the DVI ports and still this monitor is acting weird.

Now the thing is this monitor acting up is the Dell 30inch monitor at 2560x1600. It requires the video card to perform all the scaling and the sort, as it doesn't have a built in video converter and upscaler. I'm thinking this might be playing a role in the whole issue.

Secondly now when I open up 'nvidia-settings' tool box through the terminal I get this long error reported about being unable to assign attributes from my 'nvidia-settings-rc' file for this screen. All the lines pertaining to the other monitor (which looks fine) don't have a problem, it ONLY refers to lines referring to this monitor with the issue.

The error is as follows, it's long, but it's error after error reporting yet another line failing:
> 
BashMyHead : sudo nvidia-settings

ERROR: Cannot open display 'BEDROOM:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 23 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 24 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 25 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 26 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 27 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 28 of configuration
       file '/home/dylan/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 29 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 30 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 31 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 32 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 33 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 34 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 35 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 36 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 37 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 38 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 39 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 40 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 41 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 42 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 43 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 44 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 45 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 46 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 47 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 48 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 49 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       50 of configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       51 of configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/dylan/.nvidia-settings-rc' (no Display
       connection).

BashMyHead : 



Note it says "no Display connection"... huh?

Has anyone seen this?

---

