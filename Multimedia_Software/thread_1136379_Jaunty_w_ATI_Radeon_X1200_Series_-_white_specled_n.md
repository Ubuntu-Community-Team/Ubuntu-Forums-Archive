---
title: "Jaunty w/ ATI Radeon X1200 Series - white specled noise and poor performance"
date: 2009-04-25
forum: Multimedia Software
---

### Post by Dave.G on 2009-04-25
**Kubuntu 9.04** 32-bit version on AMD64 dual core

lspci tells me the graphics card in this thing is:
**ATI Technologies Inc RS690 [Radeon X1200 Series]**

The monitor is a brand-new SCEPTRE X20WG-NagaII Black 20.1" widescreen LCD.

I'm getting a **noisy output with occasional white speckles**. Easily see a few a second if I open up a terminal window maximized, thus giving a mostly black screen. Sometimes it boots up and it's far worse and more frequent. A few times the video even dropped out and back again a few times. (goes away with a reboot) Flash video performance is also crappy.

**I see no problems during boot or under Windows XP.** Problems start at the loading KDE splash.

xorg.conf didn't have any settings. I tried a few settings from others around here with ATI problems, and it might've helped slightly. Though, I could be imagining things as it's not consistent. Currently set:
```
Section "Device"
Identifier "Configured Video Device"
Driver "ati"
Option "AccelDFS" "on"
Option "AccelMethod" "XAA"
Option "MigrationHeuristic" "smart"
Option "EnablePageFlip" "on"
Option "EnableDepthMoves" "on"
Option "ColorTiling" "on"
Option "FBTexPercent" "0"
Option "RenderAccel" "on"
EndSection
```Was just the "Identifier" before I started trying things.

Seeing this sort of noise is really worrying. This is probably paranoia, but could something wrong causing this do anything harmful to the monitor itself?

Is there a program to set these options in a more friendly way, or is editing the file the only option?

Also, I'd like to try the proprietary drivers, but EnvyNG had a bunch of red exes on it. I think this is incompatible, and I don't want to try it if it's just going to hose things. Is this worth a try or is it incompatible?

If anyone knows what's wrong here or can at least point me in the right direction it would be greatly appreciated.

---

### Post by Dave.G on 2009-04-25
Attempted proprietary drivers. Nope, didn't work. Tried both the ones in the repository and the ones off their site.

Anyone have any ideas?

---

### Post by Dave.G on 2009-05-02
:sigh: Too many other posters here, so, *bump*.

This is still happening. Most times it boots up it's really bad with junk all over the screen, then the screen flashes a few times, it gets better, and after another occasional flash or two more it's more or less fine. It's eventually stable enough for use but if I make the screen all black I can see it's still speckling white dots occasionally. Again, zero problems during boot or under Windows XP.

To add some info I left out: The display is connected to an integrated HDMI port via an HDMI to DVI cable, as the display only has DVI and VGA ports on it.

Can someone at least think of another thread or an article somewhere that I might be able to get a lead from? I haven't been able to find anything similar anywhere.

---

### Post by EvilRick on 2009-05-02
The fix is going to have to come from ATI.  If you look at any of the bug reports, that's all you're going to see.  I have an X800 Pro and didn't do my homework.  I installed Jaunty this morning and then found out no support from ATI.  I spent about four hours . . . nada.

I just got done re-installing Intrepid.  I was going to live with Jaunty until a fix came, but there's no telling how long that will take.

---

### Post by Dave.G on 2009-05-04
I've switched to using the other white meat, the **radeonhd drivers**, and all seems well thus far. Flash performance is even worse, but it's not staticy and dropping out. Kind of insane that there are *three* different drivers to pick from here, but seeing as they all sorta suck I guess it's good to have options. I'll post back here if I learn anything new.

To anyone else that might need this info, I installed using a standard:
sudo apt-get install xserver-xorg-video-radeonhd

Then configured using these xorg.conf changes:
```
Section "Device"
        ...     
        Driver   "radeonhd"
        Option   "DRI"
        Option   "AccelMethod"  "EXA"
EndSection
Section "DRI"
        Mode         0666
EndSection
```[https://help.ubuntu.com/community/RadeonHD#Configuration](https://help.ubuntu.com/community/RadeonHD#Configuration)

---

### Post by smsmith on 2009-07-27
Do you get the static / flicker if you have desktop effects turned on?  I've got one of those Radeon 1200 cards, and using the radeon driver I would get flicker if I moved a window, opened a menu, etc with effects turned on.  With them off, I didn't get as much flicker, but it was still there.  Just using the radeonhd driver didn't seem to improve it much, but I didn't edit my xorg.conf file like you did.

Can you enable the desktop effects with the radeonhd driver?

---

