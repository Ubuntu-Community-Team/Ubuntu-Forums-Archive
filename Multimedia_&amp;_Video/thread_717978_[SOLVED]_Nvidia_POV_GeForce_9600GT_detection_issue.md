---
title: "[SOLVED] Nvidia POV GeForce 9600GT detection issues in Gutsy"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by atomp on 2008-03-07
This is regarding a fresh install of Ubuntu Gutsy onto a new system with a 9600GT.
Upon boot a message appears that informs me that the video card or monitor couldn't be detected and offers the option to set it up manually.

I found the monitor; Dell E770P, but the graphic cards only went up to the GeForce 8000 series. Thus i am stuck with the card set to generic VESA driver, and 800x600 res.

Installing the Nvidia drivers didn't work, as the Restricted Drivers Manager didn't recognise that the card needed them, and this is my second attempt at fixing this after breaking and reinstalling once.

I'm just really looking to get Ubuntu to work with the card as it would with say, a 7600GT series (last card i experienced in Ubuntu).

Any help in getting Ubuntu to recognise the card would be much appreciated, this card is just begging to play with compiz. :)

---

### Post by Roboticexile on 2008-03-07
Hmm, i read an article that came out last week about there being a good few weeks wait before the linux drivers for the 9series cards will be released, unless someone in the community has tried writing a driver for the card themselves already and could send you a copy?
sorry i can't be more helpful:(

---

### Post by atomp on 2008-03-07
Cheers for the reply.

I'm not even sure that it's a driver issue.

Ubuntu just isn't detecting the card.

I tried Envy, it commented that it couldn't detect what card it was and that i could try a manual install at my own risk. I decided this was an unwise choice.

I believe there are drivers that have been released that will support the card. But in my experience, Ubuntu driver installation isn't much use if Ubuntu doesn't recognise that the hardware needs drivers.

Once again thanks for your assistance in advance.

---

### Post by llamafier on 2008-03-07
I'm in the _**exactly**_ same position! (800x600 sucks) It seems the problem is that there are no linux drivers available for this card yet. It is just too new. :(

I was searching around and found [this](http://forums.nvidia.com/index.php?showtopic=60737):

[http://forums.nvidia.com/index.php?showtopic=60737](http://forums.nvidia.com/index.php?showtopic=60737)

so apparently [these](ftp://download.nvidia.com/XFree86/Linux-x86/171.05/) drivers will work:

[ftp://download.nvidia.com/XFree86/Linux-x86/171.05/](ftp://download.nvidia.com/XFree86/Linux-x86/171.05/)

I just have no idea how to install them, and I'm using the 64bit version so that probably will complicate things. :(

---

### Post by sanddgroper on 2008-03-07
Hi
I did see a new driver package in Hardy the other day
something like nvidia-glx-new-en dont know how up to date
that is.

Cheers
Sandy

---

### Post by Melcar on 2008-03-07
The current proprietary drivers do not support the card.  The drivers in the repos are much older, so no support either.  The nv module in Gutsy is too old to support the card as well.  There is an older version of the proprietary drivers that does "support" the card (the support is not official, but the card somehow works with it), but users have been reporting problems and poor performance with that particular driver.

---

### Post by xmas47 on 2008-03-08
Beta's available.

Haven't installed it yet, but am about to...

[I]
Linux Display Driver - x86

Version: 171.06
Operating System: Linux x86
Release Date: March 7, 2008

Release Highlights

    * Added support for GeForce 9600 GT.[/I]


[http://www.nvidia.com/object/linux_display_ia32_171.06.html]("http://www.nvidia.com/object/linux_display_ia32_171.06.html")

---

### Post by llamafier on 2008-03-08
Took me a while to figure out how to install that but I finally got it.

No more bad resolution! :D

---

### Post by atomp on 2008-03-08
Well i got the new Nvidia drivers installed. Then upon reboot, it still informs me that it couldn't detect the video card and monitor, as before.

I've checked that the drivers installed by attempting to install them again, the installer said that there were drivers already installed.

But i'm still getting the original problem. Is it some problem with the xorg.conf maybe? Perhaps it's not using the drivers or some such.

Once again cheers for the help.

llamafier - Could you possibly go into more detail on how you installed them? Was it following the readme on the nvidia site?

---

### Post by llamafier on 2008-03-08
Did you get through the Nvidia installer and stuff? I just did that and at the end it said it updated my xorg file. Then I just started x back up and it worked.

The only problems I had was that I didn't really know what I was doing and just figured the basic stuff out through Google. I could list exactly what I did but if you got through the installer, then that is basically all I did.

---

### Post by xmas47 on 2008-03-08
had to screw around a bit to get it working

here's the basic route I travelled:

saved .run file on Desktop as nvidia9600.run

followed this

[I]Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed[/I]

from here: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

The pressed CTRL-ALT-F1
logged in as me
ran 
[FONT="Courier New"]sudo /etc/init.d/kdm stop[/FONT] (that'd be "gdm stop" instead of "kdm stop" if you're using gnome)
then ran 
sudo sh /home/me/Desktop/nvidia9600.run
chose to let it autoconfig the xserver
ran
[FONT="Courier New"]startx[/FONT]

Here I was able to log in as usual and log in to my KDE desktop

edited xorg.conf (sudo kate /etc/X11/xorg.conf or sudo gedit /X11/xorg.conf)
added under the section "Device"

[FONT="Courier New"]Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"[/FONT]


and added
[FONT="Courier New"]
Section "Module"
	Load		"glx"
EndSection[/FONT]

at the end of the file. don't forget the blank line at eof

I'm not sure which of these steps are necessary, because I'm quite a noob myself, but I've got the driver installed and Compiz/Emerald running, and most importantly,  the 9600's fan isn't running constantly  at full speed anymore :)

---

### Post by atomp on 2008-03-08
Cheers for the responses. This helps make things a little clearer.

I followed the same steps to the installation it seems. Although upon attempting to restart the X-Server i was given this message:

Fatal sever error:
no screens found

XIO : fatal IO error 104 (connection reset by peer) on xerver ":0.0"
         after 0 requests (1 known processed) with 0 events remaining.

Upon reboot, i was once again presented with the message that the card and monitor couldn't be detected. However this time, i selected my monitor (Dell E770P) and just the VESA driver (as i could not find anything above the 8000series in the list). This followed to a login screen that was severly distorted across the horizontal axis. There were many small lines running across 'distorting' the image beyond usability.

---

### Post by xmas47 on 2008-03-08
I was getting an error message about screens being found, but none having a usable configuration.

Here's the relevant sections from the xorg.conf that didn't work:

[FONT="Courier New"]
Section "Device"
	Identifier	"nVidia Corporation NVIDIA 9600 GT"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Philips 190S"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA 9600 GT"
	Monitor		"Philips 190S"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection[/FONT]


and here's the same sections from the working xorg.conf. The Nvidia installer configured both of these at different times, but I only got error messages with the previous config.

[FONT="Courier New"]Section "Monitor"
    Identifier     "Philips 190S"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Philips 190S"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection[/FONT]

---

### Post by atomp on 2008-03-08
I actually think my screen problem is a continuation of an earlier, larger problem.

I noticed that prior to the screen detection problem there is this error message:

 (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!

And prior to that a message commenting that the driver version wasn't the same as the kernel version. I would give you the exact text, but i can't find it in the logs.

I know this is solvable, but the issue is i haven't a clue how. There is a solution in the [driver readme]("ftp://download.nvidia.com/XFree86/Linux-x86/171.05/README/README.txt") under section 8, but the wording of the answer, and the actual solution it suggests is beyond my current understanding.

How would i go about updating the kernel?

Once again, all help on this matter is appreciated, i haven't a clue why this hasn't gone smoothly, but i'm sure this will happen to someone else at some point, hence making all solutions found and posted useful.

---

### Post by atomp on 2008-03-08
I am a great deal pleased. I have fixed the problem.

[http://bitshifting.blogspot.com/2007/01/nvidia-kernel-upgrade-woes.html](http://bitshifting.blogspot.com/2007/01/nvidia-kernel-upgrade-woes.html)

This site had the answer. Following these steps (with some done in synaptic rather that apt) worked.

1. 'sudo nano /etc/modules'. Add the 'nvidia' module to the list.
2. 'sudo nano /etc/default/linux-restricted-modules-common'. Make sure the file looks like: 'DISABLED_MODULES="nv"
3. Press 'ctrl-alt-F2' to open a new terminal, and enter the following:
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg2.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start
3. Reboot the computer and it should come up.

Thanks to all and i hope this thread comes in useful if anyone else runs into similar problems.

---

### Post by xmas47 on 2008-03-08
If you installed a previous driver via Envy, make sure you run the "uninstall the nvidia driver" option in envy, then while running the vesa driver,

run this[FONT="Courier New"]
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common [/FONT]

then this[FONT="Courier New"]
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed[/FONT]

then this
[FONT="Courier New"]sudo rm /etc/init.d/nvidia-*[/FONT]

You apparently should also remove the linux-restricted-modules package (mine was linux-restricted-modules-2.6.22-14-generic) Edit: or you can edit /etc/default/linux-restricted-modules-common to include the line DISABLED_MODULES="nv"

Then press ctrl-alt-f1, log in, stop the x server, then run the nvidia installer again

?

---

### Post by xmas47 on 2008-03-08
oh i posted that before i saw your previous post

hehe

---

### Post by asemblR on 2008-03-11
Worked for Me :-)
Gutsy 8.04 Alpha 6 x86_64
evga GeForce 9600GT SuperClocked  Driver 171.06
clean install,

funny thing is tho, I did a little updating. did a reboot and it didn't work!!
I guess I installed the restricted modules and crap. it was not on there before.
had to remove with the "purge" option and double check all the module cfg's 
re-install the 171.06 driver/module and fire it up again!

:guitar:

---

### Post by isecore on 2008-03-14
> **atomp said:**
> I am a great deal pleased. I have fixed the problem.

[http://bitshifting.blogspot.com/2007/01/nvidia-kernel-upgrade-woes.html](http://bitshifting.blogspot.com/2007/01/nvidia-kernel-upgrade-woes.html)

This site had the answer. Following these steps (with some done in synaptic rather that apt) worked.

1. 'sudo nano /etc/modules'. Add the 'nvidia' module to the list.
2. 'sudo nano /etc/default/linux-restricted-modules-common'. Make sure the file looks like: 'DISABLED_MODULES="nv"
3. Press 'ctrl-alt-F2' to open a new terminal, and enter the following:
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg2.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start
3. Reboot the computer and it should come up.

Thanks to all and i hope this thread comes in useful if anyone else runs into similar problems.

Thanks, man! There was something missing which prevented my driver to install correctly, but I followed your steps and now it works perfectly. Alien Arena runs niiiiice now :)

---

### Post by Myke Greywolf on 2008-03-24
Thanks to this thread, I finally managed to get my new 9600GT card working in Gutsy. Thanks, guys! For a while, I really thought that I would be stuck with Windows for a few weeks while proper driver support wasn't implemented.

---

### Post by xmas47 on 2008-04-11
just noting that the same process is fine for the new driver 173.08.

The installer looks like it's been updated a bit, as well

---

### Post by travelinman81 on 2008-04-11
Well I was hoping that, the new driver would eliminate my TV's overscan problem but It didn't

---

### Post by patchoro on 2008-04-18
@ isecore:

Thnx, this worked like a charm.
Gotta love the community!

---

### Post by Azraelthe7th on 2008-04-20
Thanks, **atomp**, that solved my problems! :D

Things appear to be running faster/smoother, but there's a random choppyness to it too, though I think it's the driver.

---

### Post by isecore on 2008-04-20
> **Azraelthe7th said:**
> Things appear to be running faster/smoother, but there's a random choppyness to it too, though I think it's the driver.

For me, I found that the 171-driver ran a lot smoother than the newer 173-driver. With 173 I got a lot of choppy behaviour and general weirdness, while 171 runs fine.

---

### Post by xmas47 on 2008-04-24
ETQW has what appears to be serious framerate issues and I'm seeing a lot of tearing in Compiz with 173 driver.

Install procedure works on Hardy, though.

---

### Post by Azraelthe7th on 2008-04-25
Ugh, I updated to Hardy, and it wasn't working properly.  I reset the Xorg file, then tried installing the driver.  Nothing.  It's as though it's not even reading the card.

---

### Post by Azraelthe7th on 2008-05-03
And I finally got it to work!  Although, Hardy wants to re-install the removed packages via the update manager.  I'm not sure what to do.

---

### Post by jfeole on 2008-06-01
Thanks guys..just got the latest drivers working with my new 9600GT too with the advice here..

It appears that the fix for me was these 2 things after cleaning all failed drivers off and then loading the latest official nvidia x64 driver:

1) add the word nvidia to the /etc/modules file

2) check the /etc/default/linux-restricted-modules-common'. Make sure the file looks like: 'DISABLED_MODULES="nv"

Thanks again..

JFeole

---

### Post by Bryan on 2008-06-09
Using the instructions in this thread I finally got my NVIDIA 9600GT working.  I had to add one line to the "Screen" section of my xorg.conf though:

```

Option "NoPowerConnectorCheck" "True"

```

---

### Post by Alpinist on 2008-06-14
> **isecore said:**
> For me, I found that the 171-driver ran a lot smoother than the newer 173-driver. With 173 I got a lot of choppy behaviour and general weirdness, while 171 runs fine.

With the 173 driver I was getting 12900 - 13000 FPS in glxgears.  Backed out to the 171.06 driver and getting 14900 - 15000 FPS.  A 15% increase from the 171 beta driver over the latest 173 driver.

---

### Post by openElements on 2008-07-09
Thanks to you guys, I got my GeForce 9600GT working with the nvidia driver 173.14.09.    I love the Ubuntu community!

---

