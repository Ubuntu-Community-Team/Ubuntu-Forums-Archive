---
title: "Flash video failing to go fullscreen on Ubuntu 12.04"
date: 2012-05-06
forum: Multimedia Software
---

### Post by matti777 on 2012-05-06
Hi, after upgrading to Ubuntu 12.04 flash no longer wants to go fullscreen. I have a dual monitor setup with my (old) video projector attached as a "CRT" (via VGA cable) so I thought perhaps it's the same issue as this: [http://ubuntuforums.org/showthread.php?t=1829272](http://ubuntuforums.org/showthread.php?t=1829272)

However, my "CRT" monitor is disabled (from the NVidia tool) and I have never had this problem on earlier Ubuntus, so perhaps there's something new I don't know about?

- Matti

---

### Post by yippy on 2012-05-07
I have the same issue, with a Radeon 5770 instead of Nvidia.  It flashes full screen but it immediately disappears.  I can sometimes get it to stick if I click it over and over and over, that works on Youtube but so far does not work on Vimeo.

---

### Post by richtard on 2012-05-12
Are you both using Gnome Shell? 

I use Gnome Shell and have the same problem - flash will not go full-screen, it flashes and then returns to a windowed state. 
I tried all these solutions - [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)
with no luck.

I tried disabling all Shell extensions but that didn't work

I then tried using Unity to see if it was a Gnome 3 problem - It appears that it is a Gnome Shell problem - For me at least, there is no problem with full-screen Flash in Unity.

---

### Post by matti777 on 2012-05-13
> **yippy said:**
> I have the same issue, with a Radeon 5770 instead of Nvidia.  It flashes full screen but it immediately disappears.  I can sometimes get it to stick if I click it over and over and over, that works on Youtube but so far does not work on Vimeo.

Yeah same behavior here. With very persistent machine gun style clicking it sometimes sticks to being fullscreen. :) Really annoying.

I'm running Unity.

---

### Post by poikiloid on 2012-05-20
I am finding this too, and I think it is while trying to use an external monitor. Clicking full screen will show YouTube videos that should take up the whole wide-screen monitor as only reduced-size: it shows them in the "large" viewer size, with a wide margin of black all around.
I am using Unity under 12.04, (using the nouveau driver for my NVIDIA Corporation G98M [GeForce G 105M]) with the external monitor set up to be on the "left" of the laptop monitor. the external is set to its full 1920X1080 resolution, while the laptop is set to its full 1280X800 resolution... Both are turned "On" in Display manger. 

Just playing an AVI file on full screen on the external works fine...Seems to be something about flash and external monitors...


**UPDATE**:  it looks like this is a known issue. See second post here: [http://ubuntuforums.org/showthread.php?t=1951275](http://ubuntuforums.org/showthread.php?t=1951275)

see here for more solutions/ options until flash is fixed: [http://ubuntuforums.org/showthread.php?t=1009461&page=5](http://ubuntuforums.org/showthread.php?t=1009461&page=5)

---

### Post by kapad on 2012-05-27
Got the same problem. It didn't start as soon as I upgraded though. Just a few days back.

Don't have any extra monitors. Just the standard display of the laptop. Using a ATI Mobility Radeon HD3450. So the issue is affecting nVidia and ATI. 

Any suggestions. running unity.

---

### Post by Tiede on 2012-09-07
I'm baffled why those two separate issues are treated as the same.
The bug report for chromium mentions that the "flashing" from fullscreen to normal mode is fixed (which is not true, at least here it isn't...) and that the remaining issue is with the size.
Well, if I play a flash video, even if I get it to stay fullscreen for a few seconds (after rapid gunfire clicking), it still goes back to normal. And yes, that's independent of mouse and/or keyboard events/keypresses.
This happens for me under Gnome-shell, not Unity(3D) where it behaves as expected.
```

user@terminal:~$ uname -a
Linux Obsidian 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
user@terminal:~$ chromium-browser --version
Chromium 18.0.1025.168 Ubuntu 12.04
user@terminal:~$ lspci|grep Graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
user@terminal:~$

```

---

### Post by Jimboland on 2012-09-25
I have the same problem!
I can't go to fullscreen by just clicking once, I have to rapidly click the button like 10 times and then It will switch to fullscreen.

edit:

Ubuntu 12.04
Chromium (latest)
Nvidia GT520
Unity

---

### Post by mtelesha on 2012-10-02
Same issues with Chrome and Firefox and Dual Monitors.

---

### Post by Bazon on 2012-11-25
I have the same problem with 12.10 (and Gnome-Shell), and I found a workaround:
DOUBLE-click the fullscreen icon.
(So it seems to be a focus problem.)

---

### Post by debian3 on 2013-01-19
I got the solution after lot of test, it's the "click to focus" that must be enable in unsettings.

---

### Post by denver on 2013-03-30
Click to focus.....SOB!

Thanks for the sugestion. This bug drived me nuts!

---

