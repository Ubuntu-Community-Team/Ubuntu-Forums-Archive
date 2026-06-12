---
title: "Stuck in NVIDIA Driver Hell after today's kernel update"
date: 2009-01-28
forum: Multimedia Software
---

### Post by greyfox1 on 2009-01-28
OK I've been trying to fix the problems I have for several hours now so if it turns out that I have left anything out, please bear with me...

After installing the latest kernel today (2.6.27-11), I got low graphics mode and no sound when I rebooted.  I have gone through many different things to try to solve the issues and while I have gotten sound back, I am still having problems with the NVIDIA driver.  

When I go to System->Administration->Hardware Drivers and enable the recommended 177 driver and reboot, I get low graphics mode again.  I can get around this by reconfiguring Xorg (sudo dpkg-reconfigure xserver-xorg) and disabling the kernel framebuffer interface (which I have never needed to do before), but even then I still have problems: I'm not in low graphics mode anymore, but the driver is apparently not enabled.  When I go back to the Hardware Drivers utility at this point, it shows me **"a different version of this driver is in use"** when I choose the 177 driver.  At this point it becomes basically a cycle (Enable driver, reboot, reconfigure X, enable driver again, etc).  I'm stuck and I don't know how to get out of this driver hell.  Help please!

I was only able to get my sound back by booting back into 2.6.27-9 via the GRUB menu, although all the problems I described above occur in either the -9 or -11 kernel.

Before all of this started I was running the 180 driver which I had downloaded from NVIDIA's website and installed manually a few weeks ago.

Here is my xorg right now (it's just a generic config I believe):

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by greyfox1 on 2009-01-29
Some further detail:

Since I had successfully manually installed the 180 series driver prior to all this, I tried doing so again when the problems initially sprang up yesterday.  When that failed, I decided to go with the 177 series driver using the methods I described above.  This leads me to believe that the "different version of this driver" being referred to by Hardware Drivers is the 180 driver.  I think maybe I need to somehow purge the manually installed driver from my system, but I don't know how to do that.  Help would be greatly appreciated!

---

### Post by FokkerCharlie on 2009-01-30
Hi Greyfox

Sorry to hear you're having problems.  Installing 2 versions of the nvidia driver can cause problems which are a pain to solve.

I'm not a great expert on this, but I have seen something similar here.  Try uninstalling the 180.* nvidia driver, by ctrl+alt+F1, stopping the GDM, then running:

sudo sh NVIDIA.... --uninstall 

Try to reboot, then uninstall the 177 versions from the repos.  Once that is stable, re-install whichever version you like, then run:

sudo nvidia-xconfig

to get your xorg.conf back up and running.  Restart again.

Good luck!
Charlie

---

### Post by Nico0020 on 2009-01-30
I have suffered the same video related problem.  I didn't loose sound though.  I have been unable to install 177 or any of the other drivers.  I might try and install from the website the newest version, thats just always a pain.

---

### Post by greyfox1 on 2009-01-31
Thanks for the tip on uninstalling the 180 driver, Fokker.  I can at least confirm that the 177 driver is loaded now via Hardware Drivers, but I still get low graphics mode for some reason.  I have tried nvidia-xconfig, manually reconfiguring X (sudo dpkg-reconfigure xserver-xorg), or configuring X automatically (see below) but no joy.  

So basically at this point I've managed to get rid of the 180 driver and go back to the 177, but everything else is the same :/

Here are the specifics at this time:

1. When I boot, I get the message:

"Ubuntu is running in low-graphics mode

Your screen, graphics card, and input settings could not be detected correctly.  You will need to configure these yourself."

2. I click OK and I'm given the options of running in low-graphics mode for this session, reconfiguring the graphics, or toubleshooting the error.  

3. If I choose to reconfigure and choose "create new settings for this hardware" or whatever the wording is, it tells me that new settings have been created and my old ones backed up.  I then reboot, and I am back to step 1.  At any time I can log in using low-graphics mode and double check the Hardware Drivers dialog and confirm that the 177 driver is activated.

Here's my xorg.conf at the moment (generated when I chose to have it configured automatically):

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Shazaam on 2009-01-31
After you get your video drivers sorted out install dkms through Synaptic. What dkms basically will do is rebuild some kernel modules automatically when you update/upgrade the kernel. Works for VirtualBox kernel modules too.
[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)

Also...
You can try changing this part of your xorg.conf-
```
SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

to this-
```
SubSection     "Display"
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
Add higher resolutions if your monitor supports them (1400, 1600, etc).

---

### Post by DeMus on 2009-01-31
Hi,

Maybe this works for you to:
[http://ubuntuforums.org/showthread.php?t=1054842]()

It worked for me after hours of trying this and that.

---

### Post by Nico0020 on 2009-02-03
Did you ever get this solved, as I am still suffering from the same problem.

---

### Post by thethrasher on 2009-02-04
I'm Stuck in this same endless loop, running a Geforce FX 5200, crap card i know, but this is the reason i run linux. I've had no luck at all and have follow everything that you have outlined with all the same results. I never manually installed the 180 drivers. I've tried to use Envyng -t to no avail. I've even did a fresh install and still get the same results. any other ideas would be greatly appreciated

---

### Post by greyfox1 on 2009-02-04
Hi All,

I did get this solved, but unfortunately not the easy way.  I followed the advice in DeMus's thread and basically, all hell broke loose once I tried to remove restricted modules as adivsed.  I lost basically everything, including GDM.  I was at a point where it basically wasn't worth trying to repair my system since I was also left with no internet connectivity (I use ndiswrapper for a wireless USB dongle and that was gone too).

Sooo long story short, I did a complete re-install.  Fortunately I was a good boy and had already mounted a separate partition to my /home directory so I didn't lose any of my valuable stuff.  I just had to re-install Ubuntu, restore fstab, and re-install my programs.  Not too bad I guess, considering everything that went wrong.

I had not tried Shazaam's advice, although it looks sound.  I hope some info in this thread helps others who have this problem going forward.

---

### Post by SeePU on 2009-02-04
How did you get sound back?   Installing the 180.22 removed/disabled my sound, too.  

If I don't get it back soon, I'm just going to give up on this OS.  

I don't think I've been as frustrated with a problem in Ubuntu as now with this issue.  A VIDEO DRIVER INSTALL SHOULD **NOT** REMOVE, DELETE, DISABLE OR OTHERWISE LOSE YOUR SOUND.  

My kernel modules, headers, images look to be installed.  I can't think of any other culprit or reason it's gone.  But, my kmix alsamixer utility has way less equalizer channels.

---

### Post by greyfox1 on 2009-02-05
Hi SeePu,

Sorry to hear about your woes.  In my case, I lost sound when I upgraded to the 2.6.27-11 kernel from the 2.6.27-9.  It was **not** the NVIDIA 180.xx driver that caused the problem for me.  I used the 180 driver for a few weeks without any problems at all prior to updating the kernel.

I didn't look into it (I just booted back into the -9 kernel) but I think it has something to do with the fact that I removed PulseAudio.  Like I said I didn't bother to look into the sound problem on top of everything else, so I can't be sure.

As for your problem, you might be well-served checking out the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") sticky thread over in the Multimedia & Video forum.  If that doesn't do it, you should start your own thread there rather than jacking this one.  Good luck M8!

---

### Post by Nico0020 on 2009-02-09
I am really about to go crazy trying to fix this problem.  I can't seem to figure out anything that will work.  I dont want to do a reinstall of ubuntu when we are getting pretty close to April.  It was the last kernel update that did this to me, is there any way to remove what has been done?  Or is the next kernel update anytime soon?  I really want this fixed as I can't play any of my games and some video content doesn't like to play anymore.

---

