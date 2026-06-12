---
title: "nVidia driver Twinview Problem"
date: 2009-09-10
forum: Multimedia Software
---

### Post by Russell_S on 2009-09-10
Hi, I have just replaced my ATI graphics card with a new nVidia GTS250 and found that to enable the visual effects in Ubuntu I needed to load the proprietary Nvidia display driver which I did through the "Hardware Drivers" program under Administration.

However I am having problems setting up my two monitors the same as I had them with my old ATI card. I have a 22" main monitor on which I want the task bar and Ubuntu menu items and then on the right of this I have a 17" monitor which I want to be able to pan across onto. So, basically, I want the desktop spread across both monitors which I assume is the Twinview option.

However, when I try to setup the two monitors using "Nvidia X Server Settings" I am having terrible trouble getting to do what I want. Firstly, if I enable the second monitor and set it to "Right Of" the main monitor, the menu's and taskbar appear on the second monitor instead of the first even if I set the first monitor as the primary display for the X screen. I tried various different settings but the results don't seem to be very predictable. I can make the same settings twice and get two different results. I fanally managed to get the displays as I wanted by setting the position of the second monitor as "Absolute" with a value of "+1680+0", but again it isn't predictable and I tried this same setting three times before it finally gave the desired results.

The other problem is that no I've got the settings correct I can't seem to save the settings. If I click on "Save To X Configuration File" I get the error message "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'. Then when I reboot the PC the display is back to it's original; state again and I have to go through the same problems again setting it up.

Am I doing something wrong or are there problems with the Nvidia control panel.

Hopefully someone can either point out where I'm going wrong or suggest what the problem could be.


Many thanks

Russell

---

