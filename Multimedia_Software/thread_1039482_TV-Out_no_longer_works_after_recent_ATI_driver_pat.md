---
title: "TV-Out no longer works after recent ATI driver patch update"
date: 2009-01-14
forum: Multimedia Software
---

### Post by Smjork on 2009-01-14
OS: Ubuntu 8.10 (upgraded from 8.01)
Video: Sapphire ATI Radeon HD 2900 Pro (which is incorrectly seen by the OS as HD 2900 XT)
Display:
1. Samsung SyncMaster 215TW
2. TV (via S-Video, max. supported resolution 1024x768)
Drivers: the proprietary ATI drivers 8.53, including Catalyst Control Center

The story:
I worked like a slave to find out how to make TV-Out work on Linux. Something that simply worked out of the box on Windows. And I am not a Windows fan, trust me.
It took A LOT of time to read dozens of web pages, all scattered through all the internet, BECAUSE THERE IS NO FREAKING COMPREHENSIVE TUTORIAL ON HOW TO USE TV-OUT OR DUAL MONITORS with Linux nowhere. Many forums, many "try this", "try that", etc.

Anyway I managed to make it work.
And today my system announced me I have 52 updates available.
I scrolled through these updates, checked them all.
I noticed two of them were related to some ATI radeon issues and I thought I will get better drivers with these patches.
All the update went well. At the end it required a system restart.

Well... after restarting my TV-Out went absolutely nuts.
I had the TV switched on so I could see. It looked like the x-server is hardly trying to enable the TV, some images and modes changed on the TV screen (and the LCD also) and finally the Tv went black and the LCD turned to safe mode displaying an error message box saying:

(EE) fglrx(0): Unknown EDID version 0
(EE) fglrx(1): [FB] Can not get FB MC address range
(EE) fglrx(0): ===[swlDalHelperSetDisplayConfig]
               === CWDDC DisplaySetConfig failed: 6

The options were to review the configuration, to create a whole new configuration, to run in safe mode, etc.
No matter what I choose the whole X turns black.
I can not even open a console in another terminal.
The only way to solve this is to reset the computer, run in recovery mode, execute an aticonfig --initial to create a basic xorg.conf and restart the system.

This is not a cry for help. I'm pretty sure that nobody on this forum will be able to give a solution to the problem (other than reinstall all from scratch or something similar)
This is just a warning for all of you using TV-Out with or without ATI cards.

---

### Post by hrvoje-sl on 2009-01-19
I have the same problem with ATI RADEON 9200SE. Because I'm really new to linux I could not fix the thing after it went in low graphics mode and had to reinstall Ubuntu 8.10. So it is still not working and I'm afraid even to try to fix it because the graphics will crash again if i start to make changes through terminal. If someone has tv-out working with radeon 9200 it would be good to let us know exactly how he managed that.

---

### Post by bmitov on 2009-02-19
So... how DO you connect tv-out? On windows its plug and play...! But what do I have to do to get tv-out to work? I've ATI graphics card and the TV seems to not recognize that a computer is plugged in at all!

Are there any programs I should install? Please help:D

---

### Post by jwagener on 2009-02-19
had a similiar problem. after updating & restarting the system my xserver would not start at all. got the error msg: [FB] Can not get FB MC address range .. Unknown EDID version 0 . after reinstalling the ati catalyst driver the xserver worked again, but without composite (once again).

i'm getting really frustrated about it.

---

### Post by iheartubuntu on 2009-02-22
Windows XP is not very plug and play to me. Ony my wifes laptop, dual boot Ubuntu and XP with a ATI X300 video card, I cannot run any video out in XP. In the ATI catalyst there, there is no option for video out, or a second monitor or tv option. Ive got it all hooked up to the TV right now and absolutely no luck in XP. Here I am, back in Ubuntu and I cannot figure it out here either. It should be so simple too you would think.

---

