---
title: "Latest flash plugin crashes in full screen mode"
date: 2010-11-05
forum: Multimedia Software
---

### Post by afilonov on 2010-11-05
After update of adobe plugin to version 10.1.102.64 (10.1.r102) plugin crashes if I try to switch to full screen. Previous plugin (10.1.53.64) worked perfectly well. Anybody with the same problem?
My system is System76 Gazelle, Ubuntu 8.04 with all latest updates, nvidia drivers.

Additional info:
1. Same effect in Google Chrome, which uses its own plugin 10.1.r103
2. Same effect (both in Firefox and Chrome) on Thinkpad T41 with ubuntu 8.04

I downgraded plugin to r53 for now, but it's not a good idea, last update fixed some security issues.

---

### Post by ami_nakata on 2010-11-05
Yes, me too. Exactly the same problem, Hardy Heron 8.04 with all updates installed, on a Gateway laptop, with Firefox. To afilonov: can you explain how to revert to the previous Flash version, until some patch or fix is made available for Hardy? I've tangled with Flash before, and would hate to screw something up, since I know what a mess/time-sink can result if that happens. Thanks! - Ami

---

### Post by Millemillimeter on 2010-11-05
Hello,

I have the same problem, most of the time flash freezes in fullscreen mode, in both firefox and chrome. Typical that the bugs of these stupid proprietary formats are primarily fixed in windows and they dont care about linux. I hope html 5 will take over all video on the net.

Anybody know if there is any solution to the problem?

---

### Post by afilonov on 2010-11-05
> **ami_nakata said:**
> Yes, me too. Exactly the same problem, Hardy Heron 8.04 with all updates installed, on a Gateway laptop, with Firefox. To afilonov: can you explain how to revert to the previous Flash version, until some patch or fix is made available for Hardy? I've tangled with Flash before, and would hate to screw something up, since I know what a mess/time-sink can result if that happens. Thanks! - Ami

I have several computers with Hardy, so I just took /usr/lib/adobe-flashplugin/libflashplayer.so from computer which wasn't updated yet to the updated one. This is actually the only file in the package, it can be replaced safely. With Chrome, you can rename /opt/google/chrome/libgcflashplayer.so to some other extension (not .so), it will take firefox plugin without complain.

---

### Post by afilonov on 2010-11-15
Today's update (10.1.102.65-1) didn't fix the problem.

---

### Post by Najand on 2010-11-18
Are you using nvidia device? 
If so, then you are experiencing a problem with the device and probably someone should file a bug report, if someone have not done it yet.
The only way I found to fix this problem temporary is by disabling "Hardware Acceleration" at setting menu of flash. (Just right click on your flash video and then select "Setting", then uncheck the only option at display tab)
I hope this works for you.

---

### Post by luigi_mb on 2010-11-18
Please note that the recent adobe flash update actually installed the previous version. Yesterday's updates include the real v10.1.102.65, which is supposed to fix the full-screen issue.

/luigi

---

### Post by afilonov on 2010-11-18
> **luigi_mb said:**
> Please note that the recent adobe flash update actually installed the previous version. Yesterday's updates include the real v10.1.102.65, which is supposed to fix the full-screen issue.

/luigi

Just tried it. Same problem again, full screen crashes plugin. Yes, I have NVIDIA drivers. But I can also try on a laptop with ATI drivers. Will publish results.

---

### Post by bregale on 2010-11-19
i have the same problem im running 8.04 with latest flash update i have tried with all other plugins disabled even tried the last version, but that will not work anymore , so i think it must be a firefox issue as when i go to the help page for the plugins it says i am running version 9 of flash  player even though its fully upto date . on this pc i have intel graphics though.

:rolleyes:

---

### Post by freeediver on 2010-11-20
Flash just quit for me. I was trying to use Google map street view and it now freezes and tells me I need the latest version 10. I have it but still street view locks up.
I'm using 8.04

---

### Post by Eromatic on 2010-11-20
[[IMG]http://img593.imageshack.us/img593/8674/fullscreencrash.th.gif[/IMG]](http://img593.imageshack.us/i/fullscreencrash.gif/)

Plugin crashes when attempting to toggle to fullscreen. Found a bug report on it I believe at: [https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/672225](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/672225)

-Ubuntu 8.04, Firefox 3.6.12, Adobe Flash 10.1.102.65, nvidia 190.53.

---

### Post by Caranud on 2010-11-22
> **Najand said:**
> Are you using nvidia device? 
If so, then you are experiencing a problem with the device and probably someone should file a bug report, if someone have not done it yet.
The only way I found to fix this problem temporary is by disabling "Hardware Acceleration" at setting menu of flash. (Just right click on your flash video and then select "Setting", then uncheck the only option at display tab)
I hope this works for you.

Disabling the hardware acceleration in the right-click menu of the video works just well for me. Try it !

---

### Post by freeediver on 2010-11-22
I got Flash to work again but when I select full screen it still crashed.
I have a 32bit sys. Toshiba Satellite 105
using 8.04
FF 3.6.12
About says:
    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


I completely removed flash.
Then I rebooted and installed flash from 
adobe. Should be the latest.
My sites work but will not allow full screen, they all crash.
I tried Flash Aid and it did not seem to work for me, some sites would work, some not, so I removed it. They all work now Except in full screen.
I forgot to add that I did check hardware acceleration to see if it was checked, it was not checked !
Hulu does have a pop out feature and it does work in a new window but not the full screen, it crashes.

---

### Post by afilonov on 2010-11-27
> **afilonov said:**
> Just tried it. Same problem again, full screen crashes plugin. Yes, I have NVIDIA drivers. But I can also try on a laptop with ATI drivers. Will publish results.

Tried this update on Thinkpad T41 with ATI graphic card and stock open source driver. Same result, full screen crashes flash.

---

### Post by afilonov on 2010-11-28
> **Eromatic said:**
> [[IMG]http://img593.imageshack.us/img593/8674/fullscreencrash.th.gif[/IMG]](http://img593.imageshack.us/i/fullscreencrash.gif/)

Plugin crashes when attempting to toggle to fullscreen. Found a bug report on it I believe at: [https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/672225](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/672225)

-Ubuntu 8.04, Firefox 3.6.12, Adobe Flash 10.1.102.65, nvidia 190.53.

Well, it looks like Adobe plugin is not going to support GTK+ 1.2 anymore. Well, it's either upgrade or stick with older plugins. Thinking about upgrading to 10.4.1

---

### Post by Eromatic on 2010-12-12
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Installed Adobe Flash Player 10.2 Beta 1, which corrects the fullscreen issue for me.

---

### Post by Dilutu on 2010-12-12
Tried that 10.2 beta on my hardy laptop and although cpu usage is 2/3 of what it was, fullscreen is not working. last flash to work good fullscreen for me is 10.0.r45.

---

### Post by hakimoerton on 2010-12-13
Solved mine after numerous attempts. Reinstalled numerous times, changed profiles, tried Chrome, looked at mozilla's suggested fix (doesn't seem possible to upgrade to 3.6.6??): [http://support.mozilla.com/en-US/kb/The%20Adobe%20Flash%20plugin%20has%20crashed](http://support.mozilla.com/en-US/kb/The%20Adobe%20Flash%20plugin%20has%20crashed) 

Tried setting the timeout to -1 in about:config as suggested by mozilla but that made no difference. Then tried the suggestion here of unchecking the hardware acceleration option on a flash video and it went full screen with no problems.

I am running Ubuntu 10.4 on an ASUS motherboard with an intel cpu.

Best wishes all - little video on a big screen = not fun!

Hakim

---

### Post by afilonov on 2010-12-14
Upgraded my T41 to Lucid, problem fixed. Full screen works with 10.1.r102 on Firefox and 10.1.r103 on Chrome.

---

### Post by HeYzN on 2011-01-10
only thing that solved this issue for me - lenovo t61, ubuntu 10.04 LTS with nvidia graphics card - was to change driver for nvidia from recommended version to 173.
issue solved on both firefox and chrome (each running their own flash plugin)

How to:
system -> administration -> hardware drivers
this opened for me a window with two options for the nvidia proprietary driver
- NVIDIA accelerated graphics driver (version 173)
- NVIDIA accelerated graphics driver (current version) [Recommended]

click activate button for 173 version. after install restart computer.

flash videos now work in full screen without problems and high quality/speed. :)
no need to disable hardware acceleration either.

---

