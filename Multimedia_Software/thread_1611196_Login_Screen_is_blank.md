---
title: "Login Screen is blank"
date: 2010-11-01
forum: Multimedia Software
---

### Post by boomcat on 2010-11-01
I just got rid of my Dell P990 CRT and replaced it with a Samsung B2330H LCD. I got the resolution changed to 1920x1080 at 60hz through System/Preferences/Monitors and the new display looks great! There is one problem, though: the computer boots into a resolution that is not supported by the new monitor. As a result, the login screen is blank. The monitor puts a little floating message on the screen that says, "Optimum Resolution is 1920x1080..." When I start up, I hear the "bongo sound" and I hit ENTER, then enter my password, then ENTER again, and the computer desktop appears in 1920x1080 and all is well. But how do I get the login screen to appear in 1920x1080?


This is Ubuntu 10.4, using the Intel onboard card. Here's the output of lspci:

```
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)

00:02.1 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
```

I have installed the Startup Manager, but it does not allow 1920x1080 to be selected. I have also tried using Startup Manager to select other resolutions, but the login screen is still blank.

Isn't there some trick to force the login screen to appear in a specific resolution using xrandr? What file does this command go into? Maybe my old configuration files from my Dell monitor are interfering?

Any help would be gratefully received!

---

### Post by boomcat on 2010-11-01
The solution I used was to edit my xorg.conf file and add the appropriate modeline, which I found here:

[http://www.mythtv.org/wiki/Modeline_Database#EDID_Modelines_.28Data_from_your_Monitor.29](http://www.mythtv.org/wiki/Modeline_Database#EDID_Modelines_.28Data_from_your_Monitor.29)

The modeline info can be found in the file /var/log/Xorg.0.log. Mine was:

```
Modeline "1920x1080_60.00" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
```

Then I added the following line, just beneath the modeline entry, to force the login screen into 1920x1080:

```
Option	 "PreferredMode" "1920x1080_60.00"
```

Works for me.

---

