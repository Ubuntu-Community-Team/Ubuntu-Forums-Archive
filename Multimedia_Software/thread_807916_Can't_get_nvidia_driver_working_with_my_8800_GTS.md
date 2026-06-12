---
title: "Can't get nvidia driver working with my 8800 GTS"
date: 2008-05-26
forum: Multimedia Software
---

### Post by Dorkmaster Flek on 2008-05-26
I've been dealing with this issue since I upgraded to Hardy from Gutsy.  I had it working fine in Gutsy, but the X server stuff looks quite different in Hardy.  I know they made some major changes regarding it, but don't ask me the technical details.  :P  The problem is, no matter what I try, when it reaches the point where it loads the GNOME display manager during startup and the login screen is supposed to appear, it craps out and drops back down to the text interface.  A text login prompt appears, the screen blinks a couple times, and then the 640x480 'low graphics mode' screen appears asking me to configure my video card and monitor.  This happens every single time no matter what I try.  I've tried using Envy to install the drivers, and I've tried simply using the restricted driver manager, which is what everyone told me to do with 8.04 since "you don't even need Envy anymore".  :P  I can boot into recovery mode from the GRUB menu, then run xfix to reset the xorg.conf file, and then everything is great except that I have no 3D acceleration.

Here's my default xorg.conf file after using xfix to reset everything:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Okay, cool.  Pretty sparse compared to what I'm used to seeing, but I know they made some changes that supposedly make dealing with the X server easier, so whatever, we'll roll with it.  This works great, except it's the standard open source drivers so I don't have any 3D acceleration.  Now I'll install the nvidia-glx-new driver package using the restricted driver manager and enable it.  Now my xorg.conf file looks like this:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

Okay, so it's almost exactly the same, except that my video device is set to use the "nvidia" driver.  There's also the extra "Defaultdepth" setting in the screen section, and there's the module section which wasn't there before.  So I restart, and it's back to "low graphics mode".  Okay, so some people said to run this nvidia utility for configuring the X server.  "sudo nvidia-xconfig --no-composite" according to the post.  Okay, I try that.  Now I end up with some gobbldygook that looks a little more like what I saw before in Gutsy:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

Still same problem.  I tried using Envy to uninstall the whole thing, and let it reinstall it and configure it by itself.  No deal.  Same exact problem.  My monitor is a Samsung SyncMaster 204B LCD on a DVI connection.  Just a single monitor, no fancy dual screen setup like I see lots of other people having trouble with.  I just want my 3D support.

Allowing Envy to configure it ends up with a whole bunch of crap in the xorg.conf file and I don't know what to make of it.  If the standard drivers work with the extremely sparse setup in the first place, the only thing I want to change is using the nvidia drivers.  I thought I remembered reading somewhere that 8.04 was supposed to make it so you wouldn't have to deal with xorg.conf but I'm not sure.  Every post I've seen about how to install the nvidia drivers simply said to go to the restricted drivers manager and just turn it on.  It's that simple, and it worked for plenty of other people.  I don't have a clue what I'm doing wrong here.

---

### Post by PmDematagoda on 2008-05-26
If you install the Nvidia driver normally without the use of Envy, can you get a working X-Server when restarting GDM?

---

### Post by Dorkmaster Flek on 2008-05-26
You mean using the CTRL + ALT + Backspace method?  I don't think I actually tried that specifically.  I just restarted my box completely.  I did install the driver "normally" without the use of Envy.  I used the restricted driver manager in GNOME under the System menu.  I also tried using Envy with the same result: drop to text-only login prompt, screen blinks a few times, "Ubuntu is running in low graphics mode because your video card and monitor could not be configured" and whatnot.

---

### Post by PmDematagoda on 2008-05-26
I meant manually.

If you want to install the driver manually then you have to do the following:-
1) Remove the nvidia-glx-new package with:-
```
sudo apt-get remove --purge nvidia-glx-new
```

2) Install the required prerequisites for the Nvida driver install with:-
```
sudo apt-get install build-essential
```

3) Download the Nvidia driver with:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```

4) Execute the installer with:-
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

5) Start GDM with:-
```
sudo /etc/init.d/gdm start
```

If the result is still the same, then reconfigure it with:-
```
sudo dpkg-reconfigure xserver-xorg
```
and see if it works properly.

---

### Post by Dorkmaster Flek on 2008-05-26
Well, I figured it out.  I tried to install the drivers manually like you said, but it complained that the GCC version (4.2) didn't match the version my kernel was compiled in (4.1)  DANGER WILL ROBINSON!  WARNING!  WARNING!

Turns out when I upgraded from Gutsy to Hardy, I changed one tiny thing in the GRUB boot menu (I wanted to remove the quiet option, I like diagnostic info when I boot up) and it asked me if I wanted to keep my old menu.  Weeeeeeeell guess what I picked?  And guess what the version of the kernel in said menu was?

/facepalm

I changed the kernel version number to the current one and suddenly got a whole bunch of updates I didn't see before, including a new incremental kernel update!  I ran envy again to install the drivers after updating everything, and I'm enjoying Penny Arcade Adventures now.  Thanks so much for the help.

Go Linux Newbs!  :-D

---

