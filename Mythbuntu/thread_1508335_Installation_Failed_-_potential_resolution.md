---
title: "Installation Failed - potential resolution"
date: 2010-06-12
forum: Mythbuntu
---

### Post by Barry_IA on 2010-06-12
Completed the process of re-installing Mythbuntu 10.04 a little while ago. Found a few things that may be helpful: 

If an error message pops up: 

Installation Failed 
The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.

According to a quick Google search this problem seems to be due to an incompatible/not fully tested video card. (Yes, I and about 40,000 other people said "are you serious??!!) 

Potential resolution: 
At the splash screen (the one with the keyboard and stick figure icon at the bottom) hit any key. (Now that symbol makes sense!!) F6, select 'nomodeset', then the <escape> key. Wait 30 seconds or so to get back to the menu and continue. 

Should create and get to the desktop. Here the image was too big for the screen. Right_click on the desktop, Applications > Settings > Display. My resolution was set at 1152 x 864, which I found out elsewhere was a 4:3 resolution. This is a widescreen LCD display. Selected 1360 x 768 (16:9) and the display now fit. (Wondering if the installer isn’t detecting the display properly??) 


Also found the jks method of formatting apparently is not supported/not supported properly in Mythbuntu/Ubuntu.  My system previously had Mythbuntu 9.10 installed; the 1 TB hard drive was formatted with jks; had managed to get the installer to run but on reboot the system couldn't load the /var correctly.  The Ubuntu Live CD indicated jks was the problem, formatted it to xfs and resolved that problem.

Hope these suggestions help someone else!

---

