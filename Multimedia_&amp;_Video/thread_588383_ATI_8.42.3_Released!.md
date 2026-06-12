---
title: "ATI 8.42.3 Released!"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by SishGupta on 2007-10-23
I am sure many are as excited as I am:
[ATI 8.42.3]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run")

This release includes a lot of bugfixes and the much anticipated AIGLX support

And for everyones convenience, the install [HOWTO]("http://ubuntuforums.org/showthread.php?t=575843")

---

### Post by gendad on 2007-10-23
Nice :D
Downloading now!

---

### Post by VipeR_11 on 2007-10-23
Hmm, why if I go to ATI's web site they still giving me the old driver??
I have an ATI X1650 and the version they giving me for DL is the 8.40.4

and not the 8.42.3 :(

---

### Post by Rip on 2007-10-23
Try one of these links courtesy of the Phoronix forums:

[https://a248.e.akamai.net/f/674/9206...x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206...x86.x86_64.run")

[http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run")


BTW, I wonder when it will hit the repos?

---

### Post by SishGupta on 2007-10-23
> **VipeR_11 said:**
> Hmm, why if I go to ATI's web site they still giving me the old driver??
I have an ATI X1650 and the version they giving me for DL is the 8.40.4

and not the 8.42.3 :(

This was literally just released within the last hour and they haven't updated their site yet. 
Michael larabel from Phoronix who has signed an NDA to not talk about the release until it is released is now talking about the release.
Check out the [Phoronix]("http://www.phoronix.com/scan.php?page=home") page if you are interested.

---

### Post by aoanla on 2007-10-23
For me, at least, the installer doesn't work:

bash ./Desktop/ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/feisty

results in:

(lots of bug output) ending in

dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1

which is interesting, as /usr/X11R6/lib/modules/dri exists, at least.

(Feisty, AMD64 install here.)

Edit: Michael on the Phoronix forums says this is a known issue with Gusty (which is odd, considering I'm on Feisty), and there's a replacement script... check the Phoronix forums, I suspect, if you have the same problem as me.

Edit2: [http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2](http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2)  is the link for the new package installer scripts. 
You'll need to do:

bash atiinstallername --extract some-directory
and Cd to the some-directory you chose
then unpack the above archive into it, replacing the existing packages directory contents

then ./ati-installer.sh 8.42.3 --buildpkg Ubuntu/feisty

(then continue from there in the HOWTO linked in the first post)

---

### Post by spasoje on 2007-10-23
Installed like charm and that is about all that i got.

fglrixinfo fails on second monitor



[I]fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6958 Release



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6958 Release

*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x080621b8 ***
[/I]
There is bunch of trace output

WoW does not work (e.g. it starts but there is missing layer, i got same situation with 8.41 drivers) guess i will have to rollback to  8.40

root@thinkpad:~$ wine --version
*wine-0.9.46*
rootv@thinkpad:~$ uname -a
Linux thinkpad *2.6.20-16-generic* #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

Thinkpad is T42

---

### Post by fizz on 2007-10-23
can i install over top my previous envy install using the instructions at the top?

---

### Post by avanderveen on 2007-10-23
I have Ubuntu 7.10 32-bit but on a 64-bit processor. Can I still use this driver even though the file ends with "_x64"?

---

### Post by SishGupta on 2007-10-23
> **fizz said:**
> can i install over top my previous envy install using the instructions at the top?
Thats what I did, ill let you know how it went...

---

### Post by KLineD on 2007-10-23
> **SishGupta said:**
> Thats what I did, ill let you know how it went...

I'm having a lot of trouble to get this working. fglrxinfo gives me:

```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

And looking at /var/log/Xorg.0.log:

```

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Tracing the source of the error I see the following line:

```
drmOpenDevice: node name is /dev/dri/card0
```
but there's no card0 in /dev/dri

And that's where I'm stuck right now.

---

### Post by MaximB on 2007-10-23
I'm dying to see it updated on Ubuntu repros !
I can wait a few days but can anyone confirm if there would be such update in gusty, or would we must install it the hard way ?

---

### Post by aoanla on 2007-10-23
> **avanderveen said:**
> I have Ubuntu 7.10 32-bit but on a 64-bit processor. Can I still use this driver even though the file ends with "_x64"?

Yes - the package builds for 32-bit and 64-bit on install.


(People with full 64-bit installs may want to hang back on this upgrade - I've found that it seems to break wine, even on older versions that work with 8.41.7 - and other amd64 users with other distros have found it to be unreliable.

It seems to be fine for 32-bit users, though.)

---

### Post by SishGupta on 2007-10-23
OK, someone asked if you could install this over an envy install using the instructions in the parent post (my post)...

and you can! everything works well for me on my 32 bit gutsy with a x1950pro

compiz is smooth as a baby's bottom.

:guitar::guitar::guitar:

---

### Post by aoanla on 2007-10-23
> **KLineD said:**
> I'm having a lot of trouble to get this working. fglrxinfo gives me:

```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

And looking at /var/log/Xorg.0.log:

```

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Tracing the source of the error I see the following line:

```
drmOpenDevice: node name is /dev/dri/card0
```
but there's no card0 in /dev/dri

And that's where I'm stuck right now.

Uninstall the packages you installed, and then do a 

locate fglrx

and remove the files you find, especially any dri like ones.

then reinstall the driver as before.

(this is how I fixed my 8.41.7 install when it was doing this - apparently, the dri module isn't always updated or something....)

---

### Post by SishGupta on 2007-10-23
> **KLineD said:**
> I'm having a lot of trouble to get this working. fglrxinfo gives me:

```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```And looking at /var/log/Xorg.0.log:

```

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```Tracing the source of the error I see the following line:

```
drmOpenDevice: node name is /dev/dri/card0
```but there's no card0 in /dev/dri

And that's where I'm stuck right now.

I would suggest reading the phoronix forums, they have been talking about your problem i think...

---

### Post by KLineD on 2007-10-23
Thanks for the suggestions everyone. I ended up following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") (method 2: manual install) and it worked for me.

Now trying out Compiz

---

### Post by mikeymackinon on 2007-10-23
How do you use the .run file?

---

### Post by F-3582 on 2007-10-23
Say, did anyone manage to get Compiz running with that driver, yet? The driver installed without any big problems (yes, there is an "Ubuntu/gutsy" option in the installer). However, I still can't enable Compiz, although OpenGL is definitely provided by this driver.

---

### Post by daradib on 2007-10-23
> **mikeymackinon said:**
> How do you use the .run file?

Follow the install [howto]("http://ubuntuforums.org/showthread.php?t=575843"). You will use it to generate deb packages.

---

### Post by SishGupta on 2007-10-23
> **F-3582 said:**
> Say, did anyone manage to get Compiz running with that driver, yet? The driver installed without any big problems (yes, there is an "Ubuntu/gutsy" option in the installer). However, I still can't enable Compiz, although OpenGL is definitely provided by this driver.

enable compositing in your xorg.conf
whitelist the fglrx driver in /usr/bin/compiz

---

### Post by SishGupta on 2007-10-23
These drivers work pretty well for me. There are some issues but this is a great start.

AIGLX works well, and thats what i really wanted.
3d works well
fgl_glxgears gets me 3000+ fps with aiglx goin

Issues:
Firefox scrolling
Some compiz effects are jittery, while others are very smooth
Videos flicker so much that they are unwatchable

I have a x1950pro

---

### Post by Tamale on 2007-10-23
after installing this driver and restarting x, everything compiz-related was running ridiculously slow

i then removed xserver-xgl with apt and tried again, and then started getting the white screen of death when compiz tried to start.  compiz was loading even in my failsafe gnome session, so i can't login to x at all.

i've tried the skip checks fix and the white listing fix and neither stop the white screen problem.

any other ideas?  i'm in the #compiz-fusion channel on irc and would love some assistance. :)

computer is a c2d laptop with an ati mobility x1600 pro

---

### Post by myname on 2007-10-23
I just tried with the latest version of Envy, and envy is still downloading the 8.40 driver.  I have a Radeon x1600, will the 8.42 drivers work with this?

--kevin

---

### Post by Hero of Time on 2007-10-23
I got the same question. I have a x1400 Mobility Radeon in my laptop, will this driver allow me to use AIGLX? If not, why should I upgrade from the version I have now (I think it's 8.40).

---

### Post by nkessler2000 on 2007-10-23
Not working here :( 

Still trying to use Mesa instead of the ATI driver for GL, and no matter what I do it doesn´t seem to work. 
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

---

### Post by Fenix-TX on 2007-10-23
Not working :-(
```
jesus@tux-CT:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

jesus@tux-CT:~$ glxinfo |grep mesa
OpenGL vendor string: Mesa project: www.mesa3d.org
```

---

### Post by SveinT on 2007-10-23
Not working here either:

flgrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

Compiz just showing white screen...

---

### Post by rbmorse on 2007-10-23
Works here on an X1950XTX.  I had to add the fglrx driver to the driver whitelist in /usr/bin/compiz to get desktop effects going. 

Only problem is that video flickers badly when set to Vx.  Mplayer and X11 works fine for me, but some find it slow.

---

### Post by Tamale on 2007-10-23
> **Tamale said:**
> after installing this driver and restarting x, everything compiz-related was running ridiculously slow

i then removed xserver-xgl with apt and tried again, and then started getting the white screen of death when compiz tried to start.  compiz was loading even in my failsafe gnome session, so i can't login to x at all.

i've tried the skip checks fix and the white listing fix and neither stop the white screen problem.

any other ideas?  i'm in the #compiz-fusion channel on irc and would love some assistance. :)

computer is a c2d laptop with an ati mobility x1600 pro

I found an uninstaller finally.

/usr/share/ati/fglrx-uninstall.sh

i ran this with "sudo sh" and it finished without errors, and then i reinstalled xgl with "sudo apt-get install xserver-xgl"

i then restarted the computer, x had a hard time starting but finally did in a low graphics mode, then i started the restricted driver manager, disabled ati, then enabled it again and rebooted.

i'm back in x with compiz working properly.  hope this helps anyone who also found the new driver to not work properly.

---

### Post by MaximB on 2007-10-23
> **SishGupta said:**
> enable compositing in your xorg.conf
whitelist the fglrx driver in /usr/bin/compiz
They new drivers support composition ?
Cuz in every other driver this option needed to be disabled.

---

### Post by dunomous on 2007-10-23
I am also in agreeance about seeing this driver in the repos. Because my effects run fine, I'm in no hurry to upgrade. Because I love to tinker and try new things, I would like to upgrade when all the details/problems have been panned out. 

So! I'm asking does anyone know the plan or schedule, if it exists, for this to be released in the repos? As an AIGLX user, I am eager.

---

### Post by rbmorse on 2007-10-23
> **MaximB said:**
> They new drivers support composition ?
Cuz in every other driver this option needed to be disabled.

yes. 

Getting it work on a specific machine is proving to be a bit problematic, but at least ATI now officially supports composite with their proprietary driver.

---

### Post by daradib on 2007-10-23
> **Tamale said:**
> after installing this driver and restarting x, everything compiz-related was running ridiculously slow

i then removed xserver-xgl with apt and tried again, and then started getting the white screen of death when compiz tried to start.  compiz was loading even in my failsafe gnome session, so i can't login to x at all.

i've tried the skip checks fix and the white listing fix and neither stop the white screen problem.

any other ideas?  i'm in the #compiz-fusion channel on irc and would love some assistance. :)

computer is a c2d laptop with an ati mobility x1600 pro

Try opening a virtual terminal (Control-Alt-F2)
Login,and type the following:

```
sudo rmmod fglrx
cd /lib/modules/*/misc
sudo insmod fglrx.ko
modprobe fglrx
```

Note: The fglrx module was not found for me, but that is okay. Also, replace * with the kernel version (2.6.22-14-generic for me), but you can leave the asterisk if you have only one kernel version.

Then type exit and go back to the white screen (Control-Alt-F7) and restart the X server (Control-Alt-Backspace). This worked for me, but unfortunately I have to do it every time I start up my computer.

[B]EDIT: This worked to permanently fix the problem for me. If you installed the new driver by generating a deb package, you could try to unblacklist the fglrx module.
[/B]
Edit these two files:

```
/etc/default/linux-restricted-modules-common
/etc/modprobe.d/blacklist-restricted
```

Remove fglrx from the files if it is blacklisted.

Alternatively, the restricted driver in the restricted driver manager can be checked after the new driver is installed.

---

### Post by hqd22 on 2007-10-23
I just installed the 8.42 driver using the installer from ATI and successfully got fglrxinfo to say my card information and there's a yes to direct rendering when i type in glxinfo. However when I try to play any video files using a variety of applications, it displays only a black screen. Sounds are coming out so I know the video is playing but there's no images. I've tested the videos right before I installed the drivers and it was working fine.

My xorg file:

```


# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Logitech MX1000" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Logitech MX1000"
	Driver      "evdev"
	Option	    "Name" "Logitech USB Receiver"
	Option	    "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "enable"
EndSection


```

Thanks for the help!

---

### Post by mpiktas on 2007-10-23
Does this driver solve the suspend problem? I am holding the upgrade to Gutsy just because of this issue, so it would be good to know was it solved with the new driver, or not.

---

### Post by Dropknee on 2007-10-23
When I log-in my screen goes completely in white, the only way I found to log-in is with Gnome Failsave option.

Anyclue??

this is my xorg

```

# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "alt-intl"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerFlags"
        Option "AIGLX" "on"
EndSection

Section "Extensions"
    Option "Composite" "1"
EndSection
``` 

I add manually the AIGLX and the composite option, but still the same....white screen

pls help

Thanks

---

### Post by thegnark on 2007-10-23
> **SishGupta said:**
> These drivers work pretty well for me. There are some issues but this is a great start.

AIGLX works well, and thats what i really wanted.
3d works well
fgl_glxgears gets me 3000+ fps with aiglx goin

Issues:
Firefox scrolling
Some compiz effects are jittery, while others are very smooth
Videos flicker so much that they are unwatchable

I have a x1950pro

i'm experiencing similar behavior on my x600. around 3600fps in glxgears, 752 in fgl_glxgears... but firefox scrolling is horribly slow. also noticing some jittery effects. video playback just gives a black screen, but i can catch a partial frame as soon as i move the window and "let go"

not sure if these bugs are really worth it for the time being... might just revert back to ati driver

---

### Post by tolstoybikeboy on 2007-10-24
> When I log-in my screen goes completely in white, the only way I found to log-in is with Gnome Failsave option.

@Dropknee      I have that same problem. It is really annoying. I can't do anything but start in gnome failsafe as well. I have tried to find someone with the same problem/solution but have nothing. My setup is Gutsy 32bit on AMD Turion 64x2 and ATI Xpress 1100. 

Anyone else having this problem?

---

### Post by hvbakel on 2007-10-24
Unfortunately the suspend issue does not seem to be solved with this new driver, it still hangs with a black screen.

---

### Post by aaaantoine on 2007-10-24
I got the fglrx drivers to work briefly, but then spinning the cube (read: changing the workspace) caused a hard lock, and I haven't been able to get the drivers working since.

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

AMD Turion 64x2, ATI Xpress 1100, Gutsy 64-bit.

---

### Post by Melcar on 2007-10-24
I can compile the driver without errors, but the driver doesn't load; I always get mesa instead of fglrx.

---

### Post by furyy on 2007-10-24
Got installed (or so it seemed) but it appearently keeps loading 8.36.7 DRM module (???) ,thus no DRI, though it was fresh install of gutsy and no xorg-driver-fglrx was installed before that. So where the h*** does it find it ? :D

---

### Post by APGunner on 2007-10-24
Yay yet another crappy driver release from ati. Wonderful. I installed the driver using this guide. [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). and I still get the mesa driver when I go fglrxinfo. THANK YOU for yet another wonderful driver release ati. My next card is definitely going to be nvidia. OO btw this was on a CLEAN install of ubuntu so that just makes it even worse. The ati 8.41 driver worked for me and this won't very sad.

---

### Post by Technophobia on 2007-10-24
I followed everything and it worked. I have an ATI Mobile Rad 9600.

---

### Post by raist78 on 2007-10-24
> **APGunner said:**
> Yay yet another crappy driver release from ati. Wonderful. I installed the driver using this guide. [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). and I still get the mesa driver when I go fglrxinfo. THANK YOU for yet another wonderful driver release ati. My next card is definitely going to be nvidia. OO btw this was on a CLEAN install of ubuntu so that just makes it even worse. The ati 8.41 driver worked for me and this won't very sad.

The same guide worked for me and i got my ATI Radeon x1950pro AGP finally working. As far as i can see,the only glitch is that compiz fusion is a bit slow.

---

### Post by supertux on 2007-10-24
i get a segfault when i start amdcccle :

```

 catchsegv amdcccle
*** Segmentation fault
Register dump:

 EAX: 08aebb68   EBX: b7db7114   ECX: 08aeb628   EDX: 00000000
 ESI: 08afa168   EDI: 08afa1d0   EBP: bfa652d8   ESP: bfa65240

 EIP: b7db4454   EFLAGS: 00010216

 CS: 0073   DS: 007b   ES: 007b   FS: 0000   GS: 0033   SS: 007b

 Trap: 0000000e   Error: 00000004   OldMask: 00000000
 ESP/signal: bfa65240   CR2: 00000004

 FPUCW: ffff037f   FPUSW: ffff0022   TAG: ffffffff
 IPOFF: 0856d55d   CSSEL: 0073   DATAOFF: bfa65258   DATASEL: 007b

 ST(0) 0000 bb78000000000000   ST(1) 0000 a87160956c0d6f54
 ST(2) 0000 a3d66277c45cbbc3   ST(3) 0000 0000000000000000
 ST(4) 0000 0000000000000000   ST(5) 0000 8000000000000000
 ST(6) 0000 ffffffffff510000   ST(7) 0000 0000000000000000

Backtrace:
/lib/libSegFault.so[0xb7f2004f]
??:0(??)[0xffffe420]
/usr/lib/libXrandr.so.2(XRRGetScreenInfo+0x4a)[0xb7db458a]
amdcccle(_ZN14CDisplayDriver17GetResolutionListEjPSt6vectorI7resInfoSaIS1_EE+0x18f)[0x81611df]
amdcccle(_ZN12CDisplayRule13GetDriverDataEP12CDisplayData9DRVACCESS+0x2b9)[0x8187229]
amdcccle(_ZN12CDisplayRule10InitializeEP10IAppAccess+0x157)[0x8185ec7]
amdcccle(_ZN4CLDC10InitializeEv+0x8dc)[0x81554fc]
amdcccle(main+0x4d4)[0x8153e04]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7a6f050]
amdcccle[0x8150b61]

Memory map:

08048000-088e7000 r-xp 00000000 08:02 5014335 /usr/bin/amdcccle
088e7000-089a8000 rwxp 0089f000 08:02 5014335 /usr/bin/amdcccle
089a8000-08b26000 rwxp 089a8000 00:00 0 [heap]
b76f7000-b777b000 r-xp 00000000 08:02 5474782 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b777b000-b77bf000 r-xp 00000000 08:02 5637383 /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b77bf000-b784a000 r-xp 00000000 08:02 5474781 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b784a000-b7850000 r-xs 00000000 08:02 6718689 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b7850000-b7851000 r-xs 00000000 08:02 6718686 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b7851000-b7853000 r-xs 00000000 08:02 6718685 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b7853000-b7854000 r-xs 00000000 08:02 6718684 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b7854000-b7855000 r-xs 00000000 08:02 6718683 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b7855000-b7859000 r-xs 00000000 08:02 6718682 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b7859000-b785a000 r-xs 00000000 08:02 6718681 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b785a000-b785b000 r-xs 00000000 08:02 6718680 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b785b000-b785d000 r-xs 00000000 08:02 6718679 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b785d000-b7860000 r-xs 00000000 08:02 6718678 /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b7860000-b7862000 r-xs 00000000 08:02 6718677 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b7862000-b7863000 r-xs 00000000 08:02 6718676 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b7863000-b7865000 r-xs 00000000 08:02 6718675 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b7865000-b786b000 r-xs 00000000 08:02 6718674 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b786b000-b786d000 r-xs 00000000 08:02 6718673 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b786d000-b786f000 r-xs 00000000 08:02 6718672 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b786f000-b7877000 r-xs 00000000 08:02 6718671 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b7877000-b787d000 r-xs 00000000 08:02 6718670 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b787d000-b787e000 r-xs 00000000 08:02 6718669 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b787e000-b7895000 r-xs 00000000 08:02 6718668 /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b7895000-b7897000 r-xs 00000000 08:02 6718667 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b7897000-b789d000 r-xs 00000000 08:02 6718666 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b789d000-b78a0000 r-xs 00000000 08:02 6718665 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b78a0000-b78a4000 r-xs 00000000 08:02 6718176 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b78a4000-b78a6000 r-xs 00000000 08:02 6718652 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b78a6000-b78a7000 r-xs 00000000 08:02 6718741 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b78a7000-b78a8000 r-xs 00000000 08:02 6718740 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b78a8000-b78a9000 r-xs 00000000 08:02 6718729 /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b78a9000-b78ab000 r-xs 00000000 08:02 6718724 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b78ab000-b78ae000 r-xs 00000000 08:02 6718723 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b78ae000-b78b7000 r-xs 00000000 08:02 6718720 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b78b7000-b78ba000 r-xs 00000000 08:02 6718718 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b78ba000-b78bb000 r-xs 00000000 08:02 6718717 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b78bb000-b78bd000 r-xs 00000000 08:02 6718716 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b78bd000-b78be000 r-xs 00000000 08:02 6718714 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b78be000-b78c3000 r-xs 00000000 08:02 6718712 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b78c3000-b78c7000 r-xs 00000000 08:02 6718711 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b78c7000-b78c9000 r-xs 00000000 08:02 6718709 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b78c9000-b78cc000 r-xs 00000000 08:02 6718708 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b78cc000-b78cd000 r-xs 00000000 08:02 6718706 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b78cd000-b78ce000 r-xs 00000000 08:02 6718705 /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b78ce000-b78d0000 r-xs 00000000 08:02 6718699 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b78d0000-b78d6000 r-xs 00000000 08:02 6718698 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b78d6000-b78dc000 r-xs 00000000 08:02 6718697 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b78dc000-b78dd000 r-xs 00000000 08:02 6718696 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b78dd000-b78e5000 r-xs 00000000 08:02 6718695 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b78e5000-b78ea000 r-xs 00000000 08:02 6718694 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b78ea000-b78ed000 r-xs 00000000 08:02 6718693 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b78ed000-b78f3000 r-xs 00000000 08:02 6718692 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b78f3000-b7932000 r-xp 00000000 08:02 5079870 /usr/lib/locale/en_US.utf8/LC_CTYPE
b7932000-b7933000 r-xp 00000000 08:02 5079875 /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7933000-b7934000 r-xp 00000000 08:02 5079878 /usr/lib/locale/en_US.utf8/LC_TIME
b7934000-b7a14000 r-xp 00000000 08:02 5079869 /usr/lib/locale/en_US.utf8/LC_COLLATE
b7a14000-b7a16000 rwxp b7a14000 00:00 0
b7a16000-b7a1a000 r-xp 00000000 08:02 5014828 /usr/lib/libXfixes.so.3.1.0
b7a1a000-b7a1b000 rwxp 00003000 08:02 5014828 /usr/lib/libXfixes.so.3.1.0
b7a1b000-b7a39000 r-xp 00000000 08:02 5013535 /usr/lib/libexpat.so.1.0.0
b7a39000-b7a3b000 rwxp 0001e000 08:02 5013535 /usr/lib/libexpat.so.1.0.0
b7a3b000-b7a4f000 r-xp 00000000 08:02 5015586 /usr/lib/libz.so.1.2.3.3
b7a4f000-b7a50000 rwxp 00013000 08:02 5015586 /usr/lib/libz.so.1.2.3.3
b7a50000-b7a51000 rwxp b7a50000 00:00 0
b7a51000-b7a55000 r-xp 00000000 08:02 5014822 /usr/lib/libXdmcp.so.6.0.0
b7a55000-b7a56000 rwxp 00003000 08:02 5014822 /usr/lib/libXdmcp.so.6.0.0
b7a56000-b7a58000 r-xp 00000000 08:02 5014811 /usr/lib/libXau.so.6.0.0
b7a58000-b7a59000 rwxp 00001000 08:02 5014811 /usr/lib/libXau.so.6.0.0
b7a59000-b7b9d000 r-xp 00000000 08:02 1852386 /lib/tls/i686/cmov/libc-2.6.1.so
b7b9d000-b7b9e000 r-xp 00143000 08:02 1852386 /lib/tls/i686/cmov/libc-2.6.1.so
b7b9e000-b7ba0000 rwxp 00144000 08:02 1852386 /lib/tls/i686/cmov/libc-2.6.1.so
b7ba0000-b7ba3000 rwxp b7ba0000 00:00 0
b7ba3000-b7bad000 r-xp 00000000 08:02 1818646 /lib/libgcc_s.so.1
b7bad000-b7bae000 rwxp 0000a000 08:02 1818646 /lib/libgcc_s.so.1
b7bae000-b7bd1000 r-xp 00000000 08:02 1852390 /lib/tls/i686/cmov/libm-2.6.1.so
b7bd1000-b7bd3000 rwxp 00023000 08:02 1852390 /lib/tls/i686/cmov/libm-2.6.1.so
b7bd3000-b7bd4000 rwxp b7bd3000 00:00 0
b7bd4000-b7c84000 r-xp 00000000 08:02 5014547 /usr/lib/libstdc++.so.5.0.7
b7c84000-b7c89000 rwxp 000af000 08:02 5014547 /usr/lib/libstdc++.so.5.0.7
b7c89000-b7c8e000 rwxp b7c89000 00:00 0
b7c8e000-b7d14000 r-xp 00000000 08:02 5014332 /usr/lib/libGL.so.1.2
b7d14000-b7d16000 rwxp 00086000 08:02 5014332 /usr/lib/libGL.so.1.2
b7d16000-b7d18000 rwxp b7d16000 00:00 0
b7d18000-b7d1f000 r-xp 00000000 08:02 5014834 /usr/lib/libXi.so.6.0.0
b7d1f000-b7d20000 rwxp 00006000 08:02 5014834 /usr/lib/libXi.so.6.0.0
b7d20000-b7d34000 r-xp 00000000 08:02 1852400 /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d34000-b7d36000 rwxp 00013000 08:02 1852400 /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d36000-b7d38000 rwxp b7d36000 00:00 0
b7d38000-b7d40000 r-xp 00000000 08:02 5014818 /usr/lib/libXcursor.so.1.0.2
b7d40000-b7d41000 rwxp 00007000 08:02 5014818 /usr/lib/libXcursor.so.1.0.2
b7d41000-b7dad000 r-xp 00000000 08:02 7782429 /usr/lib/libfreetype.so.6.3.16
b7dad000-b7db1000 rwxp 0006b000 08:02 7782429 /usr/lib/libfreetype.so.6.3.16
b7db1000-b7db2000 rwxp b7db1000 00:00 0
b7db2000-b7db7000 r-xp 00000000 08:02 5014846 /usr/lib/libXrandr.so.2.1.0
b7db7000-b7db8000 rwxp 00005000 08:02 5014846 /usr/lib/libXrandr.so.2.1.0
b7db8000-b7dbf000 r-xp 00000000 08:02 5014848 /usr/lib/libXrender.so.1.3.0
b7dbf000-b7dc0000 rwxp 00006000 08:02 5014848 /usr/lib/libXrender.so.1.3.0
b7dc0000-b7de3000 r-xp 00000000 08:02 5014024 /usr/lib/libfontconfig.so.1.2.0
b7de3000-b7deb000 rwxp 00023000 08:02 5014024 /usr/lib/libfontconfig.so.1.2.0
b7deb000-b7ed8000 r-xp 00000000 08:02 7782473 /usr/lib/libX11.so.6.2.0
b7ed8000-b7edc000 rwxp 000ed000 08:02 7782473 /usr/lib/libX11.so.6.2.0
b7edc000-b7ee9000 r-xp 00000000 08:02 5014826 /usr/lib/libXext.so.6.4.0
b7ee9000-b7eea000 rwxp 0000d000 08:02 5014826 /usr/lib/libXext.so.6.4.0
b7eea000-b7eec000 r-xp 00000000 08:02 1852389 /lib/tls/i686/cmov/libdl-2.6.1.so
b7eec000-b7eee000 rwxp 00001000 08:02 1852389 /lib/tls/i686/cmov/libdl-2.6.1.so
b7eee000-b7ef5000 r-xp 00000000 08:02 5014801 /usr/lib/libSM.so.6.0.0
b7ef5000-b7ef6000 rwxp 00006000 08:02 5014801 /usr/lib/libSM.so.6.0.0
b7ef6000-b7ef7000 rwxp b7ef6000 00:00 0
b7ef7000-b7f0c000 r-xp 00000000 08:02 5014783 /usr/lib/libICE.so.6.3.0
b7f0c000-b7f0e000 rwxp 00014000 08:02 5014783 /usr/lib/libICE.so.6.3.0
b7f0e000-b7f0f000 rwxp b7f0e000 00:00 0
b7f0f000-b7f10000 r-xp 00000000 08:02 5079873 /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f10000-b7f11000 r-xp 00000000 08:02 5079879 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f11000-b7f12000 r-xp 00000000 08:02 5079876 /usr/lib/locale/en_US.utf8/LC_PAPER
b7f12000-b7f13000 r-xp 00000000 08:02 5079874 /usr/lib/locale/en_US.utf8/LC_NAME
b7f13000-b7f14000 r-xp 00000000 08:02 5079868 /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f14000-b7f15000 r-xp 00000000 08:02 5079877 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f15000-b7f16000 r-xp 00000000 08:02 5079872 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f16000-b7f1d000 r-xs 00000000 08:02 5047210 /usr/lib/gconv/gconv-modules.cache
b7f1d000-b7f1e000 r-xp 00000000 08:02 5079871 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f1e000-b7f21000 r-xp 00000000 08:02 1819263 /lib/libSegFault.so
b7f21000-b7f23000 rwxp 00002000 08:02 1819263 /lib/libSegFault.so
b7f23000-b7f25000 rwxp b7f23000 00:00 0
b7f25000-b7f3f000 r-xp 00000000 08:02 1819243 /lib/ld-2.6.1.so
b7f3f000-b7f41000 rwxp 00019000 08:02 1819243 /lib/ld-2.6.1.so
bfa53000-bfa69000 rwxp bfa53000 00:00 0 [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0 [vdso]

```

---

### Post by fettuohi on 2007-10-24
I got my HD 2400XT ATI card (256 MB) running with the ATI 8.42.3 driver and AIXGL and it is running quite nicely. I'm getting around 4300+ with glxgears and 950+ with fgl_glxgears. My only problem is that when I start a video file the screen suddenly turn black for a short second and then the video starts. Has anyone else experiences that? The issue wasn't present with the 8.41.7 driver but then again XGL was running there.

Regards

André

PS. Here is my working xorg.conf file on Gutsy (32 bit)


# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
	FontPath "/usr/share/fonts/X11/misc"
        FontPath "/usr/share/fonts/X11/cyrillic"
        FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath "/usr/share/fonts/X11/Type1"
        FontPath "/usr/share/fonts/X11/CID"
        FontPath "/usr/share/fonts/X11/100dpi"
        FontPath "/usr/share/fonts/X11/75dpi"
        FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection


Section "Module"
        Load "i2c"
        Load "bitmap"
        Load "ddc"
        Load "dri"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "type1"
        Load "vbe"
        Load "dbi"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "dk"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "MIRAI DML-51"
	HorizSync    28.0 - 72.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc ATI Default Card"
	Driver      "fglrx"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
	Option      "XaaNoOffscreenPixmaps"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Default Card"
	Monitor    "MIRAI DML-51"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

Section "DRI"
        Mode 0666 
EndSection

---

### Post by alina.bolero on 2007-10-24
I did this:

[LIST=1]
[*]executed the install on my HP Pavilion dv8000 with ATI Radeon Xpress 200M
[*]cd; touch .config/xserver-xgl/disable
[*]added composite and aiglx support to my xorg.conf
[/LIST]

full xorg.conf:

```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Radeon Express 200M"
        Driver          "fglrx"
        BusID           "PCI:1:5:0"
        Option          "BlockSignalsOnLock" "on"
        Option          "KernelModuleParm" "agplock=0"
        Option          "OpenGLOverlay" "off"
        Option          "UseFastTLS" "2"
        Option          "UseInternalAGPGART" "no"
        Option          "VideoOverlay" "on"
        Option          "mtrr" "off"
        Option          "no_accel" "no"
        Option          "no_dri" "no"
        Option          "EnablePrivateBackZ" "no"
        Option          "backingstore" "true"
EndSection

Section "Extensions"
        Option          "Composite"     "1"
EndSection

Section "ServerFlags"
        Option          "AIGLX"         "on"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Radeon Express 200M"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1268x854" "1213x665" "1024x768" "800x600" "640
x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1268x854" "1213x665" "1024x768" "800x600" "640
x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1268x854" "1213x665" "1024x768" "800x600" "640
x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1268x854" "1213x665" "1024x768" "800x600" "640
x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1268x854" "1213x665" "1024x768" "800x600" "640
x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1268x854" "1213x665" "1024x768" "800x600" "640
x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

some interesting snippets from my Xorg.0.log:

```

(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.42.3
        Module class: X.Org Video Driver
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(**) fglrx(0): NoDRI = NO
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                22 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
...
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0

```

dmesg said:

```

[   21.576000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg,
 GERMANY' taints kernel.
[   21.596000] [fglrx] Maximum main memory to use for locked dma buffers: 1777 MBytes.
[   21.596000] [fglrx] ASYNCIO init succeed!
[   21.596000] [fglrx] PAT is enabled successfully!
[   21.664000] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0
[   56.744000] [fglrx:drm_parse_option] *ERROR* "agplock" is not a valid option
[   56.744000] [fglrx] Maximum main memory to use for locked dma buffers: 1777 MBytes.
[   56.748000] [fglrx] GART Table is not in FRAME_BUFFER range 
[   56.748000] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   56.748000] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000

```

```

# fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.42.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: drmOpenMinor returns 5
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release

```

```

# glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.42.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: drmOpenMinor returns 5
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
display: :0  screen: 0
direct rendering: Yes
...

```

Which is just FABULOUS news!  I almost cried.

My only problem now is that when I try to start compiz I get:

```

# compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

---

### Post by alina.bolero on 2007-10-24
I added fglrx to the whitelist in /usr/bin/compiz:

```

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

```

but then I got:

```

# compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '1002:5955' found 
aborting and using fallback: /usr/bin/metacity

```

so I changed:

```

T="   1002:5954 1002:5854 1002:5955" # ati rs480

```

to:

```

T="   1002:5954 1002:5854" # ati rs480

```

then I got:

```

# compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

which sort of suggests that it's running, but I'm not seeing any of my compiz effects.  They appear to be enabled in the plugin options.   hmmmmmmmm ....

---

### Post by alina.bolero on 2007-10-24
OOOHHHHHHHHHHHHHH!!!!!!

I just rebooted and she's purring like a wet kitty with Compiz working!

I'm a very happy girl.

It was very obvious that there was a significant performance gain in the operation of Secondlife.  However, there was also a really nasty flicker the whole time that made the screen almost unbearable to look at.  Those with photoepilepsy be warned.  

I also encountered problems running GoogleEarth and playing videos.

the fix for OpenGL apps on the ATI Radeon Xpress 200M in general is to use the Extra WM Options toggles mentioned here:  [http://ubuntuforums.org/showthread.php?p=3633378#post3633378]("http://ubuntuforums.org/showthread.php?p=3633378#post3633378")

the fix for playing videos is here:  [http://ubuntuforums.org/archive/index.php/t-507332.html]("http://ubuntuforums.org/archive/index.php/t-507332.html")

-Alina

---

### Post by AncientPC on 2007-10-24
How I got Compiz working on my setup:
Gutsy Gibbons v7.10 for AMD64
(Asus) ATI x1950 Pro

I initially tried following [AMD's instructions]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.40.4-inst.html").  I got dual head support, but no direct rendering (glxgears at ~500fps, glxinfo | grep direct), and thus no Compiz support.

So I tried the instructions in [aoanla's helpful post]("http://ubuntuforums.org/showpost.php?p=3611928&postcount=6").  Where it says HOWTO he is referring to [URL="http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually"]this[url]. (note: I did **not** need to add fglrx to restricted modules list)

Despite the packages installing correctly (fglrx-amdcccle* didn't give me error messages), the kernel would not compile.

So I decided to go ahead and use the automatic install method.  Low and behold, I now have Compiz working in addition to dual head support and ATI config GUI. :)  On a side note, with the restricted 8.37.6 drivers I was getting ~12,000 fps in glxgears, now I only get ~8,500 fps.

---

### Post by aoanla on 2007-10-24
> **AncientPC said:**
> How I got Compiz working on my setup:
Gutsy Gibbons v7.10 for AMD64
(Asus) ATI x1950 Pro

> 
So I decided to go ahead and use the automatic install method.  Low and behold, I now have Compiz working in addition to dual head support and ATI config GUI. :)  On a side note, with the restricted 8.37.6 drivers I was getting ~12,000 fps in glxgears, now I only get ~8,500 fps.

Interesting. I have a similar setup to you (except Feisty AMD64 rather than Gutsy), and I found the 8.42.3 drivers were a little faster but less stable than 8.41.7.

Perhaps I should roll back to 8.37.6, if it's good for you...

---

### Post by fettuohi on 2007-10-24
> **alina.bolero said:**
> OOOHHHHHHHHHHHHHH!!!!!!

I just rebooted and she's purring like a wet kitty with Compiz working!

I'm a very happy girl.

It was very obvious that there was a significant performance gain in the operation of Secondlife.  However, there was also a really nasty flicker the whole time that made the screen almost unbearable to look at.  Those with photoepilepsy be warned.  

Figured out that if I turn Compiz off, then SL runs fine.  I had become accustomed to about 2-3 frames per second (fps) in SL.  I'm now getting about 20 fps!!!!!!!!!    I'm just .... WOW!  .... I'm gonna wet myself.

-Alina

:guitar:

Can you watch video files without it going into this black screen before the video starts?

Regards

André

---

### Post by xocekim on 2007-10-24
Im trying to install the new drivers and im getting this error
```
sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 180: dpkg-architecture: not found
Error: unsupported architecture: 

```

Using x86 Gutsy and Radeon 9600
Any ideas? Thanks

Fixed - should of read howto better, sorry :(
```
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper \
debconf libstdc++5 linux-headers-generic
```

---

### Post by chefweb on 2007-10-24
@xocekim

This works good for me:

```
 sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.HT8341
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package /home/ulrich/Desktop/ati/xorg-driver-fglrx_8.42.3-1_i386.deb has been successfully generated
Package /home/ulrich/Desktop/ati/xorg-driver-fglrx-dev_8.42.3-1_i386.deb has been successfully generated
Package /home/ulrich/Desktop/ati/fglrx-kernel-source_8.42.3-1_i386.deb has been

```

but the next step is broken:

```
 sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb  xorg-driver-fglrx fglrx-amdcccle_8.42.3-1_i386.deb 
(Reading database ... 202008 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.42.3-1 (using fglrx-kernel-source_8.42.3-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
dpkg: error processing xorg-driver-fglrx (--install):
 cannot access archive: No such file or directory
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.42.3-1_i386.deb) ...
dpkg: error processing fglrx-amdcccle_8.42.3-1_i386.deb (--install):
 trying to overwrite `/usr/bin/amdcccle', which is also in package xorg-driver-fglrx
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Setting up fglrx-kernel-source (8.42.3-1) ...
Errors were encountered while processing:
 xorg-driver-fglrx
 fglrx-amdcccle_8.42.3-1_i386.deb

```

I read in another forum that the ati installer has a bug.

---

### Post by hqd22 on 2007-10-24
> **fettuohi said:**
> Can you watch video files without it going into this black screen before the video starts?

Regards

André

I am having this trouble as well. Don't know what's wrong. Before installing the drivers, it's fine. I am also unable to start compiz but I do have direct rendering. Can anybody provide a guide?

---

### Post by Sokar on 2007-10-24
Installed them (with many problems), and when everithing seems to work fine, compiz, aplications, etc.. i've discovered that i have a very nasty flicker in videos and 3D programs (games, google earth..)

I didn't have any flicker with 8.40 drivers... anyone can tell me how to fix it?

Thanks :P

---

### Post by F-3582 on 2007-10-24
Read the first post on page 3. It explains how to whitelist the driver for Compiz.

Oh, one more thing: Does anyone know how to enable blur? No matter how I tweak the plugins, I can't get it working...

---

### Post by Sokar on 2007-10-24
> **F-3582 said:**
> Read the first post on page 3. It explains how to whitelist the driver for Compiz.

Oh, one more thing: Does anyone know how to enable blur? No matter how I tweak the plugins, I can't get it working...

Sorry, i'm new in all this

The first post on page 3 says "enable compositing in your xorg.conf
whitelist the fglrx driver in /usr/bin/compiz"

What i have to do to whitelist it?

Thanks

---

### Post by aoanla on 2007-10-24
> **chefweb said:**
> @xocekim

This works good for me:

```
 sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.HT8341
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package /home/ulrich/Desktop/ati/xorg-driver-fglrx_8.42.3-1_i386.deb has been successfully generated
Package /home/ulrich/Desktop/ati/xorg-driver-fglrx-dev_8.42.3-1_i386.deb has been successfully generated
Package /home/ulrich/Desktop/ati/fglrx-kernel-source_8.42.3-1_i386.deb has been

```

but the next step is broken:

```
 sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb  xorg-driver-fglrx fglrx-amdcccle_8.42.3-1_i386.deb 
(Reading database ... 202008 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.42.3-1 (using fglrx-kernel-source_8.42.3-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
dpkg: error processing xorg-driver-fglrx (--install):
 cannot access archive: No such file or directory
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.42.3-1_i386.deb) ...
dpkg: error processing fglrx-amdcccle_8.42.3-1_i386.deb (--install):
 trying to overwrite `/usr/bin/amdcccle', which is also in package xorg-driver-fglrx
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Setting up fglrx-kernel-source (8.42.3-1) ...
Errors were encountered while processing:
 xorg-driver-fglrx
 fglrx-amdcccle_8.42.3-1_i386.deb

```

I read in another forum that the ati installer has a bug.

It has a bug for 64bit ubuntu, which I explained how to deal with on the first page of this topic! For you, there is no bug, only a typo.

sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb  xorg-driver-fglrx fglrx-amdcccle_8.42.3-1_i386.deb 

should be
sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb  xorg-driver-fglrx_8.42.3-1_i386.deb fglrx-amdcccle_8.42.3-1_i386.deb

---

### Post by F-3582 on 2007-10-24
> **Sokar said:**
> Sorry, i'm new in all this

The first post on page 3 says "enable compositing in your xorg.conf
whitelist the fglrx driver in /usr/bin/compiz"

What i have to do to whitelist it?

Thanks
/usr/bin/compiz is a shell script. The easiest way to edit it would be pressing Alt+F2 and type the following line into the small window that opens:

gksu gedit /usr/bin/compiz

The look for a line saying something like whitelist drivers or something. In the line below just add fglrx to the rest of those drivers.

---

### Post by Trevster on 2007-10-24
The first post in this thread explains how to whitelist fglrx.

[http://ubuntuforums.org/showthread.php?t=588428](http://ubuntuforums.org/showthread.php?t=588428)

---

### Post by gillis on 2007-10-24
i am getting an error

bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/feisty
Created directory fglrx-install.rU7118
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/feisty
./packages/Ubuntu/ati-packager.sh: 175: dpkg-architecture: not found
Error: unsupported architecture:
Removing temporary directory: fglrx-install.rU7118

i am trying to install it on a hp nc8000 laptop with an ati 9600.
i have seen more people with this problem, but none of them found an answer.
someone knows the solution?

---

### Post by F-3582 on 2007-10-24
Did you follow the guide on wiki.cchtml.com ?

---

### Post by Miguel on 2007-10-24
Hi guys,

I've got an ATi Mobility Radeon 9600 and fglrx 8.42.3 installed. However, compiz fusión seems slower on some plugins (such as fade-in and fade-out) than with the open-source radeon driver. Is anybody experiencing something similar? 3D is working properly, though (except from some stuttering in Torcs when running desktop-effects).

---

### Post by F-3582 on 2007-10-24
Same here. And blur effects (except motion blur) don't seem to work, no matter what I try.

---

### Post by cinlo on 2007-10-24
Edit: Bit silly, solved the first problem by disabling xgl and whitelisting fglrx in compiz as suggested. glxgears gives me ~5000fps which is a bit lower than what I had before on the gutsy repo drivers.

The installation went OK without any errors. fglrxinfo returns:

[INDENT]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6958 Release[/INDENT]

Unfortunately, glxinfo | grep direct returns:

[INDENT]direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect[/INDENT]

and glxgears will cause a crash to login. I assume Mesa is not want I want here.


Also a more minor issue but following the HOWTO in the OP seems to have defaulted my resolution to 1600*1200 which my monitor can't support. I used <ctrl + alt + -> to lower the resolution and change it in the preferences however, the login screen still uses 1600*1200 so I have to lower it again before I can login, at which point it'll go back down to 1280*1024. 

Is there a separate setting for the login screen that I'm missing?

thanks

---

### Post by aoanla on 2007-10-24
> **Miguel said:**
> Hi guys,

I've got an ATi Mobility Radeon 9600 and fglrx 8.42.3 installed. However, compiz fusión seems slower on some plugins (such as fade-in and fade-out) than with the open-source radeon driver. Is anybody experiencing something similar? 3D is working properly, though (except from some stuttering in Torcs when running desktop-effects).

Many people are reporting that the open source radeon driver is faster with compiz than the new fglrx driver, for those cards which are supported by both, yes.

---

### Post by CarmeloV on 2007-10-24
Simply:
1) this 8.42.3 is not official from ATI.
2) then, is a beta driver.
3) then, is slow, etc........
4) and then, all you are beta testers of a unofficial driver
5) So, I wait just to the official release from ATI (can be a 8.42.4???)

Bye
Carmelo Viavattene

---

### Post by wildcard on 2007-10-24
> **Trevster said:**
> The first post in this thread explains how to whitelist fglrx.

[http://ubuntuforums.org/showthread.php?t=588428](http://ubuntuforums.org/showthread.php?t=588428)

Hmmm...I'm using Mint 3.1 (based off of Ubuntu Feisty) and my /usr/bin/compiz has NO reference to any lines about a whitelist or blacklist. (used the FIND feature of gedit to confirm that there was no reference for either term in both upper and lower case)

I'm reasonably sure that I do have everything configured correctly(direct rendering is 'yes' via glxinfo, fglrxinfo shows my ATI Radeon Xpress 200M, and 3d and Compiz are working well), but I'm still having the same annoying screen flicker on Compiz (I'm reasonably sure I'm still on 0.5.2 Compiz-pc is at home, I'm at work...) that I did with an XGL desktop and just want to rule out any issues. Other posts on 200M flickering indicated that enabling direct rendering cleared up the flickering for them, but I still have it.
Curiously, 3d Games like PenguinRacer do NOT show the flickering when displaying full screen.

Is this just Compiz related wierdness?

---

### Post by bpickel on 2007-10-24
I have the new driver installed and it is working just fine. I was having the Mesa issue but runnin the installer with

sudo ./installerfilename.run all worked.

The only troube I am seeing so far is flicker video playbeck when compiz is enabled but is fine with effects turned off. i am sure someone will figure this out. I guess I am will to disable effects to watch videos if it gets rid of XGL

---

### Post by wgsdd on 2007-10-24
when i follow "how to"
and install the 8.42.3 drive
then fglrxinfo :
Xlib: extension "ATIFGLRXDRI" missing on display ":0.0". 
Error: couldn't find RGB GLX visual! 

what  is wrong?
thank you
my card is radean 9600 servers

---

### Post by aoanla on 2007-10-24
> **CarmeloV said:**
> Simply:
1) this 8.42.3 is not official from ATI.
2) then, is a beta driver.
3) then, is slow, etc........
4) and then, all you are beta testers of a unofficial driver
5) So, I wait just to the official release from ATI (can be a 8.42.4???)

Bye
Carmelo Viavattene

Wrong.

This is an official ATI driver release - ATI doesn't make "unofficial" releases. Hence, this is not a beta driver, as ATI doesn't release beta drivers.

And the next driver release will be sometime in November, as the official release schedule is one release each month. And the version number will be 8.43.something.

---

### Post by damiencc on 2007-10-24
Trying to update broke fglrx for me, including the gutsy 8.37.6 version. Everything was built and installed fine, then starting X gives

"No devices found", and of course X stops there

This happens even if I revert to 8.37.6.

Thisis linked to the fact that when I insert by hand fglrx, there are fewer lines than usual, 

[   19.640000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   19.640000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0

and that's it. This is with a radeon 9700

Any idea ?

Thanks 

D.

---

### Post by CarmeloV on 2007-10-24
> **aoanla said:**
> Wrong.

This is an official ATI driver release - ATI doesn't make "unofficial" releases. Hence, this is not a beta driver, as ATI doesn't release beta drivers.

And the next driver release will be sometime in November, as the official release schedule is one release each month. And the version number will be 8.43.something.

I not see this driver in ATI download page, then is unofficial, or beta.

If 8.4.3 is the official (when released in ATI page) driver, then is not a stable and performing driver.

Bye

Carmelo Viavattene

---

### Post by tatrefthekiller on 2007-10-24
8.4.3 is a very old driver...
This IS an official driver from ATI. Maybe the latest version is just not linked yet.

---

### Post by aoanla on 2007-10-24
> **CarmeloV said:**
> I not see this driver in ATI download page, then is unofficial, or beta.

If 8.4.3 is the official (when released in ATI page) driver, then is not a stable and performing driver.

Bye

Carmelo Viavattene

I'm sorry, but you're simply wrong. 
If you read this article:
[http://www.phoronix.com/scan.php?page=article&item=735&num=1](http://www.phoronix.com/scan.php?page=article&item=735&num=1)
you will see that the ATI beta drivers are not released to anyone but a closed set of beta-testers, who have to sign NDAs. Any driver which is publically hosted on the ATI website (as this driver is) is not a beta driver.

It is simply the case that ATIs driver releases are well known for being... disappointing.

---

### Post by HornedBeast on 2007-10-24
Any have any ideas for a fix for this Slow Scrolling problem.

Some people seem to report it just scrolling slowly in Firefox, but I have the same problem with everything.

Its mainly when Compiz is running. So, if i switch it off the scrolling is fine again. Anyone have any ideas how to fix the slow scrolling issue?

Cheers in advance!

HornedBeast

---

### Post by michael37 on 2007-10-24
I received the changelog for 8.42 driver and decided to wait for 8.43 driver.  It think that will be a better solution overall.

Running 8.37 driver happily so far with Gutsy+fglrx+Xgl+Compiz.

---

### Post by amiga_os on 2007-10-24
Well... have a Mobility Radeon 9700... I installed the 8.42 driver manually.

To get compiz working I have to type:
```
SKIP_CHECKS=yes compiz
```
into a terminal.

My desktop then goes white, with some black lines outlining the windows.  When I move the cube using ctrl-alt-lmb, I can see the lines moving in a way that the cube would.

Boot up time has also increased.  What's crazy is that I had reasonable AIGLX support with the free driver in the vanilla Gutsy installation (which was, well, impressive).

I'm not sure what to be more annoyed by... a yet again spectacular failure by ATI to supply me with something to run my hardware correctly to it's full capacity, or, the way that Phoronix built up this huge fanfare about this driver.  I wouldn't have got my hopes up, or been nearly as excited if Phoronix hadn't promised the world, with the subtle hint that this "really was it", since they're linux insiders, and they'd tested it.

All this has served to do is make me trust Phoronix slightly less... which is a shame.

---

### Post by daveerickson on 2007-10-24
> **HornedBeast said:**
> Any have any ideas for a fix for this Slow Scrolling problem.

Some people seem to report it just scrolling slowly in Firefox, but I have the same problem with everything.

Its mainly when Compiz is running. So, if i switch it off the scrolling is fine again. Anyone have any ideas how to fix the slow scrolling issue?

Cheers in advance!

HornedBeast

I agree, I am looking for a scroll fix. I have a 9700 pro AGP, everything else seems to work fine.

---

### Post by Neo4 on 2007-10-24
bad news to me!
after following this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
this is my fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

i have an x700m on my laptop!

anyone can help?
ati sucks!

---

### Post by amiga_os on 2007-10-24
Since I can get AIGLX with the free drivers, I'm just going to use them.

And what's more, I'm going to make a concerted effort to bug report just about everything about the free driver, and do the best I possibly can to help development.  A Phoronix article said this in the run up to 8.42:

> The fglrx driver will continue full steam ahead with their monthly releases and will be for those who want a stable driver with top-notch performance, all of the bells and whistles, and avoid checking out the latest git code in order to get the latest fixes and features.

Well it looks like those who want a "stable driver with top-notch performance, all of the bells and whistles, and avoid checking out the latest git code in order to get the latest fixes and features." are those who'll stick to the open source drivers.

I am now more rabidly pro open source offerings... and what's galvanised me is the same things that galnvanised Richard Stallman - rubbishy binary drivers that are irritatingly bad at what they do, and surely could be improved by the people who use them.

I'm off to reboot my computer having removed all traces of fglrx from it... and this weekend will be given over to creating a partition just for gobuntu.

---

### Post by HornedBeast on 2007-10-24
So the slow scrolling bug is definatly an issue with the driver rather than my setup?

Any word on a fix?

---

### Post by h2z on 2007-10-24
I have the slowness aswell and another problem I've encountered is when running the game Enemy Territory, I cannot change the brightness, it stays the same form both the max and min value (in game settings) :/

---

### Post by Baby Boy on 2007-10-24
Has anyone tested the driver on Ati Xpress x1150 (integrated laptop GPU)?

---

### Post by Neo4 on 2007-10-24
i'm still needing help...

---

### Post by jctweb on 2007-10-24
> **Neo4 said:**
> i'm still needing help...

There are a number of things you need to check.  I can see that you still have the Mesa driver showing up.  What does your var/log/Xorg.0.log show ?  Anything in there indicate why the driver didn't load?

---

### Post by Sov on 2007-10-24
> **Neo4 said:**
> bad news to me!
after following this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
this is my fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

i have an x700m on my laptop!

anyone can help?
ati sucks!

Had the same problem, fglrx driver was not entering the kernel!
try this:
- switch to a vt console
- login
- stop gdm "sudo /etc/init.d/gdm stop"
- insert module "sudo modprobe -r fglrx"
-if the module doesn't insert:
sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
- and again "sudo modprobe -r fglrx"
- start gdm again "sudo /etc/init.d/gdm start"
- should be ok... till next reboot!

If this work you could fix "reboot resistant" removing restricted drivers

---

### Post by Sov on 2007-10-24
Here it is my experience with the new driver with Gutsy on a Macbook pro C2D (ati mobility x1600)

Got it from link to download 8.42.3  on phoronix, installed using this recipe:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually")

in /usr/bin/compiz sarched for:
```

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
 
```

and added fglrx :
```

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
 
```

Removed restricted drivers:
```
sudo apt-get remove --purge $(dpkg -l|awk '/restricted/{print $2}')
```
(DO NOT remove them if you are using any restricted driver apart from ATI, check with your restricted driver manager)

Everything seems to work OK, but found this problems:

- Slooooow compiz with AIXGL is much slower than compix on XGL with old drivers
- Scrolling in firefox is "chopy"
- Sleep is not working (I think it has todo with and incompatibility with the new SLUB memory allocator inculded in gutsy's kernel)
- video playing "not so fluid"

To make sleep work I created a script called "gotosleep.sh":
```

#!/bin/sh

/etc/init.d/gdm stop
modprobe -r fglrx
/etc/acpi/sleep.sh
/etc/init.d/gdm start

```

than switch to a VT and do this:
```
sudo gotosleep.sh
```

NOTE: if you are logged on X your session will be killed!

---

### Post by hoa3r on 2007-10-24
> **HornedBeast said:**
> So the slow scrolling bug is definatly an issue with the driver rather than my setup?

Any word on a fix?


I had the same issues with the slow performance with scrolling and moving windows, when desktop effects is turn off.

When I turn on the desktop effects the performance is much better. Scrolling and moving windows is much faster.

Performance in video and games are still very bad.

I have already remove the new driver and turn back to 8.37 from repository, that has good performance and is stable.

Hope next release will be soon with better performance.

---

### Post by Neo4 on 2007-10-24
that does't work for me after that still mesa =/ i'm getting sick of AMD!

---

### Post by jctweb on 2007-10-24
@Neo4 - have you followed [this other thread]("http://ubuntuforums.org/showthread.php?p=3621378") as well? 

What have you tried?  Can you be more specific?  What are the errors in your /var/log/Xorg.0.log?  Are you trying to use compiz?  Please give some detail so we can help.

---

### Post by ZTiger on 2007-10-24
> **Neo4 said:**
> that does't work for me after that still mesa =/ i'm getting sick of AMD!

I followed the How-to and I'm still stuck with Mesa as well. Not sure why. It was a fresh install of Gutsy and I enabled all the repositories. Everything seemed to run without a hitch and then I'm still showing 

$ fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

$ glxinfo | grep direct
```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

if your interested further here is my /etc/X11/xorg.conf
```
 

# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
#	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

NOTE: amdcccle seems to work now. Under the old drivers it would just give me an error that it couldn't load.

Some more info:
Video Card: ATI Radeon X1300
OS: Ubuntu 7.10 Gutsy

This card worked for video acceleration under 7.04 but stopped working in 7.10. I have a fresh install of Gutsy to see if I had something left over from 7.04.

I used the guide from [url="http://ubuntuforums.org/showthread.php?t=575843"]
Ati Video Driver Install for Dummies [/url]

---

### Post by Neo4 on 2007-10-24
finally ati!

just edit your xorg.conf

and in tall section called device
change the driver from ati to fglrx!

hugs

---

### Post by Styles on 2007-10-24
Everything seems to work OK like most other people, and I'm having the same issues as everyone else bellow: So in other words I get  a better experience using the older drivers and XGL.

- Slooooow compiz with AIXGL is much slower than compix on XGL with old drivers
- Scrolling in firefox is "chopy"
- Sleep is not working (I think it has todo with and incompatibility with the new SLUB memory allocator inculded in gutsy's kernel)
- video playing "not so fluid"


getting 800 900 FPS fgl_glxgears

my fglrxinfo

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X600
OpenGL version string: 2.0.6958 Release


here is how I got them installed maybe it will help somebody else.

1.) Remove Xgl

```
sudo apt-get remove xserver-xgl
```


2) Remove the old driver (if present)

Go to System &#8594; Administration &#8594; Restricted Drivers Manager and choose disable.

Alternatively remove it yourself:

```
sudo apt-get remove xorg-driver-fglrx
```


3.) Delete old fglrx debs (might not be necessary)

```
sudo rm -f /usr/src/fglrx-kernel*.deb
```


4.) Blacklist old fglrx module

```
sudo gedit /etc/default/linux-restricted-modules-common
```

And insert fglrx - it should look like this then:

```
DISABLED_MODULES="fglrx"
```


Alternatively remove the linux-restricted-modules-* package for your kernel (that's what I did, because I don't need them - don't do this, if you use an Atheros chip).


   1. You may want to reboot now. I did.

5.)  Download the driver installer to your home folder

```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run
```


6.) Install necessary packages

```
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic
```


7.) Create .deb packages

```
bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy

```

8.) Install .deb packages

```
sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb

```

9.) Compile kernel module

```
sudo m-a prepare,update

sudo m-a build,install fglrx-kernel

sudo depmod

```

10.) Set up the driver

```
sudo gedit /etc/X11/xorg.conf
```


Make sure "fglrx" is set for the Driver in the Section "Device".

My Xorg now looks like this bellow

```
Section "Extensions"

        Option        "Composite"        "1"     # or "Disable"

EndSection

Section "ServerFlags"

        Option        "AIGLX"            "on"

EndSection
```


11.)  Reboot


12.) let try and run it, in a terminal or alt-f2

```
SKIP_CHECKS=yes compiz
```

(necessary because fglrx is not on Ubuntu's whitelist)

If it works, do this:

mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

and I also learned instead of doing the above edit 

```
sudo nano -w /usr/bin/compiz
```

and add the fglrx in the WHITELIST var i.e.

```
# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
```

---

### Post by Neo4 on 2007-10-24
my god this efects are very slow!
anyone knows how to improve this with the new ati drivers?

---

### Post by rug77 on 2007-10-24
In my log I'm getting ...

```

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will$
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7cdd000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

This is running from a fresh Ubuntu 7.10 RC CD.  I have not yet downloaded the updates via the package manager ...

Anyone know what is going wrong ?  It looked pretty good up to that point :(

Rug

---

### Post by drprofessor on 2007-10-24
Just tried the new driver on my 9600XT AIW, worked with compiz first try.  Good job amd/ati!

---

### Post by daradib on 2007-10-24
```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

Anyone that has had that error, try the following.
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```

---

### Post by APGunner on 2007-10-24
Well i got it to work thanks to this thread. Like everyone else I have poor performance. I get 9000 fps in glxgears. Firefox scrolling is choppy though and effects are slow sometimes. I only get slow performance when I have desktop effects enabled.

---

### Post by petepan on 2007-10-24
any official news on why it's so buggy? there is nothing in the [http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1) phoronix article about any errors like these. .:(

---

### Post by zasf on 2007-10-24
> **APGunner said:**
> Well i got it to work thanks to this thread. Like everyone else I have poor performance. I get 9000 fps in glxgears. Firefox scrolling is choppy though and effects are slow sometimes. I only get slow performance when I have desktop effects enabled.

compiz is not usable with the new driver, it is sooooo slow. I was waiting the new release just for aiglx and I must say that I'm really disappointed.

Matteo

PS: compiz with radeon 6.7.194 is much faster

---

### Post by APGunner on 2007-10-24
Ya i have a X800GTO if anyone wants to know. I am really disappointed in ati. I thought this driver was gonna be the one. The article made it sound so good. My next video card is going to be nvidia. ATI just sucks.

---

### Post by Rogers on 2007-10-24
I just wrote an **UPDATED** guide on what I did to get this driver 8.42.3 driver working!   Please leave my a reply on how it works for you.

[http://runithard.com/]("http://runithard.com/")

:guitar::KS

---

### Post by AncientPC on 2007-10-24
I have an ATI x1950 and had video problems with both stable and newest drivers.  With 8.37.6 there were color issues (blue = green, etc.).  Although now the colors are correct there's a LOT of flickering (I'd guess once per frame).  Do I need to enable something out of the ordinary to prevent this?

---

### Post by ericderace on 2007-10-24
I've just installed the driver.

I'm on a Thinkpad T60, with an ATI X1400 512mb.  AIGLX works, compiz, Pro/ENGINEER..  But the driver only detects 128mb and not 512mb.  Does anyone have the same problem ?

---

### Post by KLineD on 2007-10-24
I finally installed the new driver, and I'm also experiencing very poor performance with Compiz. Also, the window decorations are somewhat screwed, the border is supposed to be translucent and whenever I move the window it turns red. This is with Compiz under KDE.

I tried also with KWin Composite, also poor performance.

---

### Post by MaximB on 2007-10-24
I give up
One time it worked and then I made the mistake of completing the installation with those 2 commands :
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

They ruined everything !

I've tried to repeat it but to no avail
I can only use the older drivers from the ubuntu restricted drivers.

PLEASE can you update the Ubuntu restricted drivers, it's the only way I can get it to work on this version of Ubuntu.

---

### Post by Melcar on 2007-10-24
> **Rogers said:**
> I just wrote an **UPDATED** guide on what I did to get this driver 8.42.3 driver working!   Please leave my a reply on how it works for you.

[http://runithard.com/]("http://runithard.com/")

:guitar::KS

Did not work for me, and the DRI section that you said to add to xorg.conf killed my xserver.  
For me the driver compiles with no errors, but it never loads.  I must be missing something at the end.

---

### Post by seanf on 2007-10-24
Got it working (on Mobility Radeon 9600) by..

1. Backing up my xorg.conf

2. Following method 2 at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

3. Commenting out the Composite stuff in xorg.conf

4. Enabling fglrx in restricted driver manager.

5. Making the compiz configuration tweaks to whitelist fglrx as described in the top of [this thread]("http://ubuntuforums.org/showthread.php?t=588605").

Overall, I'm not impressed. The only benefit I got was the Google Earth ran smoothly, as long as I had compiz turned off. Compiz didn't work as well as it did with the open-source driver. Definitely not worth the trouble.

Rolled back to the open-source driver by...

1. Disabling fglrx in restricted drivers manager (this uninstalled the driver).

2. Switched back to the open-source driver using Screens & Graphics in system prefs.

3. Rebooted - was stuck in 640x480 after rebooting.

4. Put my old xorg.conf back into place and rebooted again, everything back to normal.

When AMD can put out a driver that doesn't require a 10+ page forum thread with all of these hit-and-miss tweaks, I might try it again. Until then, I'm sticking with what works.

---

### Post by pjomega on 2007-10-24
Building the gutsy packages with the ati-... binary and installing with dpkg worked just fine on my upgraded feisty installation, following the instructions linked several times in this thread,

However, the fglrx module refused to load.
Finally fixed that. 

For all those who continue to see MESA driver loaded instead, check two files: 
1) /etc/default/linux-restricted-modules-common
2) /etc/modprobe.d/blacklist-restricted

If you installed the built packages with the xorg-driver-fglrx, etc., these are just the new versions of the restricted driver files. They should not be blacklisted. Remove or comment fglrx from these files. Then you can insmod/modprobe the fglrx driver and restart the window server to use it immediately or just reboot, which is probably easier.

Compiz now works as well, although not without bugs. Also bear in mind when whitelisting fglrx that the compiz config file in gutsy is /etc/xdg/compiz/compiz-manager.

Cheers.

---

### Post by Melcar on 2007-10-24
Got it to work finally.  Followed the [wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").  I made sure to change any "ati" reference to "fglrx" and add the lines

Section "Extensions"
	Option		"Composite"	"1"
EndSection

Section "ServerFlags"
	Option		"AIGLX"		"on"
EndSection


After I did all that I enabled the ATI driver on the Restricted Driver Manager and rebooted.  No major issues whatsoever and performance (in benchmarks at least) seemed to go up.  I ran [ozone3d]("http://downloads.guru3d.com/download.php?det=1717") and was surprised at the results.  My score is more than double what it was with the 8.38 driver. 
0y only problem is that the desktop effects do not want to turn one for some reason.

---

### Post by Rogers on 2007-10-24
> **Melcar said:**
> Did not work for me, and the DRI section that you said to add to xorg.conf killed my xserver.  
For me the driver compiles with no errors, but it never loads.  I must be missing something at the end.

My guide says to add the DRI section if NOT present.  You probably already had it in the file.

---

### Post by Melcar on 2007-10-24
> **Rogers said:**
> My guide says to add the DRI section if NOT present.  You probably already had it in the file.

It wasn't there so I added it.  
I pretty much ended up following the same steps as you outlined with the only difference that this time I omitted the DRI section and enabled the driver in the Restricted Driver Manager.

---

### Post by jody.palmer on 2007-10-24
Darn...It doesn't support the Mobility Radeon HD 2400.  Does anybody know if ATI posts their planned support schedule anywhere?  It would be nice to know when/if they intend to support my card - just so I know when to check back.

---

### Post by timstl on 2007-10-24
Followed the steps in this whole thread. No errors, everything seemed to go fine. I'm getting a bit frustrated at this point...

Everything is moving very slowly. I get the white screen on startup, and then to even read a webpage is nearly impossible. 

If I type "fglrxinfo" at the prompt it boots me out and restarts x. I can SSH in and type it, though. Not long ago it was listing the ATI driver. Now after a couple reboots it is back to saying MESA. Not sure what I messed up there -- I double checked the files from a few posts up and they look fine.

Here's my xorg.conf:

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
        Load  "dbe"
        Load  "v4l"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"

        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24

        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "1"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "on"
EndSection

---

### Post by Melcar on 2007-10-24
Finally was able to get the desktop effects going, and yes, it's slow, slower than with XGL.  Further driver upgrades should hopefully fix this.  I'm also noticing a slight slow down when scrolling webpages, but that was somewhat fixed by disabling AA and AF in the CCC (it's still a bit slow thought).  Also, a slight image tear is noticeable while scrolling.  There is also the issue of no video playback while Compiz is on.

---

### Post by kshane on 2007-10-24
> **jody.palmer said:**
> Darn...It doesn't support the Mobility Radeon HD 2400.  Does anybody know if ATI posts their planned support schedule anywhere?  It would be nice to know when/if they intend to support my card - just so I know when to check back.

The 8.41 driver is supposed to support the HD cards...  It doesn't do squat for the other ATI cards...

Kevin

---

### Post by CarmeloV on 2007-10-25
> **tatrefthekiller said:**
> 8.4.3 is a very old driver...
This IS an official driver from ATI. Maybe the latest version is just not linked yet.
Simply a error in typing.
I refer to 8.42.3

At this official page of ATI:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

For my card, radeon 9600,I see only 8.40.4, then i think the 8.42.3 is not a official driver.

The users speak of other previous drivers (8.41), then i think: is possible this driver is not for my card, and in ATI pages  i found:8.41.7 for HD 2900, previous version of the driver.

I not found a card associated to 8.42.3.:confused:

Bye
Carmelo Viavattene

---

### Post by aoanla on 2007-10-25
> **CarmeloV said:**
> Simply a error in typing.
I refer to 8.42.3

At this official page of ATI:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

For my card, radeon 9600,I see only 8.40.4, then i think the 8.42.3 is not a official driver.

The users speak of other previous drivers (8.41), then i think: is possible this driver is not for my card, and in ATI pages  i found:8.41.7 for HD 2900, previous version of the driver.

I not found a card associated to 8.42.3.:confused:

Bye
Carmelo Viavattene

Did you bother reading the article I linked you to?

The 8.42.3 driver, like the 8.41.7 driver, doesn't support all of the cards that the 8.40.4 driver did (to be precise, the 8.41.7 release was official for HD series cards only, and the 8.42.3 release is official for everything but FireGL), and hence they're not linked to on the main driver page for simplicity's sake.
As the 8.42.3 driver is hosted on the ati site (the download link on the first page of this thread is from ati) and the guys at Phoronix are allowed to talk about it (they signed an NDA which prevents them from talking about drivers until they are officially released), this actually is an official release.
I'm sorry that this confuses you, but it's par for the course for ATI.

---

### Post by eldragon on 2007-10-25
ahhhh sweet jesus......AIGLX works.....but still buggy, scrolling, video playback not working correctly either, etcetera.
i dont know if its compiz or ati's fault.

on the other hand... 2d desktop is MUCH faster.
3d gaming is MUCH faster too (now i can play ETQW on this crappy card).

once the issues with aiglx + compiz are solved, im willing to use it :)

this type of commitment from ati makes me believe in ati once more.

btw, im on a x600 128mb

---

### Post by jctweb on 2007-10-25
> **aoanla said:**
> Did you bother reading the article I linked you to?

The 8.42.3 driver, like the 8.41.7 driver, doesn't support all of the cards that the 8.40.4 driver did (to be precise, the 8.41.7 release was official for HD series cards only, and the 8.42.3 release is official for everything but FireGL), and hence they're not linked to on the main driver page for simplicity's sake.
As the 8.42.3 driver is hosted on the ati site (the download link on the first page of this thread is from ati) and the guys at Phoronix are allowed to talk about it (they signed an NDA which prevents them from talking about drivers until they are officially released), this actually is an official release.
I'm sorry that this confuses you, but it's par for the course for ATI.

Here's the official ATI page:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3.html)

---

### Post by BernardB on 2007-10-25
Despite the statements in the release notes I'm still able to reproduce corruption with Compiz.
Regardless, Cairo Clock doesn't work (looks like a white square) while Compiz and AWN seem to function well - is this a known problem or have I probably forgotten something like a Xorg module (and do I need glitz)?

---

### Post by jctweb on 2007-10-25
> **BernardB said:**
> Despite the statements in the release notes I'm still able to reproduce corruption with Compiz.
Regardless, Cairo Clock doesn't work (looks like a white square) while Compiz and AWN seem to function well - is this a known problem or have I probably forgotten something like a Xorg module (and do I need glitz)?

If you're using the new 8.42.3 driver, you should not have glitz installed - that's part of XGL.  You'll want to remove it since the new driver supports AIGLX.
```

sudo apt-get remove xserver-xgl

```

---

### Post by gillis on 2007-10-25
Everyone with whitescreens. make sure you enable the driver in system -> preferences -> drivers. It took me 1 day to found out.

i installed my driver on a hp nc8000 with a 64mb mobility 9600 radeon.
google earth runs smoothly, but when i try to enable compiz i see nothing more than glitched windows. background is black. menu's are distorted and fonts are gone.  funny thing is that i see wobblin windows. So compiz did start, its only unusable for me. 

more people with these problems?

---

### Post by bartoz on 2007-10-25
> **hoa3r said:**
> I had the same issues with the slow performance with scrolling and moving windows, when desktop effects is turn off.

When I turn on the desktop effects the performance is much better. Scrolling and moving windows is much faster.

Performance in video and games are still very bad.

I have already remove the new driver and turn back to 8.37 from repository, that has good performance and is stable.

Hope next release will be soon with better performance.

How did you remove the new driver?

---

### Post by jeffmills on 2007-10-25
> **jctweb said:**
> Here's the official ATI page:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3.html)

Interesting:

**Caution:**	The ATI Catalyst™ Linux software suite 8.42.3 will be the final software suite that supports Linux kernel 2.4 and XFree86 version 4.3

---

### Post by F-3582 on 2007-10-25
Is there anyone out there who still uses RHEL 3, but updates his drivers regularly? And plays Enemy Territory?

Probably not ;)

---

### Post by BernardB on 2007-10-25
> **jctweb said:**
> If you're using the new 8.42.3 driver, you should not have glitz installed - that's part of XGL.  You'll want to remove it since the new driver supports AIGLX.
```

sudo apt-get remove xserver-xgl

```
I don't have Xgl installed - this is a fresh install.

Google Earth also refuses to run - it states the following:
> ./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
fglrx first had a similar problem, so I created the following symlink to fix it:
> sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
This works fine with fglrx but not with Google Earth and perhaps Cairo Clock - why not?

---

### Post by aggiemarine07 on 2007-10-25
Yeah settings the Composite to "1" increased my performance by a small amount than just by having it commented out.

---

### Post by jody.palmer on 2007-10-25
Thanks.  Initially I was wary because my card wasn't on the Mobility support list for 8.41.7, The release mentioned supporting Radeon HD 2400 Series, but not the Mobility Radeon HD 2400 specifically.  Still, I installed it and everything went well - it found my card.  Thanks again.

---

### Post by ZTiger on 2007-10-25
Well I have it working now. I started all over again and used they guide here [install 8.42.3 on RS482 [ ATI Radeon Xpress 200] on a fresh install Ubuntu 7.10 Gutsy ]("http://ubuntuforums.org/showthread.php?t=591066").

It isn't much different from the guide I listed in my previous post. So I'm not entirely sure what I did differently. It is either the part about 

Step 11.
```

sudo depmod -a
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

```

OR the fact that I ran the new .run file from ATI without the --buildpkg option first. Either way it is currently working for 3D acceleration and i'm happy. I might play with getting compiz to work tomorrow.

---

### Post by F-3582 on 2007-10-25
Expect to be disappointed by its compositing performance, though. I like the open driver much better in this aspect. Say, has anyone tried MAME with the new driver, yet? Do we still need to run it in software mode?

---

### Post by myname on 2007-10-25
> **raist78 said:**
> The same guide worked for me and i got my ATI Radeon x1950pro AGP finally working. As far as i can see,the only glitch is that compiz fusion is a bit slow.

The guide did not work for me, on a fresh install of Gutsy, kept giving me the mesa driver.  I did my fresh install today.

I followed that guide yesterday in a Feisty install, and all worked fine.

However, I did get the 8.42 drivers installed via that guide only after I installed Envy and installed the ATI drivers with Envy.  Any ideas why?

I still can't get Compiz working in Gutsy, yet in Feisty, it fired right up.

--kevin

---

### Post by renegadesx on 2007-10-25
2 questions: 

1) Does Ubuntu have any plans to include this driver into the Gutsy repos? 

2) Do these drivers support X1550? I bought one because this PC is going to my old man and since good open 3D drivers are apparently on there way, I got one so my old man wont get any driver hell.

I installed the X1550 (replacing an old GeForce FX5200) at the same time I installed gutsy

It will allow 1680x1050 fine but not 1440x900, XGL is choppy with either 8.42 or 8.41 drivers and it and my card after specifying fglrx driver, goes back to vesa after restarting X

---

### Post by daradib on 2007-10-25
> **renegadesx said:**
> 2 questions: 

1) Does Ubuntu have any plans to include this driver into the Gutsy repos? 

2) Do these drivers support X1550? I bought one because this PC is going to my old man and since good open 3D drivers are apparently on there way, I got one so my old man wont get any driver hell.

I installed the X1550 (replacing an old GeForce FX5200) at the same time I installed gutsy

It will allow 1680x1050 fine but not 1440x900, XGL is choppy with either 8.42 or 8.41 drivers and it and my card after specifying fglrx driver, goes back to vesa after restarting X

See [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3.html)

At the top, it says,
> AMD recommends that this release of the AMD Proprietary Linux software driver not be used for distribution packages. Distributors should continue to use the AMD Proprietary Linux driver version 8.40.4 
So then Ubuntu might not include it.

Oddly, however, your card is not in the list of supported products. While the X1600 series and X1300 series are listed as supported ([there no card other than X1550 between them]("http://ati.amd.com/products/home-office.html")), the X1550 series is not listed.

---

### Post by robitor on 2007-10-25
Does anyone know how to fix the lag/firefox issue?!?

---

### Post by daradib on 2007-10-25
> **robitor said:**
> Does anyone know how to fix the lag/firefox issue?!?

If you haven't already, you could try disable anti-aliasing and anisotropic filtering in the Catalyst Control Center. That did it for me.

---

### Post by renegadesx on 2007-10-26
> **daradib said:**
> Oddly, however, your card is not in the list of supported products. While the X1600 series and X1300 series are listed as supported ([there no card other than X1550 between them]("http://ati.amd.com/products/home-office.html")), the X1550 series is not listed.

Thats what I was afraid of. Maybe I should consult ATi about it

---

### Post by myname on 2007-10-26
Hmm, I finally got compiz working on my ATI x1600, however, whenever I play a video in Totem, the video flickers, and if I open another window, doesn't matter what, the video is always on top, even though Totem is behind the other window (firefox in this example).

It appears to be an overlay issue. The same flickering happens when I open up UT2004.

Anyone know how to fix this, or if it's fixable?

--K

---

### Post by daradib on 2007-10-26
> **myname said:**
> Hmm, I finally got compiz working on my ATI x1600, however, whenever I play a video in Totem, the video flickers, and if I open another window, doesn't matter what, the video is always on top, even though Totem is behind the other window (firefox in this example).

It appears to be an overlay issue. The same flickering happens when I open up UT2004.

Anyone know how to fix this, or if it's fixable?

--K

Edit /etc/X11/xorg.conf

It should be something like this:
```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

EndSection

[B]Section "Module"
	Load  "bitmap"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection[/B]

[B]Section "ServerFlags"
	Option	"AIGLX" "On"
	Option	"TexturedVideo" "True"
EndSection[/B]

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "VP920 Series"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
[B]	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"[/B]
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor    "VP920 Series"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
EndSection

[B]Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection[/B]
```

Make sure you have the bold parts.

---

### Post by daradib on 2007-10-26
If the above didn't work and fglrxinfo outputs the correct information (NOT Mesa), then it may be a bug in the ATI fglrx driver. Check out bugs at [ATI Bugzilla]("http://ati.cchtml.com/"), such as Bug [248]("http://ati.cchtml.com/show_bug.cgi?id=248").

---

### Post by michael37 on 2007-10-26
Wow, it sounds like 8.42 driver is incredibly buggy.  Would the original poster please edit the first post and update the information that this driver is buggy and highly experimental?  Last thing that we need on this forum is hordes of beginner users not familiar with Linux installing this driver.

---

### Post by F-3582 on 2007-10-26
> **michael37 said:**
> Wow, it sounds like 8.42 driver is incredibly buggy.  Would the original poster please edit the first post and update the information that this driver is buggy and highly experimental?  Last thing that we need on this forum is hordes of beginner users not familiar with Linux installing this driver.
Why do you call it buggy? Just because it doesn't bring the desired Compiz experience, yet? Or because some people haven't managed to get it working, yet? I have little problems with it and I guess that there are a lot of people who experience the same. To the others, just wait until the driver gets supported by Envy and install them that way.

By the way: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

You can now officially get the driver via the front page.

---

### Post by michael37 on 2007-10-26
> **F-3582 said:**
> Why do you call it buggy? Just because it doesn't bring the desired Compiz experience, yet? Or because some people haven't managed to get it working, yet? I have little problems with it and I guess that there are a lot of people who experience the same. To the others, just wait until the driver gets supported by Envy and install them that way.

By the way: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

You can now officially get the driver via the front page.

How about reports by myname and daradib before?  Does that qualify the driver as buggy?  

Gutsy provides a tested driver version 8.37 of fairly decent quality and performance. It comes packaged in binary for Gutsy, it is easy to install and to manage by Restricted Drivers manager.  It works for absolute majority of Gutsy+ATI users.  So, why encourage updating to a problematic driver unless a specific user has problems with that particular 8.37 driver???

---

### Post by michael37 on 2007-10-26
More reasons to avoid 8.42 driver: Uninstall.

With 8.37 driver, you click on Restricted Manager and uncheck ATI proprietary driver.  Umm.  That's it.

Let's say you installed 8.42 and it doesn't work for you.  How exactly do you uninstall it?  Look around the forums -- more than half of 'Mesa nightmare' issues (when fglrx driver is installed, but fglrxinfo says Mesa Indirect) are due to incorrectly installed or incorrectly uninstalled 8.40 driver.  See why I hate it?

---

### Post by F-3582 on 2007-10-26
So you give the opinion of two people having trouble and bothering to post them here more weight than all those who apparently don't have any?The proper way of confirming the validity of your point would be running a poll, because right now the thing is pretty biased.

EDIT: Ever heard of the rule "Never ever double post"?

---

### Post by daradib on 2007-10-26
Relax.

Depending on different views, the driver may be considered either buggy or not buggy. It is buggy because of the many mentioned problems, but one might not consider it buggy because for the most part, the bugs are due to incorrect installation or other stuff that must be done, and not the driver itself. I believe this was a great driver release (because of its new features and faster FPS), but the installation (and the many bugs when there is a problem in installation) make me hesitant to recommend this driver to everyone unless an easy method of correct installation is found.

Even AMD/ATI states:

> **Caution:** AMD recommends that this release of the AMD Proprietary Linux software driver not be used for distribution packages. Distributors should continue to use the AMD Proprietary Linux driver version 8.40.4

This in the [AMD Proprietary Linux Release Notes]("http://www2.ati.com/drivers/linux/linux_8.42.3.html").

---

### Post by Toadmund on 2007-10-26
I would recommend a new user to not attempt to install this driver IMO.
I installed it, got it working, then it uninstalled itself, will not re-install, I have window remnants painting up my desktop as well.
I occasionally crash to log-in when I click on icons.
This is my second fresh Gutsy install, I see re-install #3 coming REAL soon! 

Most of my problems began with this driver, it's not ready for prime time.

That's my experience, and my opinion.

Perhaps the bugs will be worked out soon?
I hope.

---

### Post by Melcar on 2007-10-26
I don't know about you guys, but these drivers increased performance greatly on both my x1950xt and x200.  Sure, it has some bugs and performance issues, but I only experience them while running Compiz (guessing a crappy AIGLX implementation).  Only thing that really bothers me is that I get a lot of image tearing even if I force vsync on;  I never had this issue before with older driver revisions.

---

### Post by daradib on 2007-10-26
> **Melcar said:**
> I don't know about you guys, but these drivers increased performance greatly on both my x1950xt and x200.  Sure, it has some bugs and performance issues, but I only experience them while running Compiz (guessing a crappy AIGLX implementation).  Only thing that really bothers me is that I get a lot of image tearing even if I force vsync on;  I never had this issue before with older driver revisions.

Maybe its a bug. See this: [Bug 248]("http://ati.cchtml.com/show_bug.cgi?id=248") and [Bug 253]("http://ati.cchtml.com/show_bug.cgi?id=253"). Do those bugs describe your problem? See if switching from an X server session to a virtual console and then back to the X server session helps. This only works for the current X server session, and is not permanent.

---

### Post by myname on 2007-10-26
> **daradib said:**
> Edit /etc/X11/xorg.conf

It should be something like this:
```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

EndSection

[B]Section "Module"
Load  "bitmap"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection[/B]

[B]Section "ServerFlags"
	Option	"AIGLX" "On"
	Option	"TexturedVideo" "True"
EndSection[/B]

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "VP920 Series"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
[B]	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"[/B]
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor    "VP920 Series"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
EndSection

[B]Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection[/B]
```

Make sure you have the bold parts.

Yup, I have that, and I have multiple 'Section "Device"' areas, not sure why, but that still didn't help.  If I disable Compiz, everything is fine.  I don't remember this happening when I installed 8.42 on Feisty.

--Kevin

ps.  Why do I have 2 Section "Device" sections, and how do I get rid of one of them?  does it hurt to have multiple sections?

---

### Post by alex941021 on 2007-10-27
I've been using Linux for a while now and it seems that ATI has never relased a decent driver.  How hard can that be!  I am seriously starting to think that this could be on purpose, not with ATI's knowledge.  Think about it, if you were a large software company (i don't want to name anyone but if you are smart you can come up with at least one name) that is competing with Linux what would you do?  You cannot sabotage the work of thousands of open source developers, but you can do a great deal of damage if you affect core/ and close components like video drivers.  With a bad video driver the system becomes pretty much unusable.  How would you do that?  you can corrupt, bribe developers that are building such drivers...making sure that they never release a good product.  These developers are smart, and I don't believe that this is happening by chance.

I really really hope that I am wrong, otherwise it would be extremely sad and difficult to deal with a situation like that.

---

### Post by michael37 on 2007-10-27
> **daradib said:**
> Relax.

Depending on different views, the driver may be considered either buggy or not buggy. It is buggy because of the many mentioned problems, but one might not consider it buggy because for the most part, the bugs are due to incorrect installation or other stuff that must be done, and not the driver itself. I believe this was a great driver release (because of its new features and faster FPS), but the installation (and the many bugs when there is a problem in installation) make me hesitant to recommend this driver to everyone unless an easy method of correct installation is found.

Even AMD/ATI states:



This in the [AMD Proprietary Linux Release Notes]("http://www2.ati.com/drivers/linux/linux_8.42.3.html").

Thank you.  You have voiced the same sentiment that I felt when helping out users who are in 'Mesa hell' because of install and/or uninstall issues with the driver.

@Melcar:  I have ATI Mobility X1400 and I am very pleased with 3D performance, esp with Compiz performance.

@F-3582: When running a poll, you need to assume that most voters have had experience installing or uninstalling the driver, so it's quite pointless to make a poll asking about the intent to install this driver.

P.S. For those who don't know, 'Mesa hell' is best described by these few lines from Xorg.0.log due to mismatch between the kernel and Xorg drivers.  It's painfully hard to fix.  The snippet below is after the failed uninstall and attempted re-enabling of xorg-driver-fglrx.deb driver.

```

desktop-linux:~$ grep -C 8 'Kernel Module' /var/log/Xorg.*log
/var/log/Xorg.0.log-drmGetBusid returned ''
/var/log/Xorg.0.log-(II) fglrx(0): [drm] DRM interface version 1.0
/var/log/Xorg.0.log-(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
/var/log/Xorg.0.log-(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
/var/log/Xorg.0.log-(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7c3b000
/var/log/Xorg.0.log-(II) fglrx(0): [drm] framebuffer handle = 0x3000
/var/log/Xorg.0.log-(II) fglrx(0): [drm] added 1 reserved context for kernel
/var/log/Xorg.0.log-(II) fglrx(0): DRIScreenInit done
/var/log/Xorg.0.logII) fglrx(0): Kernel Module Version Information:
/var/log/Xorg.0.log-(II) fglrx(0): Name: fglrx
/var/log/Xorg.0.log-(II) fglrx(0): Version: 8.37.6
/var/log/Xorg.0.log-(II) fglrx(0): Date: May 25 2007
/var/log/Xorg.0.log-(II) fglrx(0): Desc: ATI FireGL DRM kernel module
/var/log/Xorg.0.logWW) fglrx(0): Kernel Module version does *not* match driver.
/var/log/Xorg.0.log-(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
/var/log/Xorg.0.log-(II) fglrx(0): [drm] removed 1 reserved context for kernel
/var/log/Xorg.0.log-(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7c3b000
/var/log/Xorg.0.log-(WW) fglrx(0): ***********************************************
/var/log/Xorg.0.log-(WW) fglrx(0): * DRI initialization failed! *
/var/log/Xorg.0.log-(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
/var/log/Xorg.0.log-(WW) fglrx(0): * 2D acceleraton available (MMIO) *
/var/log/Xorg.0.log-(WW) fglrx(0): * no 3D acceleration available *

```

---

### Post by mwolfe on 2007-10-27
> I would recommend a new user to not attempt to install this driver IMO.
I installed it, got it working, then it uninstalled itself, will not re-install, I have window remnants painting up my desktop as well.
I occasionally crash to log-in when I click on icons.
This is my second fresh Gutsy install, I see re-install #3 coming REAL soon!

Most of my problems began with this driver, it's not ready for prime time.

That's my experience, and my opinion.

Perhaps the bugs will be worked out soon?

I agree completely. I have these two black bars at the bottom right hand of my screen, i'm not sure how or why but everytime i boot up i get them and they are bugging the hell out of me. This driver definitely has bugs. I'd highly recommend people wait for the next release at least. I can't believe this one made it past beta testing. It looks more like an alpha than a beta to me. I disabled compiz and it still works like ish. Possibly i need to go in and disable composite and it will work like a normal driver. 

Gutsy has been great for me except video.. The ati driver they chose to use (restricted version) doesnt work on my system with a DVI output from my video card, i get no output when i boot up. I remember this problem back with feisty when i was trying to install the latest version (not the repository version) and it had this issue.. Then gutsy goes and uses that version so i install this version and its got issues as welll.. I really feel like buying a damn nvidea card.

---

### Post by dynamethod on 2007-10-27
is it possible to use DRI and XGL at the same time with the 8.42.3 release?

---

### Post by F-3582 on 2007-10-27
> **dynamethod said:**
> is it possible to use DRI and XGL at the same time with the 8.42.3 release?
Ain't possible and never was. If you want DRI working, use AIGLX instead.

---

### Post by michael37 on 2007-10-27
> **dynamethod said:**
> is it possible to use DRI and XGL at the same time with the 8.42.3 release?

Yes, it is possible, and you don't even need 8.42.3 driver.  Gutsy can do that with shipped 8.37.6 driver.   You need to use display :0 instead of display :1 though -- which means it really works only in full screen mode.

```

$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

```

@F-3582 Look, I am not trying to offend you, but you just don't seem to have experience with Xgl.

---

### Post by quadomatic on 2007-10-27
Installation isn't working for me. Here's my output when I'm building the package:

```

aneesh@aneesh-desktop:~/Desktop$ sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.M12192
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.I12281/debian/control.template ]; then \
                cat /tmp/fglrx.I12281/debian/control.template > /tmp/fglrx.I12281/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.I12281/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.I12281/debian/driver.$i > \
              /tmp/fglrx.I12281/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.I12281/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.I12281/debian/10fglrx.template > /tmp/fglrx.I12281/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.I12281/debian/fglrx.default ]; then \
          mv /tmp/fglrx.I12281/debian/fglrx.default /tmp/fglrx.I12281/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.I12281/debian/control.template ]; then \
                cat /tmp/fglrx.I12281/debian/control.template > /tmp/fglrx.I12281/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.I12281/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.I12281/debian/driver.$i > \
              /tmp/fglrx.I12281/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.I12281/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.I12281/debian/10fglrx.template > /tmp/fglrx.I12281/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.I12281/debian/fglrx.default ]; then \
          mv /tmp/fglrx.I12281/debian/fglrx.default /tmp/fglrx.I12281/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.I12281/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.I12281/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.M12192

```

Can someone help?

---

### Post by aoanla on 2007-10-27
> **quadomatic said:**
> Installation isn't working for me. Here's my output when I'm building the package:

```

aneesh@aneesh-desktop:~/Desktop$ sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.M12192
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.I12281/debian/control.template ]; then \
                cat /tmp/fglrx.I12281/debian/control.template > /tmp/fglrx.I12281/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.I12281/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.I12281/debian/driver.$i > \
              /tmp/fglrx.I12281/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.I12281/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.I12281/debian/10fglrx.template > /tmp/fglrx.I12281/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.I12281/debian/fglrx.default ]; then \
          mv /tmp/fglrx.I12281/debian/fglrx.default /tmp/fglrx.I12281/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.I12281/debian/control.template ]; then \
                cat /tmp/fglrx.I12281/debian/control.template > /tmp/fglrx.I12281/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.I12281/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.I12281/debian/driver.$i > \
              /tmp/fglrx.I12281/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.I12281/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.I12281/debian/10fglrx.template > /tmp/fglrx.I12281/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.I12281/debian/fglrx.default ]; then \
          mv /tmp/fglrx.I12281/debian/fglrx.default /tmp/fglrx.I12281/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.I12281/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.I12281/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.M12192

```

Can someone help?

Yes. See my post on the first page of this thread for the way to solve this.

(Basically, ATI failed to include working scripts for 64bit Ubuntu in this release, because they're slack. You need to download the relevant working scripts and replace the existing ones with them.)

---

### Post by quadomatic on 2007-10-27
> **aoanla said:**
> Yes. See my post on the first page of this thread for the way to solve this.

(Basically, ATI failed to include working scripts for 64bit Ubuntu in this release, because they're slack. You need to download the relevant working scripts and replace the existing ones with them.)

Thanks a lot!

I went ahead and put the guide on the cchtml wiki:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#If_installing_on_Ubuntu_x64](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#If_installing_on_Ubuntu_x64)...

---

### Post by F-3582 on 2007-10-27
> **michael37 said:**
> Yes, it is possible, and you don't even need 8.42.3 driver.  Gutsy can do that with shipped 8.37.6 driver.   You need to use display :0 instead of display :1 though -- which means it really works only in full screen mode.

```

$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

```

@F-3582 Look, I am not trying to offend you, but you just don't seem to have experience with Xgl.
Sorry. Didn't know that. I've been using XGL for just a couple of weeks before growing tired with it. You know, opening three windows and making your system unusable in the process is not what I wished for back then ;)

---

### Post by michael37 on 2007-10-27
Let me just continue my "why I hate 8.42.3 driver" bickering.  I'll copy as many complains I can from other threads so people who read this thread stay away from it.

[http://ubuntuforums.org/showpost.php?p=3646152&postcount=11](http://ubuntuforums.org/showpost.php?p=3646152&postcount=11)

and

[http://ubuntuforums.org/showpost.php?p=3647925&postcount=13](http://ubuntuforums.org/showpost.php?p=3647925&postcount=13)

==========================================================

Another link.  

[http://ubuntuforums.org/showpost.php?p=3653754&postcount=139](http://ubuntuforums.org/showpost.php?p=3653754&postcount=139)
Quote: *I made the terrible mistake of attempting to upgrade to fglrx 8.42, which was immensely painful to even compile for 64-bit and once I finally made it, the driver wouldn't load, just reverted to mesa.*

---

### Post by ricosrealm on 2007-10-27
To all of those trying to install the drivers... please save your energy... wait for the next release!  This release still has major performance and stability issues, especially when running Compiz.  I had no problems installing the driver and confirming AIGLX was being used with DRI.  But many performance issues arose and the old drivers are better with XGL.  Many others have confirmed this as well on this and other threads.  Save your time and effort, cross your fingers, and wait for next month's release!

---

### Post by Ber P on 2007-10-28
I've been running 8.42 on Gutsy for two days now, and has reasonable performance (not much better than the open source driver), but it is very unstable. When using applications that are demanding on the graphic card (i.e. google earth), I often crash. It's serious crashes, where I loose signal to the monitor and, everything is dead!
I've also noticed that I can not run google earth and super tux when compiz is active (OpenGL applications? not sure if google earth uses OpenGL). Turning visual effects off, lets me run - bur often just for a short while before I crash.

I didn't install 8.41, but 8.40 on Feisty didn't give me any stability problems. 

I've really been looking forward to this driver. Now I just hope the issuses will be solved quickly:(

By the way, My graphic card is a Radeon 9600

---

### Post by mudenza on 2007-10-28
Anyone tried this on a Mobility Radeon 7500? If it's less stable than the open source radeon driver, its not go for me...

---

### Post by F-3582 on 2007-10-28
The support for your card has ended months ago, sorry.

---

### Post by trishacupra on 2007-10-29
> **alina.bolero said:**
> I did this:

[LIST=1]
[*]executed the install on my HP Pavilion dv8000 with ATI Radeon Xpress 200M
[*]cd; touch .config/xserver-xgl/disable
[*]added composite and aiglx support to my xorg.conf
[/LIST]



Hi,

I have the same card - Xpress 200M (crappy, I know) and I'm having a heck of a time trying to get it to not show mesa in fglrxinfo.

What does this command do?

cd; touch .config/xserver-xgl/disable

---

### Post by Miguel on 2007-10-29
> **trishacupra said:**
> Hi,

I have the same card - Xpress 200M (crappy, I know) and I'm having a heck of a time trying to get it to not show mesa in fglrxinfo.

What does this command do?
```

cd; touch .config/xserver-xgl/disable

```

That command is actually two. This is marked by the semicolon after cd. First it will execute cd and put you at your $HOME, let's say /home/miguel. After that, it will "touch" .config/xserver-xgl/disable. You should really have a look at [http://en.wikipedia.org/wiki/Touch_%28Unix%29](http://en.wikipedia.org/wiki/Touch_%28Unix%29) or at the manpage. In this case, it will probably create an empty ".config/xserver-xgl/disable".

---

### Post by F-3582 on 2007-10-29
Yup, that's what it does. New versions of XGL don't need that separate XSession config anymore and will start automagically unless you tell it to do otherwise.

---

### Post by novaterata on 2007-10-29
Eureka! Eureka! Maybe... I had the white screen of death whether i used the .run or the ubuntu/gutsy build package script thingy and followed all the directons. Then I just gave up and just re-enabled the official restricted driver fglrx and reinstalled xserver-xgl, but it was just so terrible so I disabled both again and when i started x again it worked! with the new driver and aixgl. The white screen seemed to come up whenever MESA was still the opengl implementation but everything else was "working" somehow reinstalling xgl or the restricted manager fglrx set the opengl to the correct setting... i think

---

### Post by stewecar on 2007-10-29
i followed the wiki tutorial for this release and before configuring the driver i rebooted..
but..at the initial splash screen when i type username and passw the system waits a few second and again push me back to the usern/passw screen..:(
could you help me please?
thanks,
stefano

---

### Post by enryfox on 2007-10-29
I'm having big problems with this release: i followed every possible HOWTO but i always end-up with XORG not starting and reverting to failsafe. Unfortunately failsafe overwrite xorg log, so that i don't know hat actually is not working.

i'll wait for next release...

my hw: ibm thinkpad t43p with mobility fireGl v3200 (similart to x600).

bye

---

### Post by kshane on 2007-10-29
> **enryfox said:**
> I'm having big problems with this release: i followed every possible HOWTO but i always end-up with XORG not starting and reverting to failsafe. Unfortunately failsafe overwrite xorg log, so that i don't know hat actually is not working.

i'll wait for next release...

my hw: ibm thinkpad t43p with mobility fireGl v3200 (similart to x600).

bye

Hey, give this install a try.  I was having no end of trouble installing this driver until I happened to find a post here that gave the easiest way to do it, and the ONLY one that worked for me.  The link below is to ATI's site.  Just follow their install directions and it works!

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html)

Like I said, I'm a noob and I have followed about every Wiki and How-to I could find and NOTHING worked until I found this...

Kevin

---

### Post by enryfox on 2007-10-29
> **kshane said:**
> Hey, give this install a try.  I was having no end of trouble installing this driver until I happened to find a post here that gave the easiest way to do it, and the ONLY one that worked for me.  The link below is to ATI's site.  Just follow their install directions and it works!


Uhm, i'm a bit afraid of using the ATI automatic setup on my ubuntu box, i prefer a way where i can keep traces of what is going to be added to the system. I'll think about it. 

Anyway i was having also problem with the kernel module simlink: several HOWTO's create a simlink for fglrx.ko module in the "volatile" directory, but this simlink is deleted at every reboot (i guess it is the restricted driver manager, because the ati proprietary driver is disabled). 

thanks
ciao

---

### Post by NobeyamaGP on 2007-10-29
Installed this driver and all worked fine right away. However, I changed my monitor's refresh rate to 75Hz via CCC and am now getting occasional visual errors that I thought might be linked to my refresh rate since they weren't there at 60Hz. However, whenever I try to change the refresh rate back, either through CCC or the kubuntu control panel, it acts as if it changed the refresh rate, however the screen never blanks out and when I close and reopen CCC it's back at 75Hz so it obviously never changed at all. Has anyone else had this problem?

---

### Post by FLCLFan on 2007-10-29
I have a few questions on this.

Does 8.42 install XGL?

and

When will it be in the backports?

---

### Post by NobeyamaGP on 2007-10-29
> **NobeyamaGP said:**
> Installed this driver and all worked fine right away. However, I changed my monitor's refresh rate to 75Hz via CCC and am now getting occasional visual errors that I thought might be linked to my refresh rate since they weren't there at 60Hz. However, whenever I try to change the refresh rate back, either through CCC or the kubuntu control panel, it acts as if it changed the refresh rate, however the screen never blanks out and when I close and reopen CCC it's back at 75Hz so it obviously never changed at all. Has anyone else had this problem?

Never mind, disabling composite in xorg.conf seemed to do the trick. Now I can set refresh rates again.

---

### Post by myname on 2007-10-30
After reading all the post, trying all the How To's and even using Envy, whenever I installed the ATI 8.42 driver fglrxinfo returned Mesa.

So, after installing Gutsy clean 1 more time, I decided to hack apart a couple how to's and by trial and error, I found one that works for me every time.

After a fresh install of gutsy, and running a Radeon x1600 Pro, I was able to get the ATI drivers working AND get desktop effects.  The only problem I have is the flicker in video streams and games, but I can just disable while I play games.

Here are my steps, if a line wraps to a second line, it is NOT a separate command, but part of the command above it.  Separate commands have a blank line between them.:
> 
download the 8.42 driver from ATI
open up a terminal window, change to directory where you downloaded the driver, then cut and paste the following commands:

sudo apt-get update

sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy

sudo gedit /etc/default/linux-restricted-modules-common

<add fglrx to the list of restricted modules>, save

sudo dpkg -i xorg-driver-fglrx_8.42.3-1*.deb

sudo dpkg -i fglrx-kernel-source_8.42.3-1*.deb

sudo dpkg -i fglrx-amdcccle_8.42.3-1*.deb

sudo apt-get install -f

sudo rm /usr/src/fglrx-kernel*.deb

sudo apt-get -f install

sudo module-assistant prepare,update

sudo module-assistant build,install fglrx -f

sudo depmod -a

sudo rm -f /usr/src/fglrx-kernel*.deb

sudo mkdir /lib/modules/$(uname -r)/volatile

sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

Reboot

sudo aticonfig --initial --force

sudo aticonfig --overlay-type=Xv

Reboot

<I don't know what the following lines do, but they apparently are the key to this whole Mesa Hell thing>

sudo rmmod fglrx

cd /lib/modules/*/misc

sudo insmod fglrx.ko

modprobe fglrx

restart X


Hope this helps some of you that are stuck in mesa hell.

--Kevin

---

### Post by trishacupra on 2007-10-31
I've been in Mesa hell for days now.

When I try this:

**sudo rmmod fglrx**

I get this:

**ERROR: Module fglrx does not exist in /proc/modules**

What does that mean?

And then I've also discovered that the fglrx.ko symlink has disappeared since I rebooted.

Why would that happen?

You have in your instructions to do this:

[B]sudo gedit /etc/default/linux-restricted-modules-common

<add fglrx to the list of restricted modules>, save[/B]

Do I keep it like that forever?

Also, in the Restricted Drivers gui, I have the ATI accelerated graphic driver entry not ticked but there is a green tick next to the checkbox and it says In Use. Is that what it's supposed to be like?

Thanks. I just want to get out of Mesa hell.

By the way, perhaps this part of my Xorg log file would help...

> (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

and...
> 
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection

Does that help any?

---

### Post by kane357 on 2007-10-31
OK im still getting errors but this is the farthese ive gotten yet.

I get this error 
z@z-laptop:/$ restart X
bash: restart: command not found
z@z-laptop:/$ 


And this error
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
This was that second aticonfig command.



# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection



:lolflag:

---

### Post by kane357 on 2007-10-31
WOoo hooo i got it to work.

OK how do i check my cards capabilities and/or enable them.

---

### Post by Original Brownster on 2007-10-31
Hi,
Just for info, I have a radeon 9600 pro, after some initial problems with the install I got it working with 3d acceleration and 3d desktop effects the whole deal, 

The good news, fgl_gears has increased massively for me, from 550 to about 850fps. 

The bad news, it crashes in all 3d games I have, doom3, warzone2100, oolite. normally after a minute of play just a hard lock up and I have to hit the reset button. The other minor problem is i occasionally see grey lines near the mouse pointer that disappear when I move the pointer onto a window. I have tried with and without aiglx and composite but still get the crashes so I guess Ill revert to the stable driver
My /var/log/Xorg.0.log file shows no errors and only a couple of minor warnings that do not relate to dri / opengl so for me it's wait till the next release I think.

---

### Post by Formaldehyde on 2007-10-31
The above fix for the reappearance of the mesa driver is only temporary and the problem will return once you restart your computer. I did manage to get it to go away for good and use the proper ati drivers. It was one of these two things, but I did them both at once so I don't know which one it is and I can't be bothered going back and finding out. These steps assume that you've already installed the ati drivers and are being pestered by the mesa drivers appearing every time you type fglrxinfo.

Open /etc/modules as root user. If you don't know how to do it using dolphin or don't want to, use the following command (ubuntu users use gedit instead of kate)

> sodu kate /etc/modules

make sure that fglrx is NOT listed in the file. I was told to put it in there in a previous post and it doesn't need to be there and for all I know could be causing the problem. I removed it. Now reboot your computer.

If that doesn't work, try the following in a terminal window

> cd /lib/modules/fglrx

sudo sh make_install.sh

Restart your computer.

---

### Post by Formaldehyde on 2007-10-31
> **Original Brownster said:**
> Hi,
Just for info, I have a radeon 9600 pro, after some initial problems with the install I got it working with 3d acceleration and 3d desktop effects the whole deal, 

The good news, fgl_gears has increased massively for me, from 550 to about 850fps. 

The bad news, it crashes in all 3d games I have, doom3, warzone2100, oolite. normally after a minute of play just a hard lock up and I have to hit the reset button. The other minor problem is i occasionally see grey lines near the mouse pointer that disappear when I move the pointer onto a window. I have tried with and without aiglx and composite but still get the crashes so I guess Ill revert to the stable driver
My /var/log/Xorg.0.log file shows no errors and only a couple of minor warnings that do not relate to dri / opengl so for me it's wait till the next release I think.

what driver does fglrxinfo show you're using. I had all my 3D games and google earth crash and when I checked it out it was using that pesky mesa driver.

---

### Post by NobeyamaGP on 2007-10-31
> **NobeyamaGP said:**
> Never mind, disabling composite in xorg.conf seemed to do the trick. Now I can set refresh rates again.

Ok, this worked for a day or so. Now after turning my comp back on this morning I'm stuck at 75Hz and weird video artifacts. They look like little blinking green or yellow pixels. I don't know what I should do now. How can I force it to stay at 60Hz?

---

### Post by kane357 on 2007-10-31
I cant get these commands to work for me

cd /lib/modules/fglrx

sudo sh make_install.sh

---

### Post by cb474 on 2007-11-01
Is 8.42.3 supposed to totally ruin performance with XGL and only support AIGLX? I tried it on my ThinkPad with the X1400 and my fps with glxgears went from around 6900 fps (with 8.34.8--as packaged in Feisty) to about 200 fps (with 8.42.3).

Strangely, I've tried 8.42.3, 8.41.7, 8.40.4, and the Feisty version of 8.34.8 and found I get the best performance on my X1400 with 8.34.8.

---

### Post by daradib on 2007-11-01
> **cb474 said:**
> Is 8.42.3 supposed to totally ruin performance with XGL and only support AIGLX? I tried it on my ThinkPad with the X1400 and my fps with glxgears went from around 6900 fps (with 8.34.8--as packaged in Feisty) to about 200 fps (with 8.42.3).

Strangely, I've tried 8.42.3, 8.41.7, 8.40.4, and the Feisty version of 8.34.8 and found I get the best performance on my X1400 with 8.34.8.

That's strange. Are you running glxgears in an XGL session?

---

### Post by MilaNL on 2007-11-01
> **myname said:**
> After reading all the post, trying all the How To's and even using Envy, whenever I installed the ATI 8.42 driver fglrxinfo returned Mesa.

So, after installing Gutsy clean 1 more time, I decided to hack apart a couple how to's and by trial and error, I found one that works for me every time.

After a fresh install of gutsy, and running a Radeon x1600 Pro, I was able to get the ATI drivers working AND get desktop effects.  The only problem I have is the flicker in video streams and games, but I can just disable while I play games.

Here are my steps, if a line wraps to a second line, it is NOT a separate command, but part of the command above it.  Separate commands have a blank line between them.:


Hope this helps some of you that are stuck in mesa hell.

--Kevin
that worked perfectly! but the only thing is that i have to do the following command ANYtime i boot again:
sudo rmmod fglrx
cd /lib/modules/*/misc
sudo insmod fglrx.ko
modprobe fglrx
otherwise it won't work! does anyone know how to make ubuntu do these lines anytime on startup?

---

### Post by daradib on 2007-11-01
> **MilaNL said:**
> that worked perfectly! but the only thing is that i have to do the following command ANYtime i boot again:
sudo rmmod fglrx
cd /lib/modules/*/misc
sudo insmod fglrx.ko
modprobe fglrx
otherwise it won't work! does anyone know how to make ubuntu do these lines anytime on startup?

Open the restricted driver manager and check the box to use the driver.

---

### Post by daradib on 2007-11-01
Alternatively, you unblacklist the fglrx kernel module (I believe that's what the checking the restricted driver in the restricted driver manager does).

Edit these two files:

```
/etc/default/linux-restricted-modules-common
/etc/modprobe.d/blacklist-restricted
```

Remove fglrx from the files if it is blacklisted.

---

### Post by Formaldehyde on 2007-11-01
> **kane357 said:**
> I cant get these commands to work for me

cd /lib/modules/fglrx

sudo sh make_install.sh

Yeah, I was messing around trying to get my HDTV to work properly and I screwed up my ATI drivers. I've got them reinstalled but I have the mesa problem and this wont work for my now either. I either get a /proc/modules not found error or module is in use.

This has to be the most flaky and fragile driver I've ever seen.

---

### Post by Koziasty on 2007-11-01
I find that there is a much improvement of quality of video using the newest ati drivers as opposed to the radeon/ati driver... But the first one sends temperatures through the roof ;( why is that so?

---

### Post by StuipedandUgly on 2007-11-01
> **aoanla said:**
> 
For me, at least, the installer doesn't work:

bash ./Desktop/ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/feisty

results in:

(lots of bug output) ending in

dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri" "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1

which is interesting, as /usr/X11R6/lib/modules/dri exists, at least.

(Feisty, AMD64 install here.)

Edit: Michael on the Phoronix forums says this is a known issue with Gusty (which is odd, considering I'm on Feisty), and there's a replacement script... check the Phoronix forums, I suspect, if you have the same problem as me.

Edit2: [http://www.michaellarabel.com/downlo...bian-2.tar.bz2](http://www.michaellarabel.com/downlo...bian-2.tar.bz2) is the link for the new package installer scripts.
You'll need to do:

bash atiinstallername --extract some-directory
and Cd to the some-directory you chose
then unpack the above archive into it, replacing the existing packages directory contents

then ./ati-installer.sh 8.42.3 --buildpkg Ubuntu/feisty
ty

I followed your guide but I Still get the same errors?  can someone help me I'm dumb

---

### Post by MilaNL on 2007-11-02
> **daradib said:**
> Open the restricted driver manager and check the box to use the driver.
it is already checked.. Ill try on a fresh install now.

@StuipedantUgly:
try these command in the folder where the (original) installer is:
```

$ sudo mkdir 8.42
$ sudo sh ati-driver-installer-8.42.3-x86.x86_64.run --extract 8.42
$ cd 8.42
$ sudo mkdir -p common/usr/X11R6/lib/modules/dri
$ sudo sh ati-installer.sh 8.42.3 --buildpkg Ubuntu/gutsy 

```
(it's the same as what aoanla says, but now with the exact commands)

---

### Post by Koziasty on 2007-11-02
I found that 
bash atiinstaller --extract some-directory/
then copying the patch files into that directory
and running 

sudo atiinstaller.sh 8.42.3 --install gives you a beautiful GUI window. installing from packages didnt work for me, but this method gave me beautifully working driver.

---

### Post by MilaNL on 2007-11-02
Okay I did a fresh install and now it worked perfectly :D
Thank you Myname (Kevin)

---

### Post by bladerunner6 on 2007-11-02
is there a solution to the flickering bug when compiz is running and you play a video or opengl window

---

### Post by StuipedandUgly on 2007-11-02
MilaNl thanks
but i still get the same message 

:~/8.42# sudo sh ati-installer.sh 8.42.3 --buildpkg Ubuntu/gutsy
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.FU4465/debian/control.template ]; then \
                cat /tmp/fglrx.FU4465/debian/control.template > /tmp/fglrx.FU4465/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.FU4465/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.FU4465/debian/driver.$i > \
              /tmp/fglrx.FU4465/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.FU4465/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.FU4465/debian/10fglrx.template > /tmp/fglrx.FU4465/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.FU4465/debian/fglrx.default ]; then \
          mv /tmp/fglrx.FU4465/debian/fglrx.default /tmp/fglrx.FU4465/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.FU4465/debian/control.template ]; then \
                cat /tmp/fglrx.FU4465/debian/control.template > /tmp/fglrx.FU4465/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.FU4465/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.FU4465/debian/driver.$i > \
              /tmp/fglrx.FU4465/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.FU4465/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.FU4465/debian/10fglrx.template > /tmp/fglrx.FU4465/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.FU4465/debian/fglrx.default ]; then \
          mv /tmp/fglrx.FU4465/debian/fglrx.default /tmp/fglrx.FU4465/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.FU4465/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.FU4465/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1

I mad a /usr/X11R6/lib/modules/dri foldor in the File System and In the root file but i keep getting this message.
Its driving me crazy why do i keep getting this error it seems like iv tried everything i cant get the driver installed for my radeon HD 2600. Why Wont it WORK!!! WHY
please help me

Worst Case scenario can someone point me in the direction of a video card that i can install with no hassle that has tv-out and is half decent $80-140???

---

### Post by aoanla on 2007-11-02
> **StuipedandUgly said:**
> MilaNl thanks
but i still get the same message 

:~/8.42# sudo sh ati-installer.sh 8.42.3 --buildpkg Ubuntu/gutsy
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.FU4465/debian/control.template ]; then \
                cat /tmp/fglrx.FU4465/debian/control.template > /tmp/fglrx.FU4465/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.FU4465/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.FU4465/debian/driver.$i > \
              /tmp/fglrx.FU4465/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.FU4465/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.FU4465/debian/10fglrx.template > /tmp/fglrx.FU4465/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.FU4465/debian/fglrx.default ]; then \
          mv /tmp/fglrx.FU4465/debian/fglrx.default /tmp/fglrx.FU4465/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.FU4465/debian/control.template ]; then \
                cat /tmp/fglrx.FU4465/debian/control.template > /tmp/fglrx.FU4465/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.FU4465/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.FU4465/debian/driver.$i > \
              /tmp/fglrx.FU4465/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.FU4465/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.FU4465/debian/10fglrx.template > /tmp/fglrx.FU4465/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.FU4465/debian/fglrx.default ]; then \
          mv /tmp/fglrx.FU4465/debian/fglrx.default /tmp/fglrx.FU4465/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.FU4465/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.FU4465/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1

I mad a /usr/X11R6/lib/modules/dri foldor in the File System and In the root file but i keep getting this message.
Its driving me crazy why do i keep getting this error it seems like iv tried everything i cant get the driver installed for my radeon HD 2600. Why Wont it WORK!!! WHY
please help me

Worst Case scenario can someone point me in the direction of a video card that i can install with no hassle that has tv-out and is half decent $80-140???

You know the bit of my instructions where I told you to extract the file you download from the link I provided? You need to do that.

---

### Post by aoanla on 2007-11-02
> **Koziasty said:**
> I found that 
bash atiinstaller --extract some-directory/
then copying the patch files into that directory
and running 

sudo atiinstaller.sh 8.42.3 --install gives you a beautiful GUI window. installing from packages didnt work for me, but this method gave me beautifully working driver.

Yes, that should work too. For some reason, using packages works better for some setups (and is more foolproof if things break.)

---

### Post by cb474 on 2007-11-02
> **cb474]Is 8.42.3 supposed to totally ruin performance with XGL and only support AIGLX? I tried it on my ThinkPad with the X1400 and my fps with glxgears went from around 6900 fps (with 8.34.8--as packaged in Feisty) to about 200 fps (with 8.42.3).

Strangely, I've tried 8.42.3, 8.41.7, 8.40.4, and the Feisty version of 8.34.8 and found I get the best performance on my X1400 with 8.34.8.[/QUOTE]

[QUOTE=daradib said:**
> That's strange. Are you running glxgears in an XGL session?

Yes, I ran glxgears in an XGL session with 8.42.3 and got those terrible numbers. It just seemed like it wasn't working well at all.

---

### Post by espenk on 2007-11-03
I'm having a bit problems with this driver as well. The driver itself works, no problems loading and catalyst control center shows everything as normal.
But when I try to run glxgears/fgl_glxgears I get a blank window. Same with playing a video in Totem.

With gxine (Xv - default)
```

~$ gxine -V xv
...
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
...

```

gxine with xshm works, so it's clearly something wrong here.
glxinfo and fglrxinfo shows what it should, and I've set VideoOverlay to "on" in xorg.conf etc.

:confused::confused:

(Using a x1950 - agp)

-- EDIT --

Problem solved. Turned out I forgot to up the AGP Aperture Size in BIOS after replacing my old graphics card. Works like a charm now! Except for choppy response (moving windows etc) when playing video :)

---

### Post by Ber P on 2007-11-05
Ever since I installed this driver, my screen has been completely messed up during the boot sequence. Between Grub and the splash screen, it's just one big mess of dots in different colors. Whenever the splash screen is ready, the screen becomes fine again. Anybody else having this problem??

---

### Post by cb474 on 2007-11-05
I usually have that problem when the fglrx driver is not actually working and my system is just running off of the Vesa dirver. Does the "fglrxinfo" command show that the ATI driver is being used? If so, then I don't know what else would cause the grabbled color dots.

---

### Post by Polygon on 2007-11-05
just posting this here, has anyone solved the problem where like open gl is misconfigured after installing?

i tried to do glxinfo:

mark@Cactus-Fantastico:~$ glxinfo 
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


how do i solve this?


EDIT: you just type in terminal

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

and it works! got compiz and everything.

---

### Post by Evil Wayz on 2007-11-05
My problem is query shows both monitors are connected but will only let me enable one or the other. if i do both i end up in low graphics mode and have to reconfigure. anyone else having this problem with dual screens?

---

### Post by Ber P on 2007-11-06
> **cb474 said:**
> I usually have that problem when the fglrx driver is not actually working and my system is just running off of the Vesa dirver. Does the "fglrxinfo" command show that the ATI driver is being used? If so, then I don't know what else would cause the grabbled color dots.

fglrxinfo shows that fglrx is installed and working. Besides 'minor' bugs like crashes, and opengl issues when running compiz, everything is working well - after the splash screen. 

Only the boot sequence is messed up.

---

### Post by tomsen_san on 2007-11-06
Does someone know when this will show up in the restricted repository? Or does someone know whom to ask? :-) I'm on 7.10.

---

### Post by aoanla on 2007-11-06
> **tomsen_san said:**
> Does someone know when this will show up in the restricted repository? Or does someone know whom to ask? :-) I'm on 7.10.

It almost certainly never will turn up in the restricted repository - this release is less stable than the current occupant of the repository, and doesn't even fix one of the long standing bugs with the newer ATI drivers (failure on returning from suspend on laptops, with certain kernel builds).

This month's release, 8.43.x, might be added, if it is much more stable and fixes some bugs. However, it isn't even released yet (and won't be until at least the 14th, given the usual schedule), so there'll be a while before it gets into a official repository, if it does at all.

---

### Post by tomsen_san on 2007-11-06
Thx aoanla. So my best bet is manual install as described here...

---

### Post by chedabob on 2007-11-06
Does this finally have X1950 pro support or what? I really want to make the jump to Ubuntu, but not until I can actually run it properly.

---

### Post by VipeR_11 on 2007-11-06
Hi, here i am again :(

I didn't have the time to check again the ati site BUT I still cannot use my ATI X1650 Pro 512 card.

I have install the drivers and still cannot even pu the desktop effects on.

Sry I'm really noob in Ubuntu and linux generally!

Do I have to change the drivers ubuntu uses through the graphics manager?

What I have done so far is:

Install ubuntu 7.10 then enable the restricted driver (it's the ATI driver I think ) Then download from the sinaptic manager all tha ati and radeon packages (with relations to each other)
Reboot nad still nothing trying to put another setting to the drivers ubuntu uses from the monito & graphics manager but testing never passes, and still Haven't got any 3D support.

Any suggestion or help??
:(
Thank's


Edit: The drivers from the synaptic manager I download was the 39 version and not 42 but since i can't even make them work I gues I can not make the 42 version  as well. It seems that Does not install them at all or just install them and not using them!!!

---

### Post by nixie21 on 2007-11-06
> **Formaldehyde said:**
> what driver does fglrxinfo show you're using. I had all my 3D games and google earth crash and when I checked it out it was using that pesky mesa driver.


I still do not have my 9600 working fully yet..

Like I posted earlier, I have the latest ATI drivers working, have direct rendering and am mostly fine.  I can not get desktop effects working unless I install xserver-xgl, then compiz works but games will crash X and get me back to login and user switching gets a black screen and a hard computer restart is needed.  I did notice before uninstalling xserver-xgl that is said directrendering = no and some mesa drivers were there, as soon as I uninstalled it I was back to direct rendering = yes and ATI drivers...

Any ideas?

Thanks

nixie21@Main:~$ glxinfo | grep direct && glxinfo | grep glx && glxinfo | grep OpenGL
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
nixie21@Main:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

---

### Post by luis.alves@lafaspot.com on 2007-11-07
just follow the 3d section on this link
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Remove this section from to the /etc/X11/xorg.conf file. The new xorg server enables "Composite" by default.

# Section "Extensions"
#        Option  "Composite" "0"
# EndSection

Compiz does not know about the fglrx driver. You can either skip the checks

mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

or add it to the compiz white list. *Recommended*

sudo gedit /usr/bin/compiz

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

---

### Post by nixie21 on 2007-11-07
> **luis.alves@lafaspot.com said:**
> just follow the 3d section on this link
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Remove this section from to the /etc/X11/xorg.conf file. The new xorg server enables "Composite" by default.

# Section "Extensions"
#        Option  "Composite" "0"
# EndSection

Compiz does not know about the fglrx driver. You can either skip the checks

mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

or add it to the compiz white list. *Recommended*

sudo gedit /usr/bin/compiz

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"


Call me stupid, but this bottom line:

WHITELIST="fglrx nvidia intel ati radeon i810"

I guess I change i810 with 9600 (my card?)

Thanks

---

### Post by macabro22 on 2007-11-07
How is the performance of the new driver and AIGLX compared to the performance of the old drivers with XGL?

---

### Post by Yellow Pasque on 2007-11-07
> Call me stupid, but this bottom line:
WHITELIST="fglrx nvidia intel ati radeon i810"
I guess I change i810 with 9600 (my card?)
No, you want the name of the driver (fglrx) in that string, not the model number of your video card.

---

### Post by Yellow Pasque on 2007-11-07
> **macabro22 said:**
> How is the performance of the new driver and AIGLX compared to the performance of the old drivers with XGL?
It wasn't that great for me. I tried some Desktop effects, but it kept throttling my processor (2.5GHz X2) to full speed and I had to put up with the other bugs in the new driver. Finally, I got tired of it and went back to 8.40.4.  Oh well, maybe next time.

---

### Post by havchr on 2007-11-07
Anyone else noticed a huge memory leak in this driver?
I've been going through some of my own code, and it seems that glClear has a huge memory leak. even the gears app is leaking like crazy..

[IMG]http://img.photobucket.com/albums/v138/vamecum/Screenshot-4.png[/IMG]

---

### Post by VipeR_11 on 2007-11-10
I fed up, I'm not going to use ubuntu utnil I get a n nVidia card next month.

For those there in ATI just make a decent driver for linux guys!!

If you don't want then we are not going to buy your GPU any more, it's soo simple for us!!

---

### Post by seamus7 on 2007-11-10
I would suggest sticking with the version of fglrx in the official repositories. By what I've read, the newest cutting edge drivers are buggy and not worth all the effort. AIGLX isn't worth it if your system is slower and buggier after an upgrade away from XGL.

---

### Post by EpicBuntu on 2007-11-10
OK, I updated to the new AIGLX but I noticed what you guys said: It is muuuuuch slower and buggy. I had experience with XGL and indeed it was much better. HOW do I go back to XGL, now that I have updated to this AIGLX and removed XGL? (I have an ATI XPRESS 200M).

---

### Post by md_lasalle on 2007-11-10
On the same kind of note. I'm also really disappointed with the new drivers

I'm trying to revert  to 8.27.10 but every time I'm finished installing it, and i restart i get :

```

(EE) module ABI major version (0) doesn't match the server's version (1)

```

How to fix that ? I'm stuck with those driver :(

---

### Post by lingenfr on 2007-11-11
Looks like my experience may be similar to others. My only complaint is that (I assume) the driver is giving me some video artifacts. I get a square box in the lower right corner of my monitor with horizontal lines. I get a similar ghost image over my mouse cursor on occasion. Sometimes it corrects itself, sometimes I have to restart X. I will consider reverting to the repository, but right now it is just mildly annoying.

---

### Post by md_lasalle on 2007-11-13
> **lingenfr said:**
> Looks like my experience may be similar to others. My only complaint is that (I assume) the driver is giving me some video artifacts. I get a square box in the lower right corner of my monitor with horizontal lines. I get a similar ghost image over my mouse cursor on occasion. Sometimes it corrects itself, sometimes I have to restart X. I will consider reverting to the repository, but right now it is just mildly annoying.

I'm experiencing the same exact thing.

How would one revert to drivers from the repository ? I don't want to end up with the same error I describe just above.

Thanks

---

### Post by Yellow Pasque on 2007-11-14
The corruption in the lower-right part of the screen is what drove me back to 8.40.4

To go back to the repo drivers:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

I'd also reinstall the repo driver package
```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f
```

If you're using the TV-out, you may need to install the [8.40.4 package](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run). Don't quote me on that though.

---

### Post by Toshick on 2007-11-14
I've rolled back, as shown in previous post, but it became worse. Sim become one big artifact :)

---

### Post by Yellow Pasque on 2007-11-14
> **Toshick said:**
> I've rolled back, as shown in previous post, but it became worse. Sim become one big artifact :)

Hmm, so where are you at now? What driver do you want to go with?
Either way, post your xorg.conf

---

### Post by slash123 on 2007-11-20
After 1 whole day of playing around with system files, I finally have a working version of the 8.42.3 driver and compiz... **Animations and effects are blazingly fast and I see no video artifacts in playing video (at least using vlc).** This is on a Compaq nc6230 - a modest 1.73 GHz Pentium processor and an arguably old ATI Radeon X300 Mobility GPU. This is going to be a long post, so read on...

This is especially for people who had a previously installation of the ATI driver and installed 8.42.3 using the ATI installer (available from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)) and/or used the envy script (available from [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu13_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu13_all.deb)). However, I feel that this could help others with ATI installation problems as well. 

Ensure that compositing is enabled in your xorg.conf (there should be a section at the end that says "composite" and then "enable" or "1"). Also, check that the driver used is "fglrx" and not "ati". Further, check that your etc/rc.local does not have any references to delete fglrx files (a line that includes (uname -r)). If it does, remove these lines. 

**The ATI installer and/or the Envy script should create a folder /lib/modules/fglrx with a file fglrx.2.6.22-14-generic.ko in it. This is the correct module to be loaded... What you have to do is ensure that all references to the fglrx module insertion, point to this one and not any other** (for example, I found mine to be towards /lib/modules/2.6.22-14-generic/volatile/fglrx.ko and /lib/modules/2.6.22-14-generic/misc/fglrx.ko).

To test this method bootup normally, then run these commands in an xterm:
```
lsmod | grep fglrx
```
This should give a response that tells you that fglrx is loaded. If it is, run (ignore if not loaded):
```
sudo rmmod fglrx
```
Then insert the correct module by running:
```
sudo insmod /lib/modules/fglrx/fglrx.2.6.22-14-generic.ko
```
The following command will confirm the insertion:
```
lsmod | grep fglrx
```

Now all you need to do is restart X (ctrl-alt-backspace). Run fglrxinfo to check that your display card has been identified correctly.

To ensure that this is done everytime, you need to ensure the insertion of this module everytime you boot. This may require you to edit your /lib/modules/2.6.22-14-generic/modules.dep file (I found this reference to the wrong module particularly difficult to trace) and alter the line that points to the wrong module (search for fglrx). 

The brute force way of correcting all references is to run a search using Gnome's 'Search for Files' program to find all files in /etc and /lib that include the text "fglrx" and checking that the reference is to the fglrx folder and not the 2.6.22-14-generic folder.

All the best!

PS> Anyone who is really interested in reaching the root of their 8.42.3 problem should start at /var/log/Xorg.0.log. That's the starting point for my trace.

To check out a video of my working installation: [http://technyou.supersized.org/archives/70-Take-a-Peek-into-my-World-Ubuntu-Screencast.html](http://technyou.supersized.org/archives/70-Take-a-Peek-into-my-World-Ubuntu-Screencast.html)

---

### Post by jctweb on 2007-11-20
Very nice :)  thank you

---

### Post by aoanla on 2007-11-20
I should note, incidentally, that it is now known that there is a serious memory leak in the OpenGL code path used by the 8.42.3 driver with newer (R500 and possibly R600) cards. 
If you experience instability, or even system lock-ups, after periods using OpenGL accelerated software with this driver, this is probably the issue.

Downgrading is the only known workaround - hopefully, this will be fixed in 8.43.x

---

### Post by therealknewman on 2007-11-20
Well I've gotten the new driver to install correctly (according to my fglrxinfo output) and I've whitelisted fglrx in compiz settings, and i've enabled aiglx and composite in my xorg.conf file. But when I run compiz all I get is a fuzzy mess. I can see outlines of the windows and if I hit alt+f4 i can see the neat effect as the window closes, the desktop switcher works too but its all fuzzy. Any ideas as to why compiz isnt working right?

---

### Post by biviano1976 on 2007-11-20
I am about to use Alberto Milone's Envy software on a fresh install of 7.10.  I got 3D effects to work last night on my x1650 pro.  I will let you guys know how it goes.

---

### Post by macabro22 on 2007-11-21
This guy claims to have solved the firefox lazy scroll issue:

[http://technyou.supersized.org/archives/70-Take-a-Peek-into-my-World-Ubuntu-Screencast.html#c47](http://technyou.supersized.org/archives/70-Take-a-Peek-into-my-World-Ubuntu-Screencast.html#c47)

---

### Post by Miguel on 2007-11-22
I don't know how many of you have just installed 8.42.3, but 8.43,  also known as Catalyst 7.11 (let's hope windows naming scheme gives us improvements) is out. Get it [here](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Oh, yes! No FireGL support probably means this is still beta quality.

---

### Post by Tarmael on 2007-11-22
I've read it somewhere else in the forum, ATi do NOT formally release beta drivers to the public.

They have their own beta testers that sign specific contracts and stuff like that to make sure they don't release the programs, this is NOT beta quality, it's an actual release because it is listed in the downloads directory.

I can't remember the actual arguments I was reading a while ago on things like this, but I KNOW that they don't release beta drivers to the public for specific reasons.

Cheers.

Bas.

---

### Post by Miguel on 2007-11-22
> **Tarmael said:**
> I've read it somewhere else in the forum, ATi do NOT formally release beta drivers to the public.

They have their own beta testers that sign specific contracts and stuff like that to make sure they don't release the programs, this is NOT beta quality, it's an actual release because it is listed in the downloads directory.

I can't remember the actual arguments I was reading a while ago on things like this, but I KNOW that they don't release beta drivers to the public for specific reasons.

Cheers.

Bas.

Well, what you said is absolutely true from a formal point of view. But if you look at all the traffic lights in the changelog, if you look at the unresolved issues and if you take into account that these drivers are not recommended by ATi to distributors it's hard not to think this is not yet production quality software.

Please remember that the memory leaks are still there, according to a phoronix poster.

---

### Post by Tarmael on 2007-11-22
Oh well yes, of course.

soon after posting my reply, I did realise what you properly mean.

I am right though it's not beta software, but it's also not the most stable.
So it's an official release of not complete software, and some would class that as beta (for personal use more shall explain soon) because it isn't fully developed and there are lots of issues to resolve with those first.

I am happy to see ATi doing monthly updates, it's a great idea.

It's just unfortunate that I haven't been able to get the 8.40.4 (Had it working at one stage) nor the 8.42.3 drivers working.
I'm working on trying the new 8.433 (7.11) working though. (Should take a better look at it next time I'm alone)

So yeah, not officially ATi beta software, but not completely usable, nor completely reliable.

---

### Post by eldragon on 2007-11-22
7.11 will not help at all :(

same issues... i was hoping some improvemente in the aiglx area........

---

