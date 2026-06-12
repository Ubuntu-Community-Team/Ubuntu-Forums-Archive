---
title: "ubuntu 12.04 multi-monitor"
date: 2012-06-28
forum: Multimedia Software
---

### Post by toffer96 on 2012-06-28
Hello everyone... I am new to this. I finally have my computer dual-booting ubuntu and win 7 nicely, after many attempts to get it right. My issue at this point is getting a multi-monitor display to work properly with a nvidia geforce 7600 gs card. Obviously, the native drivers do not work and I tried nvidia's proprietary drivers, with no success. I am running 12.04. I have googled and searched this and other forums, and either I'm not typing in the right search words, or the solution isn't out there. Please, again, I am new to ubuntu, so... talk slow :).

Thanks. Toffer.

---

### Post by toffer96 on 2012-07-09
Hello? Anyone? Please help.

---

### Post by coffeecat on 2012-07-09
> **toffer96 said:**
> Obviously, the native drivers do not work and I tried nvidia's proprietary drivers, with no success.

Obviously? Why obviously?

If by "native" driver you mean the default open source "nouveau" driver, this is perfectly capable of working with a dual-display using the configuration options built in to the 12.04 Unity GUI. That is, if your nvidia card is capable of this. I was able to set up dual-monitors with a nvidia 8400GS card with the nouveau driver just fine. 

Try this. Make sure you are using the nouveau driver and not the proprietary nvidia one. Boot up with both monitors attached and working. Click on the system settings cogwheel icon top-right and choose "Displays". Untick "mirror displays". Then highlight each monitor in turn and choose resolution and launcher placement according to your preferences. Click on apply when appropriate. If you need to reverse the order of the monitors as they appear in the upper pane, simply drag with the mouse.

And what didn't work with the proprietary nvidia driver? There was an issue with the newer version of the nvidia driver and the 7*** series of cards, but I don't know what the current status of this is. If this is what the problem was, the nvidia-173 driver, which is in the repositories, may be more suitable. You would also need the nvidia-settings package in order to configure dual-monitor support.

If you need help either with purging the proprietary driver so that you can use the nouveau driver, or with installing a more suitable version of the proprietary driver, then post back.

**EDIT**: I notice you say "multi-monitor". If you mean support for more than 2 monitors, then I don't have experience of this. I barely have desk room for two! :)

---

### Post by toffer96 on 2012-07-27
I got it to work. I don't even recall exactly what was giving me the problems, but I am posting here exactly what I did to get it working. Keep in mind, I did quite a few updates before I got it working correctly, so that may be a factor...

1. make sure your monitors are set correctly on the gray bar at the top (simply click & drag if you need to rearrange them) 

2. both monitors should be set to 'On'

3. 'Mirror Displays' should be unchecked

4. *'Resolution' should be set to:
	 Ancor Communications Inc 24": 1920 x 1080 (16:9)
	Samsung Electronics America 18": 1280 x 1024 (5:4)
    [I]*these should be set to your monitors... using mine as an example
[/I]
5. 'Rotation' should be set to 'Normal' for both monitors

6. 'Launcher placement' should be set to Ancor Communications Inc 24" *(again, using mine as an example)*

7. 'Sticky edge's should be unchecked *(matter of personal preference, but this means that your cursor will 'stick' to the edge of your monitors when moving from one to the other).*

And again, while doing the updates, I may have installed the proper drivers. I check said updates to see what they are, and don't recall seeing anything about display drivers, but it's possible I missed it, of course. I didn't manually install anything new. Hope this helps.

---

### Post by CJ_Hudson on 2012-10-03
Thanks Coffeecat, I will also try your suggestion. Was having similar difficulties to the above on this thread [http://ubuntuforums.org/showthread.php?t=2043666](http://ubuntuforums.org/showthread.php?t=2043666) ...and funnily enough I also have the  NVidia 8400 GS card.

---

### Post by CJ_Hudson on 2012-10-19
Ah that's funny- you now appear to have an Ndivia GS 6700 card. I either misread that or you edited it.

---

