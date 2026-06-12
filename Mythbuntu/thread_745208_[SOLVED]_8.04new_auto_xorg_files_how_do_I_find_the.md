---
title: "[SOLVED] 8.04:new auto xorg files: how do I find the actual settings?"
date: 2008-04-04
forum: Mythbuntu
---

### Post by arjay1 on 2008-04-04
In the "old-style" xorg.config files all the actual settings for various hardware were set out nicely in each section.  That made it easy (say) to change the modes, or the video driver and so on.

Now, in the new-style autoconfigured xorg.conf files there is no detail at all.  For each section it just says  "mouse configured", "screen configured" etc etc.  No detail at all.

Now I am in a situation where i want to check the exact settings for the mouse, so that I can possibly make some changes, (I am progressively getting to the stage where i can get an MS mce keyboard to work - but the the mouse won't play nice.

I have looked up a few things in Xorg.0.log etc but I can't get the level of detail I need for all the hardware that I used to be able to get  in xorg.conf.

Can someone tell me to if it is possible to get the old-style xorg files back or where else I might find the info that used to be there.

I am running mythbuntu 8.04 beta BTW

Thanks in Advance

---

### Post by majoridiot on 2008-04-04
> **arjay1 said:**
> In the "old-style" xorg.config files all the actual settings for various hardware were set out nicely in each section.  That made it easy (say) to change the modes, or the video driver and so on.

Now, in the new-style autoconfigured xorg.conf files there is no detail at all.  For each section it just says  "mouse configured", "screen configured" etc etc.  No detail at all.

Now I am in a situation where i want to check the exact settings for the mouse, so that I can possibly make some changes, (I am progressively getting to the stage where i can get an MS mce keyboard to work - but the the mouse won't play nice.

I have looked up a few things in Xorg.0.log etc but I can't get the level of detail I need for all the hardware that I used to be able to get  in xorg.conf.

Can someone tell me to if it is possible to get the old-style xorg files back or where else I might find the info that used to be there.

I am running mythbuntu 8.04 beta BTW

Thanks in Advance

the config file is still located at /etc/X11/xorg.conf -- at least on my 8.04 beta box.

for edits to be applied, you need to edit this file as sudo:

```
$ sudo nano etc/X11/xorg.conf
```

or

```
$ sudo gedit etc/X11/xorg.conf
```

or with your editor of choice, etc.

---

### Post by arjay1 on 2008-04-04
Sorry - probably didn't make myself clear.  I know where the file is and have edited it many times over the years.  However, I am used to seeing sections like this:

Section "InputDevice"
    Identifier     "Serial Mouse"
    Driver         "mouse"
    Option         "Protocol" "Microsoft"
    Option         "Device" "/dev/ttyS0"
    Option         "Emulate3Buttons" "false"
    Option         "Emulate3Timeout" "70"
EndSection

But all my auto-generated file now says is (something like this - can't be exact because I am not at the mythbuntu machine):

Section "InputDevice"
    Identifier     "Serial Mouse"
    Driver         "vmmouse"
   Mouse configured
EndSection

Same with the other sections too.  I'll try and attach my actual xorg.conf file tomorrow.  What I wanted to know its where is this info kept.  The xorg.conf file may just say that the keyboard, mouse, screen, etc are "configured" but it must keep the actual info somewhere about WHAT the configuration is.

This looks more and more like the cr*p that  I used to get from Microsoft Windows.  First you had to guess what the system file was, then you had to find a way to open it, and then you found there was no useful info in it anyway.

I can understand the advantages to the user of having auto-config, but for the life of me I cannot see the advantage of then not being able to discover what the configuration actually is?  Or am I missing something?

---

### Post by majoridiot on 2008-04-04
> **arjay1 said:**
> Sorry - probably didn't make myself clear.  I know where the file is and have edited it many times over the years.  However, I am used to seeing sections like this:

Section "InputDevice"
    Identifier     "Serial Mouse"
    Driver         "mouse"
    Option         "Protocol" "Microsoft"
    Option         "Device" "/dev/ttyS0"
    Option         "Emulate3Buttons" "false"
    Option         "Emulate3Timeout" "70"
EndSection

But all my auto-generated file now says is (something like this - can't be exact because I am not at the mythbuntu machine):

Section "InputDevice"
    Identifier     "Serial Mouse"
    Driver         "vmmouse"
   Mouse configured
EndSection

Same with the other sections too.  I'll try and attach my actual xorg.conf file tomorrow.  What I wanted to know its where is this info kept.  The xorg.conf file may just say that the keyboard, mouse, screen, etc are "configured" but it must keep the actual info somewhere about WHAT the configuration is.

This looks more and more like the cr*p that  I used to get from Microsoft Windows.  First you had to guess what the system file was, then you had to find a way to open it, and then you found there was no useful info in it anyway.

I can understand the advantages to the user of having auto-config, but for the life of me I cannot see the advantage of then not being able to discover what the configuration actually is?  Or am I missing something?

strange... i haven't seen settings like those.  the xorg.conf generated on my 8.04 install looks just like any other...
except for goofy custom modelines that didn't work right... ;)

have you tried pasting the info from an older-known working xorg.conf into the new one- or just configuring it
by hand?

---

### Post by arjay1 on 2008-04-05
> **majoridiot said:**
> strange... i haven't seen settings like those.  the xorg.conf generated on my 8.04 install looks just like any other...
except for goofy custom modelines that didn't work right... ;)

have you tried pasting the info from an older-known working xorg.conf into the new one- or just configuring it
by hand?

I haven't seen a file like it either!  Here it is:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

As you can see no real info at all.

I did try one old file but had trouble with the mode lines (I have a new 42" Sony Bravia LCD TV and am still getting to grips with it's display).

It would be good if you (or anyone) could post their xorg.conf file from mythbuntu.

Cheers

---

### Post by majoridiot on 2008-04-05
> **arjay1 said:**
> I haven't seen a file like it either!  Here it is:

# xorg.conf (X.Org X Window System server configuration file)
#<snip>

As you can see no real info at all.

I did try one old file but had trouble with the mode lines (I have a new 42" Sony Bravia LCD TV and am still getting to grips with it's display).

It would be good if you (or anyone) could post their xorg.conf file from mythbuntu.

Cheers

yeah... that's missing just a *little* bit of information LOL!

you have never stated your video card, driver, etc. so it's pretty hard to come up with
an xorg.conf out of thin air...  two tings to try:

boot into "recovery" mode (esc within 3 seconds @ the grub prompt on boot) to 
bring up the boot menu. once you are logged into a recovery session:

```
$ sudo dpkg-reconfigure xserver-xorg
```

this will take you through X configuration again and (should) let you select mouse, keyboard,
video driver, etc.  for now, i would select the generic or open-source driver for you video
card (vesa, nv, etc.)- make *especially* sure to set-up only the resolutions that your 
card/display can handle and remove ones you will not be using.

once everything is reconfigured,  you should be able to reboot into mythbuntu and at least 
get far enough to pull up MCC and install/configure the appropriate restricted driver.

alternatively, you can post info on you video card, etc. and we can help you cobble together
an xorg.conf that will get you far enough to get to MCC and restricted drivers manager.

/me recommends option 1, first. ;)

---

### Post by arjay1 on 2008-04-05
You'll never believe this, but it WAS $ sudo dpkg-reconfigure xserver.xorg that produced the crappy xorg.conf file that I posted!!  However, it did give me a functioning system - video card, keyboard and mouse etc - no complaints really.

It is just that now I am trying to get the Microsoft remote keyboard and mouse up and running, I need the detailed info on the current configuration.  I can then try some different settings for the mouse and keyboard.  Other than that, I am just hacked off that xorg.conf doesn't show this stuff - or for that matter - the config for the video card.

I am not at the mythbuntu PC right now but can post you the info on the video card when I can get on it.  I am using the onboard chip for now as I have had problems recently with my nvidia fx5200 card.  It works beautifully in any pc you can think of but not a pc with a via epia chipset - apparently this is quite well known.  It gives spontaneous reboots and other weird happenings with mythbuntu AND mythdora if fitted in the pc with the via board. (Tried it with vesa, nv and prop. drivers - always the same problems).  

IIRC, MMC describes the graphics "card" as an i810 Intel Graphics Card and the driver as Intel 845 - if that means much to you.  The screen runs at 1920x1080@60.  Not sure what else i can tell you.

Appreciate your continued help

---

### Post by majoridiot on 2008-04-05
> **arjay1 said:**
> You'll never believe this, but it WAS $ sudo dpkg-reconfigure xserver.xorg that produced the crappy xorg.conf file that I posted!!  However, it did give me a functioning system - video card, keyboard and mouse etc - no complaints really.

It is just that now I am trying to get the Microsoft remote keyboard and mouse up and running, I need the detailed info on the current configuration.  I can then try some different settings for the mouse and keyboard.  Other than that, I am just hacked off that xorg.conf doesn't show this stuff - or for that matter - the config for the video card.

I am not at the mythbuntu PC right now but can post you the info on the video card when I can get on it.  I am using the onboard chip for now as I have had problems recently with my nvidia fx5200 card.  It works beautifully in any pc you can think of but not a pc with a via epia chipset - apparently this is quite well known.  It gives spontaneous reboots and other weird happenings with mythbuntu AND mythdora if fitted in the pc with the via board. (Tried it with vesa, nv and prop. drivers - always the same problems).  

IIRC, MMC describes the graphics "card" as an i810 Intel Graphics Card and the driver as Intel 845 - if that means much to you.  The screen runs at 1920x1080@60.  Not sure what else i can tell you.

Appreciate your continued help

maybe try a slightly different approach with:

```
$ sudo dkpg-reconfigure -phigh xserver-xorg
```

that should generate a full default config to work from.

---

### Post by arjay1 on 2008-04-05
Sorry, my bad.  I should have said that I tried both expressions - one with, and one without, -phigh - the result was the same sort of output for the xorg,conf.

Frustrating innit?

EDIT: nothing to lose as this is a test machine only - I'll try the command again as per your suggestion and post the output.

---

### Post by arjay1 on 2008-04-05
OK - very strange this.  I ran the command "dpkg-reconfigure -phigh xserver-xorg" and got exactly the same xorg.conf except for it changing the keyboard from GB back to US.  However, I got no interactive dialogue screens - it just created the xorg and backed up the original.

So I deleted the xorg file completely and re-ran the command.  This time it offered me some choices about the keyboard which I filled in (gb, pc105 etc) and then it skipped right out without anything to do with the screen, video etc.

What is going on?

---

### Post by majoridiot on 2008-04-05
> **arjay1 said:**
> OK - very strange this.  I ran the command "dpkg-reconfigure -phigh xserver-xorg" and got exactly the same xorg.conf except for it changing the keyboard from GB back to US.  However, I got no interactive dialogue screens - it just created the xorg and backed up the original.

So I deleted the xorg file completely and re-ran the command.  This time it offered me some choices about the keyboard which I filled in (gb, pc105 etc) and then it skipped right out without anything to do with the screen, video etc.

What is going on?

go ahead and post an old xorg.conf that worked and we can use that to create something that will hopefully work now.

---

### Post by arjay1 on 2008-04-05
Sure - will do, Unfortunately it will have to be tomorrow.  I have two HDDs on my test machine - one of which is the test setup of mythbuntu and one is actually working so i am recording a film right now!!!!!!!!!

---

### Post by superm1 on 2008-04-05
A majority of drivers are automatically configured now as you discovered.  Any "old" options that were available can still be used however.

---

### Post by prosonik on 2008-04-05
Hi!

Alot of people seem to be having some issues with the newer xorg. I'm an nvidia user. I didn't catch your hardware. I let the nvidia driver figure stuff out. The key to your settings is in your logs. if your an ati user, change the nvidia to ati.  I use:

 pic /var/log/Xorg.0.log | grep 'NVIDIA(0)' | less

and just scroll through  it.

as you can see below, you can find all sorts of intresting settings in there:

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TVStandard" "HD1080p"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TV Standard string: "HD1080p"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600 GTS (G84) at PCI:4:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.55.00.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600 GTS at PCI:4:0:0:
(--) NVIDIA(0):     WDE WESTINGHOUSETX-42F430S (CRT-0)
(--) NVIDIA(0): WDE WESTINGHOUSETX-42F430S (CRT-0): 400.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled


hope this helps,

ps, there some xorg wizards over at the knoppmyth forums. I'm a converted mythbuntu user, but i still use there wiki and forums.. if you are having alot of problems, it's worth checking out there.

prosonik

---

### Post by Baul on 2008-04-05
Hope this will help!

I was having no end of trouble with recent upgrade of Hardy Beta kernal (from 12 to 15/) which seemed to cause problems with my nivdia driver and gnome panels.

Also the menu Application>Other>Screen and Graphics had disappeared and would not reactive when I tick the box in System>Preferences>Main Menu

Don't know why the above happen but found on a post this command sudo displayconfig-gtk that at lest brought up the screen and graphic box again.

This enabled me to adjust (after a fresh install and update) the Monitor display in Model input so that I could get 1024x768 rather than the previous 800x600 default - again this appeared to fix/ allowed me to use nivdia option again.

The Xorg.conf had attempted to default to a Generic LCD Panel which appears to have caused some of  the problems!!!.


My Machine specs are

AMD 64 Dual Core 4200+
Magic View Plug and Play (quite old from my first computer!)
and 
Gainward Nvidia 7800 GS AGP
on a ASRock 939A8X-M motherboard

Overall I think Hardy is shaping up well and it fun being a Beta basher as a noobie!

---

### Post by arjay1 on 2008-04-06
> **superm1 said:**
> A majority of drivers are automatically configured now as you discovered.  Any "old" options that were available can still be used however.

superm1

Thanks for the info.  I think for a lot of linux users who are not very expert, what they want to hear is "it is good to know it is not just me"!!  

I was very surprised (and not a little annoyed) to find the lack of information in the latest xorg.conf files.  As I said in an earlier post, this is very reminiscent of MS Windows - where they don't want you to know what is going on - either because it is commercial confidence, or, worse, because they don't trust you to make the right changes...

When you say "Any "old" options that were available can still be used however" - I take it you mean that we can still insert the Options and Sections that we used to do?  

My more general question to you as the resident expert is "Where are the actual settings held on the computer, now that xorg.conf does not list them?  Presumably when xorg is called it has to go somewhere to find the actual settings (keyboard, mouse, screen, video driver etc) and load them.  So, how does it know where to go, and where are they? <g>

---

### Post by arjay1 on 2008-04-06
To the other good folks who have chipped in - thanks for the contributions.  Actually, I am using the onboard graphics chip rather than a separate video card - see earlier posts in this thread, so the advice on nvidia settings etc might help others but doesn't really help me.

---

### Post by arjay1 on 2008-04-07
OK guys - never got an answer to my original question which was "Where does the new style xorg.conf files store the actual settings?" (As the new style xorg does not show any of the settings - see posts above).

However - I have been able to set up my own xorg.conf which DOES show the settings.  This file is good for a standard keyboard and two button PS2 mouse, for an onboard INTEL graphics chip and a 1920x1080 Sony Bravia KDL-40W3000 LCD TV:

```
 Section "ServerLayout"
  Identifier "XFree86 Configured"
  Screen 0 "Screen0" 0 0
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "PS/2 Mouse" "CorePointer"
EndSection

Section "ServerFlags"
  Option "AllowMouseOpenFail" "true"
EndSection

Section "Files"
# Xorg 7.0 font paths

FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/misc:unscaled"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
EndSection

Section "Module"

EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "keyboard"
  Option "CoreKeyboard"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "gb"
#  Option "XKbOptions" ""
EndSection


Section "InputDevice"
  Identifier "PS/2 Mouse"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/psaux"
  Option "Emulate3Buttons" "false"
  Option "Emulate3Timeout" "70"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection



Section "Monitor"
  Identifier "Monitor0"
  VendorName "unknown"
  ModelName "unknown"
  Option "DPMS" "true"
  HorizSync    67.5
  VertRefresh  60

EndSection



Section "Device"
  Identifier  "Card0"
  Driver "intel"
  BoardName "unknown"
  Screen 0
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 24
  
  SubSection "Display"
  Depth 8
  Modes "1920x1080" "1280x1024" "1024x760""800x600"
  EndSubSection
  SubSection "Display"
  Depth 15
  Modes "1920x1080""1280x1024" "1024x760""800x600"
  EndSubSection
  SubSection "Display"
  Depth 16
  Modes "1920x1080""1280x1024" "1024x760" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 24
  Modes "1920x1080""1280x1024" "1024x760" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 32
  Modes "1920x1080""1280x1024" "1024x760""800x600"
  EndSubSection

EndSection

 
Section "Extensions"
  Option "Composite" "Enable"
EndSection
```


Note:  Mythbuntu's MCC does not reliably select the correct driver for my 845 chip - it sometimes chooses the i810 driver (which works fine except only up to 1280x1024.  It won't allow 1920x1080). But if you choose "intel" as the driver, as per my xorg.conf - it runs 1920 just fine.  BTW - you will see no Modeline expressions in the xorg file.  These are selected automagically - I found that inserting them in the actual Device Monitor section crashed X.  YMMV.

I have also tried it with a Radeon 9200 Pro video card as well and it works fine if you just change the driver from "intel" to "ati".

Hope this helps someone.

I am still interested if anyone has the answer to my original question - superm1 never came back?

RJ

---

### Post by majoridiot on 2008-04-07
> **arjay1 said:**
> OK guys - never got an answer to my original question which was "Where does the new style xorg.conf files store the actual settings?" (As the new style xorg does not show any of the settings - see posts above).
I am still interested if anyone has the answer to my original question - superm1 never came back?

RJ

i'm following up on this with superm1 and will post the info back here, once i find out what is up with the new "autoconfig".

as i said, my xorg.conf is as it always has been, so i have no way of troubleshooting it myself.

in the meantime, i'm glad you got it working again!

---

### Post by majoridiot on 2008-04-07
ok... here's the deal with the "new" xorg.conf situation:

the settings are generated on-the-fly at boot and are not actually "stored" anywhere for editing.  apparently, the rationale
is to hopefully eliminate xorg.conf entirely.

so, if the "auto configured" settings are failing, you should look at the Xorg.0.log to see what the problems are, and edit/add/replace
the offending sections by hand.

in the meantime, it's a really good idea for anyone fighting this issue to work from an older known-working xorg.conf and to make
a backup of the working xorg.conf, once you get on to play nicely.  that way, if anything goes awry, you can simply copy over
your backup.  i've made it a habit to *always* keep muliple copies of my working xorg.conf in more than one location, specifically
to make setting up X correctly a painless copy procedure.

hope this helps.

---

### Post by Regenpak on 2008-04-07
Can't say I'm charmed by the idea of an "invisible" xorg.conf file. With 7.04 it was easy, just hack around a bit, with 7.10 it appeared to be changed with settings modified using the GUI, and now there is nothing meaningful in this file? Well, if building my own xorg.conf manually fixes my D201GLY video problems (crappy SiS driver documented elsewhere, maybe I'll get this nice little board to work) then hiding it would be something I could live with. But this sure was unexpected!

---

### Post by arjay1 on 2008-04-07
Hey majoridiot - thanks for clearing that up.  Like you, I have dozens of old xorg.conf files saved around the place.  Their names make interesting reading - I have files (long forgotten now) that are called things like: xorg.conf.working.butonlyonescreen, and xorg.conf.ati9200.broken.butworthplayingwith!!  however,  a newbie coming to linux for the first time is not going to have a bank of xorg files he/she can use as templates for a new setup.

Bit disturbed to hear that the new style xorg is created on the fly.  This is fine if you have a good diagnostic program like Win XP that tells you exactly what driver you are using, what all the settings are and so on.  Also where you can "roll back" a new driver install.  The one thing linux could do well to implement.  

I know that you can get some info from the Xorg.0.log file but it is not in a format that a newbie would want to cut and paste to what is in effect now a blank xorg.conf file.  The info in the log file is not set out in a way that could be transferred to the xorg.conf file - for example, the Modeline statements have no quote marks in the log file.  If you didn't know that you needed to put Modeline "1920x1080@60" ...etc... you would be dead in the water.

Maybe we will have to create a new section in the forum with xorg.conf files that have worked for different setups in the past....

Anyway - I'll mark this up as solved.

Thanks to one and all

RJ

---

### Post by webaake on 2008-04-23
In spite of installing latest Envyng and latest Nvidia drivers I get this message in the log file:

(cat /var/log/Xorg.0.log | grep EE)

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Seems all my resolutionproblems stems from Envy not working or the Nvidia driver not working.

I've tried to choose the other drivers in Envy, 169.xx and 96.xx but then Envy crashes.

Is there another way to install Nvidia drivers?

---

### Post by arjay1 on 2008-04-23
Presumably you have tried the drivers in mythbuntu control centre?  It installs them automagically?

---

### Post by majoridiot on 2008-04-23
> **webaake said:**
> In spite of installing latest Envyng and latest Nvidia drivers I get this message in the log file:

(cat /var/log/Xorg.0.log | grep EE)

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Seems all my resolutionproblems stems from Envy not working or the Nvidia driver not working.

I've tried to choose the other drivers in Envy, 169.xx and 96.xx but then Envy crashes.

Is there another way to install Nvidia drivers?

envy is a good way to stay up with the *latest* drivers, but not necessarily a good idea, unless
you *have* to always be running the latest and greatest.

the restricted driver manager included in ubuntu and mythbuntu is the best way to install proprietary
drivers, as it keeps the system sane.  unless you know for sure that an "issue" you are having is a
bug for *sure*, then it's not a good idea to use envy with mythbuntu.

---

### Post by arjay1 on 2008-04-23
Couldn't agree more.  Mythbuntu is well packaged and the nvidia drivers included in the package seem to work most of the time for most people.  I don't think Envy and Mythbuntu are a good mix.

---

### Post by axel_oxenstierna on 2008-04-23
Thx for all the input! 

I solved my issues by installing the latest beta driver from Nvidia (173.x) and found out that I'd chosen the wrong monitor in "Displays and graphics".

---

