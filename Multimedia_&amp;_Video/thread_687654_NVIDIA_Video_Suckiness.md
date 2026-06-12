---
title: "NVIDIA Video Suckiness"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by nullfactor on 2008-02-04
Just got my wife a new laptop that has NVidia Go 7600 graphics, built-in.

We've noticed that, regardless of appearance settings (none, normal, extra, or custom), various bizarre anomalies appear.

Some of these problems include:  missing text that magically appears when you mouse over it (this is true on web pages, as well as program menus), sudden "folding" of the screen (this is true, even when appearance is set to "none"), and intermittently blinking display.

Steps that we have taken to solve this issue include:  uninstalling/reinstalling nvidia drivers through Synaptic and installing NVidia drivers through Envy (that was a nightmare).

System specs are:

Ubuntu 7.10 (Gutsy)
Intel Dual Core 1.8GHz
2 GB RAM
120GB Hard Drive
NVidia Go 7600 video

If anybody has any information on how to tame this beast, that would be great.  We do NOT want to switch back to Windows... *shudder*

---

### Post by nullfactor on 2008-02-04
Anybody have any ideas on this?  Can't use the computer until the problem is corrected... and I've exhausted all research that I can do on my own.

Thanks much!

---

### Post by bharkins on 2008-02-04
I agree, although on my HP I don't have the problems that you seem to be having. Running Nvidia driver 169.09 causes the high rez lockup as posted above. However, on my other partition running the regular nvidia drivers without the 3D function, everything works fine except of course no 3D effects, Compiz, etc. On 2 other laptops running ATI and Intel graphics drivers, the Desktop Effects work great.

Nvidia is the culprit IMHO.

---

### Post by nullfactor on 2008-02-04
I'm going to try to get a screen shot of my wife's issue... maybe a visual will help people help me?

As for my computer, I'm using the Intel video... and it works great.  Darn nVidia and their new drivers!!!  Grrr.

---

### Post by nullfactor on 2008-02-04
Okay... here is the screen shot.  This shot should illustrate:

1)  The problem

2)  Why we're frustrated.

If ANYBODY has an idea on this, it would be appreciated.  Thanks.

---

### Post by nullfactor on 2008-02-04
Okay... apparently nobody has an answer to THAT question, so let me change the question...  

Does anybody think my wife would enjoy better video performance with KDE (rather than Gnome)?  Or would changing windows managers make no difference?

I've been looking at KDE examples and it looks to be an attractive manager.  But, I don't want to waste my time downloading the desktop if it won't make a difference.

If anybody has experience with that, any opinion would be very much appreciated!

Mucho thank you.

---

### Post by keykero on 2008-02-04
Doubt it would be any different with KDE since the X server is still the same regardless of which desktop environment/window manager you use.  Do/did you have similar issues with Windows on this machine?

---

### Post by zxscooby on 2008-02-04
I think the problem is with the anime on your desktop. 
your computer wants porn. 
:lolflag:

---

### Post by nullfactor on 2008-02-04
KEYKERO - Dang it!  That's what I was thinking, but I was hoping to be wrong.  Have you ever heard of this problem happening?  I've read a lot about the "new" nVidia drivers being extremely buggy, but have not seen a single plausible fix for it.  As for the "does it work in Windows" question... we don't know.  We ordered the laptop without an OS, so we could just throw Ubuntu on it.  We do not have a copy of Windows to test with, either.  Thanks for the reply!

ZXSCOOBY - Not unless my wife is into anime porn.  heh heh heh  Though that desktop she has is pretty nice... heh heh heh  :guitar:

---

### Post by steveneddy on 2008-02-04
OK - Here is what you need to do to get the good graphics on your nVidia controlled lappie.

First and foremost, make sure that you only have** ONE** nVidia video driver installed.

Second, unless you **NEED** the ultra high spec of the Envy driver, go with the one in the repos (Synaptic)

Get the** nvidia-glx-new** and the **nvidia-kernel-common**.

Open a terminal and copy/paste this in there:

```

sudo gedit /etc/X11/xorg.conf

```

This is the text file that sets up your video settings.

Under the Section "Device" make your look like this:

```

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce Go 7600]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	[B]Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"[/B]
	Option		"NoLogo"	"True"
EndSection

```

**Only add the bold settings**. The others are my own settings for my laptop.

Look at Section "Screen" and make sure that it is set to** Depth 24**.

The very last thing in the file should be this:

```

Section "Module"
	Load		"glx"
EndSection

```

This is just a start, but these settings should get you going. save the text file, close everything out and restart.

**IF** you have problems, use this command.

**WRITE THIS DOWN**!

```
sudo dpkg-reconfigure -phigh xserver-xorg


```

You don't have to go overboard to get good graphics with nVidia.

Try these settings and post back as soon as you can.

If you have to use the dpkg-reconfigure tool, choose the** nv** driver. This is a safe driver so you can at least start up.

Good luck.

:popcorn:

---

### Post by nullfactor on 2008-02-04
STEVENEDDY - I followed the conf file... all of those settings were already in there.  I attempted to do the if-all-else-fails... now, the screen is blinking still intermittently, but more often than before.  Any ideas?  Thanks for the idea.

---

### Post by steveneddy on 2008-02-04
Blinking? Like when you look at the desktop, the screen has a flash, like it loses video for a split second?

What video driver are you using?

Please post your xorg.conf file.

---

### Post by nullfactor on 2008-02-04
Yes... the split second dark screen is a perfect description for what I'm seeing.  Interestingly, I just played a game that would, without fail, cause the desktop to look like the screen shot I posted.  It played without distorting the screen.  The video kept seizing up for a few seconds at a time, but no distorted video.

See attachment for xorg.conf...

---

### Post by grampamoses on 2008-02-04
This sounds like your issue.  

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Scroll down to common problems.  

""""Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not recieving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a [WWW] known bug, and can be resolved by editing your /etc/X11/xorg.conf file:

    *Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
    *Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
    *Find the line that says Section "Screen"
    *Insert a new line that says Option "UseDisplayDevice" "DFP".
    *Save the file. If you had to restart into revocery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.""""""

Also, I love Shakugan No Shana.  :-D

---

### Post by steveneddy on 2008-02-04
> **nullfactor said:**
> Yes... the split second dark screen is a perfect description for what I'm seeing.  Interestingly, I just played a game that would, without fail, cause the desktop to look like the screen shot I posted.  It played without distorting the screen.  The video kept seizing up for a few seconds at a time, but no distorted video.

See attachment for xorg.conf...

Here is your new xorg.conf - try this to see if you have any better luck.


```

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce Go 7600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce Go 7600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

You just need to change some things in the bottom half of your xorg.conf.

Open the file again

```
sudi gedit /etc/X11/xorg.conf
```

and copy/paste this there and try this out.

---

### Post by nullfactor on 2008-02-04
GRAMPAMOSES - I did the xorg.conf modification... played the game that would ALWAYS end up distorting the screen... no distortion (that's great).  However, the video keeps locking up for brief moments.  Sometimes, those brief moments aren't really that brief... but no distorted video.  Any idea on the locking up video?

As for Shakugan No Shana, heh heh heh... my wife wanted a background that was kind of sexy, so she did a Google search.  That was one of the results.  She was hooked... :)

---

### Post by nullfactor on 2008-02-04
STEVENEDDY -  I tried your new xorg... started getting glitching, again (I'm not convinced that it was right, before..).  Before glitching and distortion happened, I noticed LONG pauses in any animation.  During those pauses, I couldn't click anything (couldn't close windows, open menus, etc).  After the distortion, the screen started blanking out, again... that flickering I described, earlier.

Friggin' nvidia...

---

### Post by steveneddy on 2008-02-05
That's odd. There are a few other addititions to the xorg.conf.

Which video driver did you say you had?

Did you install it from the repos or from Envy?

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - Actually, I tried both - repository and Envy.  Before doing Envy, though, I made sure to remove the drivers that were previously installed.  Neither method seemed to work, well.

---

### Post by steveneddy on 2008-02-05
If you are on Feisty, you may try upgrading to Gutsy as it has the Restricted Driver Manager that could help.

I have used the same config file for a couple of years and nVidia works well for me.

My wireless and nVidia both work very well for me.

But I don't game. I do watch a lot of movies and video online with this machine.

Here are some other options that you might try one at a time to see if it changes your performance:

remember to restart x after you make a change (ctrl+alt+backspace)

Option "AllowGLXWithComposite" "boolean"

boolean means either true or false. Enter true.

Option "AddARGBGLXVisuals" "boolean"

and look [here]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html") for other TV out options.

---

### Post by frodon on 2008-02-05
BTW, are you running compiz ?

Compiz is rather new and the ubuntu version has still known unfixed graphic bugs especially with Nvidia cards.

---

### Post by steveneddy on 2008-02-05
Didn't think about that, but turn off compiz before gaming.

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - Really, the only gaming my wife does is some really convincing remake of Super Mario Brothers... it's a game written in Java.  This is the game that breaks it, every time.

Interestingly, sometimes she experiences missing text when looking at pages such as Google.  The text is viewable if you highlight everything on the page... after you deselect what was just highlighted, the text is viewable.  This is also true with panel menus.  These pop-up menus often are missing text until you mouse over them.  After the mouse-over, all text is visible.

Really, really a strange problem.

---

### Post by nullfactor on 2008-02-05
FRODON - Something worth trying!  How do I go about that (turning off Compiz)?

---

### Post by frodon on 2008-02-05
To disable it :
System &#8594; Preferences &#8594; Appearance &#8594; Desktop Effects then select "No effects" to disable desktop effects.

---

### Post by steveneddy on 2008-02-05
> **nullfactor said:**
> FRODON - Something worth trying!  How do I go about that (turning off Compiz)?

metacity --replace

I think...

---

### Post by steveneddy on 2008-02-05
> **frodon said:**
> To disable it :
System &#8594; Preferences &#8594; Appearance &#8594; Desktop Effects then select "No effects" to disable desktop effects.

Nevermind....

---

### Post by nullfactor on 2008-02-05
FRODON/STEVENEDDY - Okay... I already tried setting effects to "none".  The problem STILL exists, believe it, or not.  That was the first thing I tried.  

This is one stubborn little problem.  Any other idears?  Thanks!

---

### Post by frodon on 2008-02-05
The only time i saw something like that (without compiz) was on a medion laptop due to a global bad cooling issue which created graphic bugs under ubuntu as well as under linux.
You can check the graphic card temp in nvidia-settings window, should be somewhere in the menu or you can type directly "nvidia-settings" in terminal, don't know for the CPU temp.

This may be a cooling problem, could you try to reproduce this with another OS ?

---

### Post by nullfactor on 2008-02-05
FRODON - The "slowdown threshold" is 110C... we're currently operating at a core temp of between 45-55C.  

As for another OS we could test with... I have several versions of Linux I could throw on there (Knoppix, SuSE, Ubuntu (Feisty and Gutsy)... I may have an unused Windows XP, but that is an OEM disc that may or may not work on this computer.

Do you see any point in trying to put another flavor of Linux on there (just to test it out)?  The going theory is, whatever version of Linux you throw on there, you're still using the same Xserver, so it wouldn't make a difference.  What's your take on that?

---

### Post by steveneddy on 2008-02-05
You know. On the first post, you said it was a new laptop.

The system specs you give tell me that the software should work correctly if set up correctly.

Maybe you could post the model number of the laptop in question.

This may reveal some other issues that would bring us to the end of this quest.

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - Good point.  It's an NSpire EL80.

---

### Post by steveneddy on 2008-02-05
> **nullfactor said:**
> STEVENEDDY - Good point.  It's an NSpire EL80.

I swear that this lappie looks like my System76 Serval Performance that I bought last year.

Even the specs are the same.

I don't know why you are having issues.

I use the nVidia driver from Synaptic (the repos) and have zero issues.

My video looks great!

The xorg.conf file works with my machine and should work on yours, if you are using the same video driver.

Funny thing, you might try the [System76 driver]("http://knowledge76.com/index.php/System76_Driver#Download") to see if that solves any issues.

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - It very well could be a similar system... the Nspire EL80 is a "whitebook", so it is entirely possible...

I'll give that system76 driver a go!

---

### Post by steveneddy on 2008-02-05
Pic here.

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - Tried the system76 drivers... still no good.  Exact same symptoms.

---

### Post by steveneddy on 2008-02-05
> **nullfactor said:**
> STEVENEDDY - Tried the system76 drivers... still no good.  Exact same symptoms.

Well - on a slightly different note, does your camera work?

---

### Post by nullfactor on 2008-02-05
STEVENEDDY -Just saw your pic... sorry for not seeing it earlier.  The good news is, YES... that IS the system.  Exactly.

I'm not even sure how to use the camera on this system.  Any pointers?  I'll let you know if it works after the pointers. :)

As an update... I'm looking at F-spot's import source.  My options are:  SELECT FOLDER and NO CAMERAS DETECTED.  That would tell me that, no... camera is not working.

---

### Post by steveneddy on 2008-02-05
> **nullfactor said:**
> STEVENEDDY -Just saw your pic... sorry for not seeing it earlier.  The good news is, YES... that IS the system.  Exactly.

I'm not even sure how to use the camera on this system.  Any pointers?  I'll let you know if it works after the pointers. :)

As an update... I'm looking at F-spot's import source.  My options are:  SELECT FOLDER and NO CAMERAS DETECTED.  That would tell me that, no... camera is not working.

Yeah - mine either.

How's your video coming?

Have you tried changing the refresh rate?

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - The video is still completely forked.  I've devised a bit of an action plan, though.  Since this computer is, without question, the same one you have... I'm using the system76 driver manager to "restore system back to factory settings", then run some upgrades to see if this solves any problem.  If not, I'm going to do a complete system reload.  Just in case I botched something in the installation.  If that does not work... I dunno what I'll do... heh heh heh

UPDATE - PLAN A was a spectacular failure... video distorted immediately.  On to a total system reload...

---

### Post by steveneddy on 2008-02-05
> **nullfactor said:**
> STEVENEDDY - The video is still completely forked.  I've devised a bit of an action plan, though.  Since this computer is, without question, the same one you have... I'm using the system76 driver manager to "restore system back to factory settings", then run some upgrades to see if this solves any problem.  If not, I'm going to do a complete system reload.  Just in case I botched something in the installation.  If that does not work... I dunno what I'll do... heh heh heh

UPDATE - PLAN A was a spectacular failure... video distorted immediately.  On to a total system reload...

I really don't think you need a complete system reload, but I have done this, too, to solve issues.

My belief is that you delete the newest nVidia driver that you got from Envy and install the one from the repos.

Then tweak the xorg.conf file from there.

If you do a complete reload, use the Restricted Drivers Manager to get the nVidia driver.

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - I've done a complete system reload... same problem.  So, I found an OEM (unlicensed to that computer) version of Windows XP... video works great.  This tells me that it is not a hardware issue, but a problem with something Ubuntu (or, more likely driver) related.

I'm going to reload Ubuntu back on the system and use your recommendation of using the restricted drivers, then editing the xorg.conf file from there.  

My wife better appreciate me for this!!! heh heh heh

UPDATE - Reinstalled Ubuntu... used restricted drivers... set up xorg.conf as described... problem STILL exists.  I don't know if this has ANYTHING to do with it, but it seems to really bomb on Java-based games.  Is there a known issue with Java interacting with nVidia video?  Or ANYTHING along those lines?

---

### Post by nullfactor on 2008-02-05
Looked at the "Post The Way You Got Nvidia To Work For You" sticky... the only page I found on the Go 7600 said "no additional tweaking needed".  What are the odds that I DO have a hardware issue?  I'm not sure WHAT to think, anymore...

---

### Post by gsmanners on 2008-02-05
> **nullfactor said:**
> STEVENEDDY - I've done a complete system reload... same problem.  So, I found an OEM (unlicensed to that computer) version of Windows XP... video works great.  This tells me that it is not a hardware issue, but a problem with something Ubuntu (or, more likely driver) related.

Did you install the nVidia driver in XP? Or were you just using the default video?

---

### Post by nullfactor on 2008-02-05
Never mind... even with Java uninstalled, it's f'ing up.

---

### Post by nullfactor on 2008-02-05
Interesting new development... I just loaded a live CD running KDE on the computer and tried my best to break it.  I couldn't!  It seems to run perfectly under KDE.  That blows away my theory.  Tonight, I'm downloading the kubuntu-desktop package and seeing if this fixes the issue.  Stay tuned...

---

### Post by steveneddy on 2008-02-05
> **nullfactor said:**
> Interesting new development... I just loaded a live CD running KDE on the computer and tried my best to break it.  I couldn't!  It seems to run perfectly under KDE.  That blows away my theory.  Tonight, I'm downloading the kubuntu-desktop package and seeing if this fixes the issue.  Stay tuned...

Cool!

You know - that is a dual core laptop - you could run the 64 bit version and get better performance.

---

### Post by nullfactor on 2008-02-05
STEVENEDDY - Did someone say, "better performance"?  You're speaking my language!  :guitar:

---

### Post by steveneddy on 2008-02-05
64 bit is the way to go. All the cool kids are doing it.

Look at the[ 64 bit forums]("http://ubuntuforums.org/forumdisplay.php?f=134").

---

