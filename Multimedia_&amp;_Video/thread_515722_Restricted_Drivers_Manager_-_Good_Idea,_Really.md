---
title: "Restricted Drivers Manager - Good Idea, Really?"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by porcorosso on 2007-08-02
I'm running Ubuntu 7.04 on a Dell M70 notebook with an nVidia Quadro FX Go1400 video subsystem on it.

I performed a previous installation a couple of weeks ago that I got hosed in the following manner:

1. Installation / updating / configuration of OS and a number of add-on applications went without any real hitches. Only minor issues appeared which were easily solved with a little research. I was impressed.

2. I tried selecting a couple of different screensavers and wound up with a locked system. I dope-slapped myself when I realized that these screensavers were trying to take advantage of advanced display features not available in the VESA driver.

3. I used the Restricted Drivers Manager to install the nVidia driver, and suddenly everything was really working nicely -- screensavers included.

4. I took the thing home and plugged it into my port replicator. Hmm. Nothing happening on the external DVI monitor. I opened the notebook and saw that the primary display was being used. I couldn't use the standard function key combination to switch the display to the external one. This perturbed me a bit because the VESA driver had no problem at all with me switching back and forth between the docked configuration with external display and the regular configuration with the primary display being detected automatically.

5. I realized that I needed some kind of control for the new driver. I found references that indicated that the nvidia-settings software should have been installed when I configured the driver, but it wasn't installed on the system.

6. I installed nvidia-settings manually with the system undocked. I saw, naturally enough, only the option for the primary display. I took the system home, docked it, and xserver wouldn't start. (I got the text mode red/white/blue screen.)

Okay. I realized that I could open a terminal and, after doing a little research, figure out how to correct this situation. But I had spent precious little time configuring the system in the first place and decided to start over with a clean installation.

This is a real annoyance. It appears that making the choice to install the binary from nVidia is a good way to throw a monkey wrench into the system. The easy-to-use Restricted Drivers Manager is a nice first step toward dealing with a problem that I wish we didn't have to deal with at all. But it appears to have set me up for an exasperating problem because of my particular system configuration.

If the hardware manufacturers like ATi and nVidia aren't ever going to allow us to have decent Open Source drivers for our video subsystems we have to choose between a kludgy workaround that might bite us in the tail or doing without 3D features that we paid for in the hardware.

Integrated graphics from Intel are beginning to look better to me. I'm experimenting with Linux because closed source software (and particularly closed data file formats) have always made my skin crawl. But choosing between decent hardware functionality and having a working xserver has put a bit of a bad taste in my mouth about this.

i've been using everything from mainframes to minis to CP/M to DOS to Windows to AIX over a span of about forty years, but this is the first step into Linux. I'm impressed as hell with this distribution, but this one glitch is a real annoyance.

I know that the folks at Ubuntu (and the Open Source community in general) can't do a lot to make the hardware manufacturers behave intelligently, but this issue is still a problem for the community. And I think that the people who design these distributions should at least configure them so that the OpenGL screensavers are disabled by default -- or until an appropriate driver is installed. And maybe making sure people with multiple displays / docking station configurations don't get trapped would be nice, too.

I'm going to try installing the "evil" driver again to see if I can get it to work properly with this configuration. I can guess that I should do that while the system is docked, and with the lid up on the notebook, so that the system detects and can use both displays for the initial setup.

Can anyone think of anything else I might do to improve the likelihood of getting this to work right on a first try?

---

### Post by tseliot on 2007-08-02
> **porcorosso said:**
> 4. I took the thing home and plugged it into my port replicator. Hmm. Nothing happening on the external DVI monitor. I opened the notebook and saw that the primary display was being used. I couldn't use the standard function key combination to switch the display to the external one.
Did you try plugging in the external monitor before turning on the laptop?

---

### Post by porcorosso on 2007-08-02
I'm not absolutely sure I'm understanding what you're asking, but -- yes, the external monitor was, by necessity, plugged in before the system was powered up. The system was plugged into the port replicator, and then it was powered on.

This time around, I am not having a failure of xserver to start. However, I got the system up and running with only the primary monitor (the one built in to the notebook) showing anything. I tried using the nvidia-settings applet to set up the external monitor (a Dell flat panel) as the primary monitor. It worked. Sort of. Now Ubuntu in the docked mode starts up just fine with the desktop on that external monitor. However, if I start a terminal window on that system the terminal is a blank white square. No window borders or menu. No ability to type anything within the terminal.

Bizarre. I can't revert to earlier settings in the docked mode because I can't crank up the nvidia-settings applet.

Edited:

Okay. So I undock and reboot the system into Ubunt. I get a plain brown background with a white cursor -- and absolutely nothing else. No access to anything.

So the system can only be booted into Windows Vista, which works just fine -- docked or undocked. But Ubuntu is hosed -- again.

---

### Post by tseliot on 2007-08-02
Unplug the external monitor then turn on your computer and boot Ubuntu in Recovery mode.

then type:
```
dpkg-reconfigure xserver-xorg
```
and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot
```

and boot Ubuntu as usual

---

### Post by porcorosso on 2007-08-02
Hi. Thanks for your efforts.

Well, I tried your suggestion. I'm back to where I was when I blew away Ubuntu and started over before -- at a blue background with white text that tell me that xserver failed to start.

I'm beginning to think that this system isn't going to work with the restricted driver.

I have to knock off for tonight. Getting up for work in about 4 hours. But I'll return here tomorrow morning to see if anyone can shed some light on this.

I'll hold off on blowing it away this time to see if someone can teach me something here. But, obviously, using the VESA driver is an option. It's just kind of annoying to make either choice, really.

But, again, I thank you for any light you can try to shed on this. I'm brand new to this OS. I know that learning the arcana of the OS is just a matter of time for me. I'm just trying to muddle through this first time in beginner mode in an effort to see how friendly the OS really is.

My impression so far is very good -- as long as I avoid the restricted drivers for the video subsystem!

Edit: I should mention that, though this is my primary machine, the Ubuntu installation is merely a second boot option for me (via Wubi). The primary OS is Vista, and that is operating just fine. There's no urgency to this. But I greatly appreciate the opportunity to learn something about Ubuntu / Linux that doesn't seem to be covered directly in any of the FAQs / Wikis / other documentation that I've run across so far. I realize that the problem may be Dell's particular implementation of the Go 1400 in their design.

---

### Post by porcorosso on 2007-08-03
I have had some time to work at this some more today. It's not looking good.

XSERVER won't start. So I take a look at the log and see:

```
(WW) NV(0): Bad V_BIOS checksum
```

and

```
using framebuffer
```

The use of the framebuffer doesn't make sense, I think, and the log seems to indicate I'm right because they indicate "no such file or directory" for /dev/fb0 through /dev/fb7.

Fine. I do

```
sudo dpkg-reconfigure xserver-xorg
```

and turn off the framebuffer. (Not sure if I fat-fingered that choice whilst running the configuration last night or not. Now it boots to a GUI logon screen, but logging on nets me an all-white screen with a cursor being the only desktop feature present. The cursor moves, but it doesn't have a job to do. Right-click on this "desktop" doesn't bring up a context menu or anything.

Restarting X brings me back to a graphical logon screen. Failsafe Gnome doesn't work any better than the regular session. Lets me log in but then nothing but white.

I have reconfigured as well as I know how using the text mode utility, but it's not resulting in a useable desktop for me. I even finally tried reverting to the VESA driver from the utility, but I can tell the system is still using the proprietary driver. (It looks pretty different right after the logon prompt but before it gets to the desktop.

Am I right in thinking that the "Bad V_BIOS checksum" message is bad? Can anyone tell me what the ramifications of that might be?

I have to say that the VESA driver worked flawlessly within its limits -- including giving me the ability to use my external monitor when docked and my built-in monitor when undocked, with nary a need for any input from me on the matter.

Installing the restricted driver using RDM works really well -- until I try to change the docking status of the system. Throwing a second monitor into the mix really screws up the system, with it trying desperately to use only the built-in monitor from that point on. If I use the nvidia-settings applet I can sort of get both of the monitors working, though only with them both acting as part of a single desktop. But the very first reboot or restart of X after that it all goes to the bad place.

If anyone has a suggestion for me I would appreciate advice. If I don't get a response fairly soon I'm just going to blow it away again. And this time I'll keep my promise to myself about just sticking with the VESA driver.

---

### Post by tseliot on 2007-08-03
maybe try removing the Nvidia driver:
```
sudo apt-get --purge remove nvidia-glx nvidia-glx-new
```

reinstall Mesa:
```
sudo apt-get install --reinstall libgl1-mesa-glx libglu1-mesa  libgl1-mesa-dri
```

then set the driver to "vesa" in the Section Device of your /etc/X11/xorg.conf

Finally restart the Xserver.

---

### Post by porcorosso on 2007-08-03
Thank you. I had got the first and third instructions right from reading your posts in other threads. The second instruction is kind of useful, too.

:)

I am sticking with VESA for now. Thank you for your help.

Do you have any idea why this driver set was failing on my system? Was that invalid checksum error indicative of anything in particular? I assume that the problem had more to do with the routine that was doing the checking than it had to do with the Video BIOS itself, since the video subsystem has performed very well with every other OS I've had installed on the notebook.

Thank you again for your help.

---

### Post by tseliot on 2007-08-03
> **porcorosso said:**
> Do you have any idea why this driver set was failing on my system? Was that invalid checksum error indicative of anything in particular? I assume that the problem had more to do with the routine that was doing the checking than it had to do with the Video BIOS itself, since the video subsystem has performed very well with every other OS I've had installed on the notebook.
I think it was the "nv" (Nvidia's open source driver) that threw this error:
```
(WW) NV(0): Bad V_BIOS checksum
```

While I don't think the Bios has anything to do with the problem, I don't know what the cause might be (since I don't write drivers).

---

### Post by porcorosso on 2007-08-03
Thanks once again for helping me. I'm enjoying Ubuntu, but I'm going to sulk a little each day until I can install a driver that supports OpenGL -- without hosing the system!

Have a good day!

---

