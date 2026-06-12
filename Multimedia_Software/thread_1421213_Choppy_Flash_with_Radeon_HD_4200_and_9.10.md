---
title: "Choppy Flash with Radeon HD 4200 and 9.10"
date: 2010-03-03
forum: Multimedia Software
---

### Post by eric8s on 2010-03-03
I'm running an athlon II X2 on a Gigabyte GA-MA785GM-US2H motherboard Graphics are running on the Radeon HD 4200 on the motherboard. System has 2 GB of RAM.

I recently did a clean install of Ubuntu 9.10. I previously had 9.04 installed and flash video ran completely smoothly, and the CPUs wouldn't even come out of 800 MHz power save mode.

Since upgrading to 9.10, flash runs choppy and the CPUs max out every time there is a lot of movement on full screen videos. On 9.04 and 9.10 I was running the ATI proprietary FGLRX hardware drivers.

I've tried re-installing the ATI drivers and flash. I've also disabled compiz desktop effects.

Thanks in advance

---

### Post by rexh on 2010-03-07
I have the same the issue with the same mobo.

---

### Post by no2498 on 2010-03-08
try this you can set it back if it dont work and i think you need to restart the computer to see it work rite down wat its set to now
open a terminal type ( gstreamer-properties ) click enter
set the plugin to /     x window system (no xv)

---

### Post by rexh on 2010-03-08
> **no2498 said:**
> try this you can set it back if it dont work and i think you need to restart the computer to see it work rite down wat its set to now
open a terminal type ( gstreamer-properties ) click enter
set the plugin to / x window system (no xv)
 
 
That made it better, but not perfect.

---

### Post by hxcobd on 2010-03-09
Unfortunately, terrible Flash performance on recent linux distros is a well-documented and well-known problem.

I've used 9.10 on 3 different computers now, 2 laptops and 1 desktop, and they all produced terrible Flash performance on certain websites.

HD-quality video using Flash players, for example, always performed horribly.

I've yet to find a solid solution, and I've heard from others that there simply isn't one.

---

### Post by dustin.jorge on 2010-04-23
I have (2) 1gb radeon 4870s on a crossfire setup and had the exact same problem.

My solution turned out to be installing the Flash Player 10.1 Release Candidate 2 from Adobe Labs:

Labs Page:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

File Link:
[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc2_linux_041910.tar.gz)

Download, extract, and move the included libflashplayer.so to /usr/lib/adobe-flashplugin, replacing the old one. You'll need super user permisions:

```
$ gksudo nautilus
```

---

### Post by kronictokr on 2010-04-29
this is what works for me

[http://ubuntuforums.org/showthread.php?t=1464748](http://ubuntuforums.org/showthread.php?t=1464748)

same card

---

### Post by bullpuckey on 2010-08-12
First of all i should probably say I'm running 10.04 but I had identical issues. I had these same issues with a mobo integrated with an ATI Radeon  4200 HD graphics card. I tried all of the above solution along with several others found elsewhere, None of them worked. After struggling with this for a few days I finally found a solution that was actually quite a bit simpler than some of the others I  had tried. The answer was here:

 [http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-1004.html](http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-1004.html)

Basically just:

1. Open firefox.
2. Go to a flash video and right click it.
3. Under settings Uncheck hardware acceleration.
4. Open a terminal.
5. Type "sudo mkdir /etc/adobe" without the quotes and hit enter.
6. Enter your password and hit enter.
7. Type "sudo su" without quotes and hit enter.
8. Type "sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg" without quotes and hit enter.
9. Close your terminal, go back to firefox, right click a flash video and enable hardware acceleration under   settings.
10. Restart firefox.

That's it. It worked perfectly for me and several videos and restarts later I still have no issues with flash in fullscreen.

---

