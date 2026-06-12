---
title: "Post the way you got the ATI driver to work"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by tseliot on 2006-07-22
The owners of an ATI card can post here the model (and the identifier) of their card and the tweakings they had to use in order to get ATI's proprietary driver to work. 

All this data can be accessed by other users who will save much time by looking at the solutions available here for their cards.

[B][COLOR="Red"]
What this thread IS NOT:
*a place for requesting support
*a place for asking about Envy 2 (I will make a new page for that)[/COLOR][/B]



Please, follow this form:

1) Post the output of this command:
```
lspci -n | grep 0300
```

2) Post the model of your card (if you do not know its name just post the output of "lspci | grep VGA" )

3) Post the tweakings required to get your card to work.

For example you can say:
"I needed to get to the Section Device of my xorg.conf and add the following option":
```
Option "RenderAccel" "True"
```

Or, if you nothing is needed for your card to work properly you can write:
No tweaking needed.


I will start posting about my card:

1) 0000:01:05.0 0300: 1002:4337

2) 0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

3) No tweaking needed (it works with direct rendering with the driver which comes by default with Ubuntu)

NOTE: it does not work with fglrx

---

### Post by gerbman on 2006-07-22
Card: Radeon 9500 Pro
Guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Tweaks: none needed, even for dual screen

---

### Post by whatever on 2006-07-23
1) 0000:02:00.0 0300: 1002:4e44
2) 0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
3) no special tweaking, just installed fglrx like described at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

note to 2): it's a radeon 9700 nonpro with edited bios to allow software overclocking, which causes it to identify as pro.

---

### Post by scottDkoDer on 2006-07-23
lspci -n | grep 0300
0000:01:00.0 0300: 1002:4150
lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

Tweak: Had to uninstall fglrx and take care when setting the Horizontal and Vertical refresh rates /etc/X11/xorg.conf in device section.  Still get the 
No ctx->FragmentProgram._Current!! WARN_ONCE messages.

---

### Post by whatever on 2006-07-24
> **scottDkoDer said:**
> Still get the 
No ctx->FragmentProgram._Current!! WARN_ONCE messages.
this is a message from the open source r300 dri drivers, not from fglrx...
so i guess you are not using fglrx at all.

---

### Post by lazyd2 on 2006-07-24
1. 0000:04:00.0 0300: 1002:3e50
2. 0000:04:00.0 VGA compatible controller: ATI Technologies Inc RV380 0x3e50 [Radeon X600]
3. Just followed [this]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") guide.(no tweaking)

---

### Post by daniel of sarnia on 2006-07-24
checked the ati driver box in easyubuntu, X850xt.

---

### Post by caryb on 2006-07-24
1) 01:00.0 0300: 1002:4c57
2) 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
3) Worked out of the box but fails with fglrx

---

### Post by Joga5000 on 2006-07-24
1. 0000:01:00.0 0300: 1002:7100
2. [x1800xt] 0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7100  
-I'm not quite sure why it's unknown... but doesn't seem to hurt anything.
3. EasyUbuntu didn't work, so I followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually") (method 2), except I did not blacklist the old fglrx module. Everything works perfectly.

---

### Post by rocketman768 on 2006-07-26
me:~$ lspci -n | grep 0300
0000:01:00.0 0300: 1002:4e48
me:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]

Following the wiki guide posted several times above did not work for me. The old MESA OpenGL kept loading. I uninstalled the xorg-driver-fglrx package, and just used the driver and instructions from ATI. Run the script, don't build a package from it, and edit your xorg.conf properly (or run aticonfig).

---

### Post by matthew on 2006-07-26
[SIZE=2]lspci -n | grep 0300
0000:01:00.0 0300: 1002:4e50

lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

To install the 3D drivers I did this...

Starting with a fresh install I installed the restricted modules for my kernel.

Next I installed xorg-driver-fglrx

Then I did these: [/SIZE] [SIZE=2]
[/SIZE][SIZE=3][SIZE=2]sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Finally, sudo dpkg-reconfigure xserver-xorg, selecting the fglrx driver and setting my monitor resolution how I wanted it

Then I rebooted and that was it.[/SIZE]  
[/SIZE]

---

### Post by evil_elman on 2006-07-26
**-- 1 --**
```
lspci -n | grep 0300
0000:01:00.0 0300: 1002:3150

```

**-- 2 --**
```

lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

```

**-- 3 --**
Install the driver package from Synaptics.
Then run ```
aticonfig --initial --input=/etc/X11/xorg.conf
```
Add the following two lines manually in the xorg.conf file:
```

	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
```
in the 'device' section for the graphics card.

---

### Post by jrjr on 2006-07-28
.

---

### Post by sirclaudio on 2006-07-29
ATI 9500 non pro:
fglrx package from ubuntu, 3D acceleration worked from the start.
The only problem i've had was the resolutions and vertical frequencies, the driver didn't allowed for resolutions above 1024*768@60Hz. Tried the Option "NoDDC" "yes" but it still used the vesa modes. 
A quick look to xorg's log and i saw that the driver was detecting a tv and a second monitor, so i had to put the option "ForceMonitor" "crt1, notv, nocrt2" (after trying many other things). Only with this i could use the full range of my monitor (a Philips 107E).

---

### Post by mayhemt on 2006-07-29
1.
```

root@Bluhills:~# lspci -n | grep 0300
0000:01:00.0 0300: 1002:4e4a


```

2. 
```

root@Bluhills:~# lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT]


```

3. Driver installation as expained in
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
(USing the drivers from ati.com )

4. Latest drivers from ati 8.27.10-x86_64

5. these options for device
```

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e4a
    Screen 0
EndSection


```


6.  IMPORTANT: Finally copying libdri.so to /usr/X11R6/lib/modules/dri
which comes with ati drive .run file, but somehow I didnt see it copied by the build package option...

---

### Post by Dubbayoo on 2006-07-30
I followed this guide:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

1. 
steve@ubu:~$ lspci -n | grep 0300
0000:01:00.0 0300: 1002:514c

2.
steve@ubu:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]


3. didn't have to tweak anything

---

### Post by knives on 2006-08-02
1) 0000:02:00.0 0300: 1002:4153
2) ***Radeon 9550***
3) Followed [this guide]("http://www.ubuntuforums.org/showthread.php?t=204910") and now it appears to work.

Admittedly, it still is listed as an Unknown Ati device 4317 or something but it doesn't appear to be affecting it...:-\"

---

### Post by bluntu on 2006-08-05
I gave up on ATI Radeon 9000 Pro so I went out and purchased "ATI Radeon X1300"

I installed Ubuntu and then without updating anything I restarted the comp and entered Recovery mode and did this:

-----------------------------------------
$ apt-get update
$ apt-get install xorg-driver-fglrx
$ sudo aticonfig --initial
$ sudo shutdown -r now
-----------------------------------------

Someone posted that around here so I decided to try that on my Radeon X1300 and it works. Doing:

$ fglrxinfo

shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)
---------------------------------------------------------------

Keep in mind that this was a FRESH install. Even though it works fine, I however still would like to tweak it so that it can run at its max. Anyone here knows how to tweak ATI card under LINUX?

---

### Post by daone on 2006-08-06
Agh crap, does this mean I have to give up on my Radeon 9000 pro?

I'm going to keep trying because for a awhile longer as this card should work and I don't want to get a different card yet.

The only card I see for a replacement would be a Nvidia 6800 and their not cheap.

---

### Post by jrjr on 2006-08-06
.

---

### Post by bluntu on 2006-08-06
> **daone said:**
> Agh crap, does this mean I have to give up on my Radeon 9000 pro?


I have not heard once that "9000 Pro" can be used under Linux and I also have tried with no success. I still keep my 9000 PRO in case the next Ubuntu release might support it. 

(It would be funny if 9000 PRO works on next release but not X1300)

---

### Post by Carlos Araujo on 2006-08-06
lspci -n | grep 0300

0000:05:00.0 0300: 1002:7249

VGA compatible controller: ATI Technologies Inc: Unknown device 7249
Model: ATI RADEON 1900xt

ATI for me: NO driver install, NO XGL,NO Compiz,NO Acelerated;

NO ATI CARD?

---

### Post by calixtine on 2006-08-06
Radeon R250 Lf [Radeon Mobility 9000 M9]

--1--
```
lspci -n | grep 0300
0000:01:00.0 0300: 1002:4c66 (rev 02)
```

--2--
```
lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
```

--3--
Followed the instructions at [http://www.ubuntuforums.org/showthread.php?t=204910&highlight=%22ati%22](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=%22ati%22)

The module was not loading, dmesg |grep fglrx was giving me this error :

```
[fglrx:firegl_init_module] *ERROR* firegl_stub_register failed
```

I removed the drm module from /etc/modules to fix :-D

---

### Post by Neo Tom Bombadil on 2006-08-06
1)0000:01:00.0 0300: 1002:7142
2)0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 714 2
3)No tweaks
Note: I am x86-64 drapper, so i used the X86-64 installer. Used method 2 in the unoffcial ati linux wiki line for line, with adding Edit DISABLED_MODULES to include fglrx at first, so lastly this is my information.
**@**-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.5946 (8.27.10)
This was a fresh install, worked flawlessly, unlike the first time i tried with the automatic installers left my screen black and had to re-install because i dident follow instructions but im happy now :)

---

### Post by ubuntu_demon on 2006-08-08
1)0000:01:00.0 0300: 1002:5b62
2)0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]
3) 

$sudo apt-get install linux-restricted-modules-$(uname -r)
$sudo apt-get install xorg-driver-fglrx
$sudo dpkg-reconfigure xserver-xorg
$sudo aticonfig --overlay-type=Xv

$ glxgears -printfps
```

17385 frames in 5.0 seconds = 3476.898 FPS
16495 frames in 5.0 seconds = 3298.805 FPS
16257 frames in 5.0 seconds = 3251.281 FPS
16258 frames in 5.0 seconds = 3251.419 FPS
16029 frames in 5.0 seconds = 3205.766 FPS

```

I think I forgot to reboot the machine before I ran this command :

$ fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by Flavian on 2006-08-10
1) 0000:03:00.0 0300: 1002:5653
2) 0000:03:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

3) I went into recovery mode from GRUB. Than I opened up my xorg conf
```

sudo vi /etc/X11/xorg.conf

```
Changed the graphics driver to "VGA" (that was the only one working, VESA didn't work either) and 8 bit.
saved with
:wq!
rebooted
Now XServer loaded to an ugly 320x240@8bit or someting display. There I managed to execute the driver with SU rights.
Anyhow aticonfig didn't work, so I just copied another xorg.conf over mine (if you do that back up your own first)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

Here is the one I used:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
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

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```
Good luck

---

### Post by TFrog on 2006-08-10
1)  0000:01:05.0 0300: 1002:5955

2)  0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

3)  ATI Driver 8.27.10 installed as per ATI doc found here:
 [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html#176980](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html#176980) 

followed by the commands:

aticonfig --initial

then:

aticonfig --resolution=0,1280x800

This setup my Compaq R4125US laptop with the 3D drivers direct from ATI.

---

### Post by quad3d@work on 2006-08-11
[LIST]
[*]0000:01:05.0 0300: 1002:5955
[*]0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
[*]No tweaking involved. [Following method 1]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").[/LIST]Laptop: Compaq Presario V2410US; Turion64 running 32-bit Ubuntu Dapper, 1.5GB RAM. bcm43xx wifi works as well with native driver.

I did tried [method 2]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") and that didn't work. ATI driver installation guide from ATI site doesn't work neither.

Update: Xgl/compiz works quite nicely as well. \\:D/

---

### Post by Angry on 2006-08-20
I have an ATI X700 card:

I had [downloaded the drivers from ATI]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run") and followed the instructions [they provided]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html").

They only thing I had to do manually was to edit the xorg.conf and change the Driver from "ati" to "radeon".

```

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Driver      "radeon" # <-- originally was "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

```

---

### Post by brim4brim on 2006-08-22
1) 0000:01:00.0 0300: 1002:3150
2) 000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

Followed the howto here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Note: on Latitude D810 I needed to use --force when doing sudo aticonfig --initial command in the howto.  I used the manual howto method because my laptop & Linux doesn't work with the Satellite broadband provider we have.

I also have the latest update from Dell which is supposed to allow suppport for the card in Linux which I got ages ago but it never worked with the driver until now.  Has support for cloned display from ATI Control panel

fglrxinfo:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 GENERIC
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by petri on 2006-08-22
1) 0000:01:00.0 0300: 1002:4242
2) 0000:01:00.0 0300: 1002:4242
3) Followed [this]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") guide

Add the following two lines manually in the xorg.conf file:
```
Option "VideoOverlay" "on" 
Option "OpenGLOverlay" "off"
``` in the 'device' section for the graphics card.

TVtime works but not kdetv, it crashes X and logs me out ](*,) 
kdetv did work before

---

### Post by Logic* on 2006-08-24
> **rocketman768 said:**
> me:~$ lspci -n | grep 0300
0000:01:00.0 0300: 1002:4e48
me:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]

Following the wiki guide posted several times above did not work for me. The old MESA OpenGL kept loading. I uninstalled the xorg-driver-fglrx package, and just used the driver and instructions from ATI. Run the script, don't build a package from it, and edit your xorg.conf properly (or run aticonfig).

This worked for me too (same card). Just saying THANKS :D

---

### Post by Riverine on 2006-08-26
1) 0000:01:05.0 0300: 1002:5954

2) 0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

3) The ubuntu supplied driver worked except it somehow screwed up X so that shutdown/restart requests crashed the system.

4) Installing the ATI supplied driver as per instructions at [http://ubuntuforums.org/showthread.php?t=204910]("http://ubuntuforums.org/showthread.php?t=204910") fixed the problem nicely.

The tweaks in those instructions are:
[INDENT]aticonfig --initial [/INDENT]
[INDENT]aticonfig --overlay-type=Xv[/INDENT] 

(The version of the ATI driver downloaded by the forum instructions above is pretty old but it still works.)

---

### Post by Baji on 2006-08-27
```
lspci -n | grep 0300
0000:02:00.0 0300: 1002:4966 (rev 01)
```

```
lspci | grep VGA
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

```

I Followed this guide ([http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually"))

and still ended up with the mesa card in fglrxinfo and choppy glxgears

this is the error dmesg | grep fglrx gave me:

```
[fglrx:firegl_init_module] *ERROR* firegl_stub_register failed
```

the fix was:

remove **radeon** from /etc/modules

(I saw a post who fixed it by removing drm from modules which gave me the ide to check the file out)

---

### Post by drseuk on 2006-09-01
0000:01:00.0 0300: 1002:5964 (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

Make sure that xorg-driver-fglrx is *not* installed (direct rendering will be disabled if it is).

In the Section "Device", Driver "radeon". *No* other options, as something, possibly fbdev causes gross instability (freezes, random reboots).

This seems stable and gives direct rendering so I can experience getting fragged in bzflag the way it is meant to be!

Linux <hostname> 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux (Ubuntu 6.06)

---

### Post by cblanquer on 2006-09-01
lspci -n | grep 0300
    0000:01:00.0 0300: 1002:4e51
lspci | grep VGA
    0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600]

I followed one of the forum threads without any relevant problem.

---

### Post by jubilee33 on 2006-09-02
1)0000:01:00.0 0300: 1002:4c66 (rev 01)
2)0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
3) No tweaking needed (it works with direct rendering with the driver which comes by default with Ubuntu)

---

### Post by gonesolo on 2006-09-03
Ok can't get description from my OS as I'm in work atm
but:

ATi Radeon X1600 (PCIe) (512Mb)

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

Reboot.

Worked first time.

---

### Post by tmadsen on 2006-09-07
```
tmadsen@jenna:~$ lspci -n | grep 0300
0000:01:00.0 0300: 1002:4e45

tmadsen@jenna:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
```

I got it to work!

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

And I figured that since that didn't give me DRI, I'd try out the symlink fix at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1)

```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

Before this symlink thing i got around 233fps with glxgears, now it's

```
tmadsen@jenna:~$ glxgears -printfps
19288 frames in 5.0 seconds = 3857.453 FPS
19220 frames in 5.0 seconds = 3843.876 FPS
19219 frames in 5.0 seconds = 3843.745 FPS
```

Much better \\:D/

---

### Post by lognok on 2006-09-09
1) lspci -n | grep 0300: 0000:01:00.0 0300: 1002:4c66 (rev 02)

2) lspci | grep VGA: 0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

3) followed this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

3.a) replaced quote "/usr/lib/libGL.so.1.2 with libGL.so.1.2 from the previous driver version (8.24.8)"

By the way I'm running Dapper's Included Driver (8.25.18), not the newest one.

Finally got fglrx to work in Dapper :-D

Thank you to this thread and all the people who posted their solutions...THANKS!

---

### Post by Floren on 2006-09-09
1: 0000:01:00.0 0300: 1002:7142
2: 0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7142

3. EasyUbuntu didn't work, so I followed the same method as Joga500 [method]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually") It seems to work fine.

---

### Post by oskarloko on 2006-09-10
Ok, I used [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

```

$ lspci -n | grep 0300
0000:01:00.0 0300: 1002:4153
$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

```

Anyone know how to brenchmark - compare to Windows ?

I'll use AlienArena2007 - I think
[http://red.planetarena.org/](http://red.planetarena.org/)
(show fps with ??? anybody know ?)

---

### Post by metal_ike on 2006-09-13
1. 0000:01:00.0 0300: 1002:5961 (rev 01)
2. 0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
3. Installed the flgrx driver according to [this guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and had to replace the libGL.so.1.2 driver with an older version.  So far seems to work fine.

---

### Post by FyreBrand on 2006-09-16
1. 0000:01:00.0 0300: 1002:5b60

2. Radeon X300 (PCIE)

3. I haven't made any specific tweaks.  I did use the proprietary driver version 8.28.8 and fitzman49's HowTo.

---

### Post by captaindave on 2006-09-20
admin@admin-laptop:~$ lspci -n | grep 0300
0000:01:00.0 0300: 1002:4c4d (rev 64)
admin@admin-laptop:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

Laptop screen runs perfect out of the box

---

### Post by bittergourd on 2006-09-22
1) 0000:01:00.0 0300: 1002:4150
2) 0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
3) fglrx standard installation
note: motherboard asus k8n (nf3 chipset), bios must downgrade to 1006. otherwise only mesa works without DRI.

---

### Post by purple on 2006-09-22
well just to say that i made my ubuntu run a 3d acceleration succesefuly..
the thing is that i did a kernel compiling folowing instructions [HERE](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)..
i used 8.24.8 driver which isnt broken for my ati radeon 9200se..
after succesefuly compiled kernel by these instructions and installing fglrx module at the and of guide together with your new kernel dont forget to run

```
sudo dpkg-reconfigure xserver-xorg
```
and choose refresh of monitor 30-70 and 60-150 and fglrx driver..

and folowing these above by this:

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```


this is my output:
```
purple@dapper:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)
```

```
purple@dapper:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
```

 I hope u'll manage youselfs here..if any questions PM is open 4.. enjoy :P

---

### Post by ermannobonifazi on 2006-09-23
The latest Ubuntu update broke support for my ATI Driver (Radeon SE 9200). I discover this may depend from ATI that drop support for certain card from the lastest ATI Driver. Vefore the workaround I tryed to downgrade the drives using the standard Ubuntu repositories (xorg-fglrx-driver) and so on, but nothing works and I was getting back MESA as driver event if FGLRX was enable in my Xorg.conf.
So, if someone is facing my same problem I fix the issue following this steps:

------

Generating/Installing Ubuntu packages for the 8.28.8 ATI drivers (DO NOT INSTALL driver greater than this!!!) in Ubuntu Dapper Manually


The new fglrx driver (> 8.28.8) supports Radeon 9500+ (older cards will not work!) and the X-series cards up to X1900

A) Blacklist old fglrx module from linux-restricted-modules

As ubuntu's linux-restricted-modules package includes the fglrx module from an old driver version (8.25.18), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

sudo gedit /etc/default/linux-restricted-modules-common
DISABLED_MODULES="fglrx"

B) Installing the new driver

Download the ATI driver installer: ati-driver-installer-8.28.8.run at [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

This guide refers to the 32bit version of the driver. The installation procedure for 64bit should be the same as for 32bit, except the filenames of the created .deb packages will differ slightly and you have to install the ia32-libs package which can be done with apt-get or synaptic.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:

sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)


Create .deb packages:

bash ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper

Install .deb packages:

sudo dpkg -i xorg-driver-fglrx_8.28.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.28.8-1_i386.deb
sudo dpkg -i fglrx-control_8.28.8-1_i386.deb

Remove any old fglrx debs from /usr/src/:

sudo rm /usr/src/fglrx-kernel*.deb

Compile the kernel module:

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

Note: You have to remove any old fglrx debs and recompile the kernel module after each kernel update!

Update the xorg.conf file changing driver from ati to flrx:

sudo gedit /xtc/X11/xorg.conf
change driver from ati to fglrx

or 

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


Reboot:

sudo shutdown -r now

How to confirm that it worked
Type in your terminal 

fglrxinfo

output should be

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON (your card here) Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

---

### Post by Daniel15 on 2006-09-23
I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) (method 2 on that page) to install the drivers (at the time, it was version 8.28.8

1) 0000:01:00.0 0300: 1002:7145
2) ATI Mobility Radeon X1400. lspci reports "ATI Technologies Inc: Unknown device 7145"
3) No tweaking done.

fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ARB_draw_buffers, GL_ATI_draw_buffers,
    GL_ATI_element_array, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_shader_texture_lod, GL_ATI_texture_compression_3dc,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

---

### Post by Vampirlinux on 2006-09-25
Hi all

lspci -n | grep 0300
0000:01:00.0 0300: 1002:5c61 (rev 01)

lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)

How to work. Downloading the official driver:
$ sudo apt-cdrom add
$ sudo aptitude update
$ sudo aptitude module-assistant build-essential
$ sudo aptitude install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
$ chmod +x ati-driver-installer-8.26.18-x86.run
$ ./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
$ sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb
$ sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb
$ sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
$ sudo rm /usr/src/fglrx-kernel*.deb
$ sudo module-assistant prepare
$ sudo module-assistant update
$ sudo module-assistant build fglrx
$ sudo module-assistant install fglrx
$ sudo depmod -a
$ sudo aticonfig --initial
$ sudo aticonfig --overlay-type=Xv

It stoped to work with the update of 2.6.15.26. and restricted driver.
But thanks to tseliot=D> adding this:
deb [http://www.webalice.it/albertomilone/ubuntu/driver/32bit](http://www.webalice.it/albertomilone/ubuntu/driver/32bit) binary/
to sources.list it works fine. Thanks again tseliot

---

### Post by JermCool on 2006-09-28
1) $ lspci -n | grep 0300
0000:01:00.0 0300: 1002:5964 (rev 01)

2) $ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

3) Three tweaks were required.  First, I downloaded the ATI package ($ sudo apt-get install xorg-driver-fglrx).  Second, I edited the /etc/X11/xorg.conf file so that under "Devices" the driver was changed from "ati" to "fglrx".  Finally, an old version libGL.so.1.2 file was copied over the existing (retrieved from [http://www.ground-impact.com/libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2") (Credit to Josh Robinson).

Works a treat now!

---

### Post by jonberling on 2006-09-30
1)
0000:03:00.0 0300: 1002:5e4b

2)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]

I know it says I have a PCIE, but I really have a AGP. Everything works fine though.

3)
I used the same guide as lazyd2. It worked perfectly, no tweaking. You can find it at: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by petri on 2006-09-30
> **petri said:**
> 1) 0000:01:00.0 0300: 1002:4242
2) 0000:01:00.0 0300: 1002:4242
3) Followed [this]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") guide

Add the following two lines manually in the xorg.conf file:
```
Option "VideoOverlay" "on" 
Option "OpenGLOverlay" "off"
``` in the 'device' section for the graphics card.

TVtime works but not kdetv, it crashes X and logs me out ](*,) 
kdetv did work before


Still using same guide and same options as in my [post #31]("http://ubuntuforums.org/showpost.php?p=1409048&postcount=31") but an older driver [version 8.28.8]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27") because the guide uses a current driver today :mrgreen:

---

### Post by zero_koop on 2006-10-04
> **Joga5000 said:**
> 1. 0000:01:00.0 0300: 1002:7100
2. [x1800xt] 0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7100  
-I'm not quite sure why it's unknown... but doesn't seem to hurt anything.
3. EasyUbuntu didn't work, so I followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually") (method 2), except I did not blacklist the old fglrx module. Everything works perfectly.

I also used that site.  I used Method 1 after Easy Ubuntu didn't work.  I have a Radeon 9600.

---

### Post by blitzer on 2006-10-05
1.```
lspci -n | grep 0300

[COLOR="Blue"]0000:01:00.0 0300: 1002:5964 (rev 01)[/COLOR]

```
2.```
lspci | grep VGA

[COLOR="Blue"]0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)[/COLOR]
```

3.```
fglrxinfo

[COLOR="Blue"]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
[/COLOR]
```

MESSAGE FROM ATI:  [URL="https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300"]ATI Proprietary Linux x86 Display Driver
[/URL]
As of [COLOR="Red"]driver version 8.29.6[/COLOR] support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

Users with these products should use [COLOR="Red"]driver version 8.28.8
[/COLOR] 

**[COLOR="Blue"]How I fixed my video card:[/COLOR]**
Used this [site]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1") [COLOR="Red"]applying method 1 step by step[/COLOR] :D 

[COLOR="Red"]This is very important:[/COLOR]
As you follow the steps make sure you do [COLOR="Red"]"Troubleshooting for Method 1"[/COLOR] 

[How to]("https://help.ubuntu.com/community/RootSudo"):  Getting root privliges to copy and or move files ](*,)  (if an easier way please post it)

Enabling the root account
In console
```
sudo passwd root
```
Enter password for root
Confirm password for root
Restart and log in using username:root password: password you made

Disabling the root account
```
sudo passwd -l root
```

[SIZE="5"]Thanks for this thread tseliot and to all who posted [/SIZE];)

---

### Post by epennings on 2006-10-07
```
lspci -n | grep 0300
[COLOR="RoyalBlue"]0000:01:00.0 0300: 1002:4150[/COLOR]
```

```
lspci | grep VGA
[COLOR="RoyalBlue"]0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600][/COLOR]
```

I used the following guide to install the drivers : [link]("http://ubuntuforums.org/showthread.php?t=204910&highlight=xpress")
Just replace [COLOR="RoyalBlue"]ati-driver-installer-8.26.18-x86.run[/COLOR] with [COLOR="RoyalBlue"]ati-driver-installer-8.29.6.run[/COLOR]

I had to modify my xorg.conf to make it work with beryl/xgl (I also noticed a slight performance increase for normal gnome sessions):
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option       "no_accel" "no"
	Option       "no_dri" "no"
	Option       "DynamicClocks" "on"
	Option       "mtrr" "on"
	Option       "DesktopSetup" "Single"
	Option       "ScreenOverlap" "0"
	Option       "Capabilities" "0x00000000"
	Option       "CapabilitiesEx" "0x00000000"
	Option       "VideoOverlay" "on"
	Option       "OpenGLOverlay" "off"
	Option       "CenterMode" "off"
	Option       "PseudoColorVisuals" "off"
	Option       "Stereo" "off"
	Option       "StereoSyncEnable" "1"
	Option       "FSAAEnable" "no"
	Option       "FSAAScale" "1"
	Option       "FSAADisableGamma" "no"
	Option       "FSAACustomizeMSPos" "no"
	Option       "FSAAMSPosX0" "0.000000"
	Option       "FSAAMSPosY0" "0.000000"
	Option       "FSAAMSPosX1" "0.000000"
	Option       "FSAAMSPosY1" "0.000000"
	Option       "FSAAMSPosX2" "0.000000"
	Option       "FSAAMSPosY2" "0.000000"
	Option       "FSAAMSPosX3" "0.000000"
	Option       "FSAAMSPosY3" "0.000000"
	Option       "FSAAMSPosX4" "0.000000"
	Option       "FSAAMSPosY4" "0.000000"
	Option       "FSAAMSPosX5" "0.000000"
	Option       "FSAAMSPosY5" "0.000000"
	Option       "UseFastTLS" "0"
	Option       "BlockSignalsOnLock" "on"
	Option       "UseInternalAGPGART" "no"
	Option       "ForceGenericCPU" "no"
	Option       "KernelModuleParm" "agplock=0"
	Option       "PowerState" "1"
EndSection

Section "Monitor"
	Identifier	"1825"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor		"1825"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by ullivilli on 2006-10-16
1. lspci -n | grep 0300
0000:01:00.0 0300: 1002:4150

2. lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

3. No tweaks at the moment... but i'l try to get my card to show movies on my tv in a way like in windows there is theatre mode. not shure tho is it fully possible in linux.:-k 
[anyone know is theatre mode possible at all??]

Getting it to work was a pain in teh but. 
I followed [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) Method 2. for a shitloads of times ](*,) and still ended up with : 
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1) :confused: 

then finally i tried what about uninstalling everything before installing.
So i started synaptig typed in radeon got rid of everything there what was installed (had to install radeontools back tho because gnome-sessions depend on it).
Again i went through the [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
and voilla i got it to work.

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6065 (8.29.6)

and 

$ glxinfo | grep render
direct rendering: Yes
GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9600 Generic

just bring tears to my eyes :mrgreen:

---

### Post by fummo on 2006-10-18
I used this installer for my 9250 [http://www.ubuntuforums.org/showthread.php?t=235145&highlight=ati]("http://www.ubuntuforums.org/showthread.php?t=235145&highlight=ati"):D :D  I'm a happy bunny now.

---

### Post by stitch on 2006-10-25
lspci -n | grep 0300
01:00.0 0300: 1002:4153

ATI Radeon 9550SE

3D works, but very slow

 fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Tried a lot of test, all of them unsuccessful.

---

### Post by Tranquilo on 2006-11-01
Got it to work by following this:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Installing_Edgy.27s_Included_Driver_.288.28.8.29](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Installing_Edgy.27s_Included_Driver_.288.28.8.29)
No problems. Tried both methods. Both worked.
I have an x1300 Radeon.
This after trying various other howtos and reinstalling several times :)

---

### Post by yusufk on 2006-11-01
> **stitch said:**
> 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".


Hi, I've got the mobility x700, getting the same error message, tried LOTS of guides and methods and not getting anywhere. Next attempt is to remove all generic kernel stuff and replace with 386.

](*,)

---

### Post by mirak63 on 2006-11-02
I fixed my problem with 9600 pro using this page : [http://66.249.93.104/search?q=cache:c80xQyXXpXUJ:www.linuxquestions.org/linux/answers/Hardware/Making_ATI_drivers_work_with_nforce2_and_kernel_2_6_in_Gentoo+gentoo+nforce+2+9600+pro&hl=fr&ct=clnk&cd=3&client=firefox](http://66.249.93.104/search?q=cache:c80xQyXXpXUJ:www.linuxquestions.org/linux/answers/Hardware/Making_ATI_drivers_work_with_nforce2_and_kernel_2_6_in_Gentoo+gentoo+nforce+2+9600+pro&hl=fr&ct=clnk&cd=3&client=firefox)

I filed a bug report with the fix and ask how to integrate that into main [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/69876](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/69876)

Hi,
No matter what I do, the fglrx module doesn't enable DRI and 3d acceleration, or a broken one at least, without rebuilding a kernel and disabling the module ATI Radeon. I did that for Dapper and it worked.

I found this fix on google from a gentoo user :
[http://66.249.93.104/search?q=cache:c80xQyXXpXUJ:www.linuxquestions.org/linux/answers/Hardware/Making_ATI_drivers_work_with_nforce2_and_kernel_2_6_in_Gentoo+gentoo+nforce+2+9600+pro&hl=fr&ct=clnk&cd=3&client=firefox](http://66.249.93.104/search?q=cache:c80xQyXXpXUJ:www.linuxquestions.org/linux/answers/Hardware/Making_ATI_drivers_work_with_nforce2_and_kernel_2_6_in_Gentoo+gentoo+nforce+2+9600+pro&hl=fr&ct=clnk&cd=3&client=firefox)

```
Making your Radeon 9600 PRO work with Nforce2 and kernel 2.6(Gentoo)

I realize there are many guides out there, however none really worked for me. I figured I'd write this so that others may benefit from my long tired hours in front of the screen, leering back at me.

Lets begin:
The first thing you need to do is make sure your kernel is configured correctly. If not, you'll have to recompile over again, however using gentoo this should not be much of a challenge :)

#cd /usr/src/linux
#make menuconfig

Now make sure the following are enabled:

Device drivers>Character devices:
(M)AGP support(agpgart)
(M)nforce2 chipset support
(*)direct rendering manager (drm)
- (*) ATI radeon

but NOT support for ATI radeon!(Strange as it may sound)

If they are continue, if not, recompile your kernel.(If you can't remember how it is done, refer to the excellent installation handbook at gentoo.org)

Now you need to enable the new modules so you'll need to edit your modules autoload:

#nano /etc/modules.autoload.d/kernel-2.6

then write in: (from the top)
agpgart
nvidia-agp
radeon

```

Then you build fglrx with the habitual method.


Using Option "UseInternalAGPGART" "no" should in theory resolve most problems, but for radeon 9600 pro the problem seems somewhere else.

I am not sure this problem only happen when you use nforce2 + radeon 9600 pro, but I found on google a lot of person who had this problem with 9600 pro.

So I am wondering how this bug could be fixed without users having to rebuild a kernel+fglrx modules.
I believe asking to have a special kernel in main is a bit to much :p

---

### Post by Turin Turambar on 2006-11-02
RADEON 9000 PRO

I got DRI working out of the box, with Tungsten/Mesa drivers.
However, although OpenGL (e.g. Planet Penguin racer game) worked, I couldn't start the same program more than once - if I did, the screen would go black and froze the system!

However, thanks to [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) I managed ATI drivers to work. Now everything works like charm!

---

### Post by websurrfr on 2006-11-02
Using Ubuntu 6.10
Card: X1900XT

Method:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Worked like a charm.  Followed it step by step.

---

### Post by huwshimi on 2006-11-02
> **yusufk said:**
> Hi, I've got the mobility x700, getting the same error message, tried LOTS of guides and methods and not getting anywhere. Next attempt is to remove all generic kernel stuff and replace with 386.

](*,)

Have you tried adding the following to the end of your xorg.conf?
> 
Section "Extensions"
        Option  "Composite"     "Disable"
EndSection

It worked for me (X700 pro).

Cheers.

---

### Post by vseehua on 2006-11-03
1. 01:00.0 0300: 1002:5653
2. 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
3. Guide: ATi Binary guide in wiki.ubuntu.com, but need to manually install the Linux Restricted Modules. The standard Ubuntu Edgy install didn't provide that by default (at least for me).

---

### Post by Rocket on 2006-11-05
Opps I pushed the wrong button, see post below

---

### Post by Rocket on 2006-11-05
[B][I]lspci -n|grep 0300 0000:01:00.0 0300: 1002:5960 (rev 01)
 lspci|grep ATI VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)[/I][/B]
Video card is actually labelled Asus 9250 with 128 of ram.
 
After building new box with Sempron 3300+, Asus K8V Motherboard, did a clean install of Dapper from cd, and internet access. The box would crash on boot, when X would attempt to start. I tried to install ATI driver 8.28.8 from command line in safe mode,(later drivers do not support this card) The ATI installer worked in fashion and produced a driver, but it kept locking up on X startup also.
Thoughly fed up with trying various other drivers, I removed the Radeon AGP card and put in an old S3 pci card, after configuring xorg.conf, it worked as it should. I then proceeded to use the 8.28.8 installer to install the ATI driver in graphic mode, all went as it should.
I then removed the old S3 card and replaced the Radeon 9200 pro card, next boot I then configured xorg.conf ie driver fglrx, along with the correct parameters for my display.

Intructions for 28.8.8 driver installer is here [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html")
Driver installer is here[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run")
**There was no way that I could see to bring X up from a clean install with the Radeon 9200 card.**
regards
Rod

---

### Post by Handssolow on 2006-11-05
How I got my ATI Radeon 9600 AGP  card working in a desktop with Asus A7V800 AMD 2.4 Ghz Athlon Mobile 1Gb ram. Last week I had a problem running Edgy from a live CD, I'd just get a blank screen but eventually I managed to get to a command line and changed to “vesa” driver in xorg.conf then go for the full install. I posted on this in a thread about black screen in the install/upgrade section.
To get the video card working I followed lots of advice in this thread and altered xorg.conf countless times but still it wasn't working.
$ glxgears 
was very slow and jerky, giving the error report-
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering

$ fglrxinfo
gave the following error report
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I googled for the first error line from fglrxinfo getting
[https://lg3d.dev.java.net/lg3d-getting-started.html](https://lg3d.dev.java.net/lg3d-getting-started.html) 
Reading this I added at the end xorg.conf
Section "DRI"
	Group "video"
	Mode 0666
EndSection

and it worked. glxgears runs smooth without errors, though I haven't checked the speed yet.
fglrxinfo gives
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)
For other who require the information I've selected parts of my xorg.conf file.
Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dri"
EndSection
Section "ServerFlags"
	Option	    "AIGLX" "off"
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "UseFBDev" "True"
	Option	    "OpenGLOverlay" "off"
EndSection
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
Section "DRI"
	Group "video"
	Mode 0666
EndSection

Any comments, further tests I should run etc?
Why did it have to take so long?
Sorry for long post but I thought it might shed some light.

---

### Post by Anonii on 2006-11-05
Ok I made my ATI 9600 to work! I'll write it here, so that i can remember the procedure the next time :P

Actually, now that I check it out again, I just followed the second method [in this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually"). And it seems like I have added these lines:
```

Section "Extensions"
        Option      "Composite" "0"
EndSection

Section "DRI"
        Mode    0666
EndSection

``` in the end of my xorg.conf

---

### Post by Handssolow on 2006-11-05
Suitably chastened I set off hot foot (hot fingers more like) to follow the guide to install the latest ATI driver and discovered I’d returned to a mesa error.

For those of us who are less interested in what is under the bonnet (hood) all this does seem a bit frustrating and hardly likely to result in a recommendation of Ubuntu to friends.

---

### Post by Handssolow on 2006-11-05
Re my attempt to get ATI 8.30.3 working with my 9600 XT card gives these after what appears to be an error free install from the wiki- 
lsmod shows no fglrx
but etc/modules has fglrx on a new line
modprobe fglrx
FATAL: Error running install command for fglrx

I'be read the bug report, any suggestions? Go back to the earlier ATI driver?

---

### Post by bphunter616 on 2006-11-06
Installed 6.10 from scratch on my IBM T43 with a Westinghouse 19" WFP.  Had no issues with the installatin:

(1) lcpi = 01:00.0 0300: 1002:5460
(2) lcpi |grep VGA = 01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
(3) Just followed this guide with no tweaking: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Very nice 1440x990 display! ;)

---

### Post by edgardz on 2006-11-06
I just installed the ATI drivers 8.30.3 on my Edgy 64-bits with the following method : [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

fglrx seem to work correctly. Here is the fglrxinfo output:
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6119 (8.30.3)

But the problem is that my performance are very bad. I know that glxgears is not a benchmark but 150 fps is very low ! I also notice that my opengl screensaver are very choppy. Anyone have the same problem ?

Thanks !

Edgardz

---

### Post by Melcar on 2006-11-07
> **edgardz said:**
> I just installed the ATI drivers 8.30.3 on my Edgy 64-bits with the following method : [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

fglrx seem to work correctly. Here is the fglrxinfo output:
)

But the problem is that my performance are very bad. I know that glxgears is not a benchmark but 150 fps is very low ! I also notice that my opengl screensaver are very choppy. Anyone have the same problem ?

Thanks !

Edgardz

Same problem here.  Running the new 8.30s with a 200M.  Performance is notably slower than in Dapper.

---

### Post by Buickman on 2006-11-07
With Dapper

0000:01:00.0 0300: 1002:4b49

ATI Technologies Inc R480 [Radeon X850XT]

No tweaking, other than changing driver to fglrx in the xorg.conf.

---

### Post by sebos69 on 2006-11-11
```
lspci -n | grep 0300
01:00.0 0300: 1002:4e50

```

 ```
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```


driver verision : 8.30.3 on edgy. Got it working using the ATI installer, whith this help:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

---

### Post by clever forum name on 2006-11-12
> **sebos69 said:**
> ```
lspci -n | grep 0300
01:00.0 0300: 1002:4e50

```

 ```
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```


driver verision : 8.30.3 on edgy. Got it working using the ATI installer, whith this help:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)


Sebos,
Can you provide more information about the "working" condition in Edgy. I used the same method myself but my performance (FPS) is low compared to Dapper. Your post ould be appreciated. 
_CFN

---

### Post by Fittersman on 2006-11-12
all i did was upgrade to edgy and now mine works (well direct rendering works now)

only thing i havent figured out yet is the tv output thing

---

### Post by sebos69 on 2006-11-12
> **clever forum name said:**
> Sebos,
Can you provide more information about the "working" condition in Edgy. I used the same method myself but my performance (FPS) is low compared to Dapper. Your post ould be appreciated. 
_CFN

Well, my FPS are also weird with glxgears. I got 250fps which is low. But I also have 250 fps when running fullscreen, which somehow means that the bottleneck is maybe somewhere else. On the other hand, 3D apps (google earth, as an example) work fine and as fast as in Dapper (as far as I remember performances with Dapper).

There is only one weird thing about available offscreen space, see this post :
[http://www.ubuntuforums.org/showthread.php?t=296286](http://www.ubuntuforums.org/showthread.php?t=296286)

---

### Post by clever forum name on 2006-11-13
> **sebos69 said:**
> Well, my FPS are also weird with glxgears. I got 250fps which is low. But I also have 250 fps when running fullscreen, which somehow means that the bottleneck is maybe somewhere else. On the other hand, 3D apps (google earth, as an example) work fine and as fast as in Dapper (as far as I remember performances with Dapper).

There is only one weird thing about available offscreen space, see this post :
[http://www.ubuntuforums.org/showthread.php?t=296286](http://www.ubuntuforums.org/showthread.php?t=296286)

Thanks Sebos. Your data points are greatly appreciated. I hope to find a solution at some point. Other apps seem okay, but the performance should be much better. Thanks again for getting back to me.
_CFN

---

### Post by NemesisUK on 2006-11-15
I also get low FPS with glxgears, however with real apps and games performance is fine. UT2004 for example runs as well as it does in windows.
So I'm going to ignore glxgears from now on as it's not a benchmark.

If I recall correctly ATI themselves said to ignore glxgears and to use the games you run to do any testing of driver perf.

---

### Post by clever forum name on 2006-11-15
> **NemesisUK said:**
> I also get low FPS with glxgears, however with real apps and games performance is fine. UT2004 for example runs as well as it does in windows.
So I'm going to ignore glxgears from now on as it's not a benchmark.

If I recall correctly ATI themselves said to ignore glxgears and to use the games you run to do any testing of driver perf.

Thanks for the reply. I should probably just move on, but it irritates me to see trivial problems on my PC. As an example screen-saver is jumpy when it should be smooth. I realize this is not the best example since screen savers require me not to use the PC at all in order to be turned on. I'm not playing to many games or other graphic intensive applications so it may be cosmetic in my case. Once I saw the performance in Dapper, I wanted the same in Edgy. Perhaps the call into the driver has changed/improving efficiency or some other aspect of operation. glxgears may not be making this call, etc. Unknown...
Thanks for posting.
_CFN

---

### Post by Jacen on 2006-11-16
1) 01:00.0 0300: 1002:7145
2) ATI Radeon Mobility X1400
3) This worked perfectly with edgy, after about 2 days of mucking around.

[Ubuntu Edgy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

One thing that I will mention that only applies to Mobility cards if you have them, make sure you get ati-driver-installer-**8.31.5**-x86.x86_64.run or above (there is a link in the guide).

I only mention this because my days of trouble were all from the ignorant ATI site that provided me with an older driver through their "driver selector" which just by chance did not support my X.org version(Edgy). I hope this helps someone because i sure needed this help.

And also while I am ranting, if you are having problems with the mouse locking up randomly on a Core 2 Duo and x86_64 architecture, give up for this kernel, believe me i spent a great deal of time on it and couldnt find any help.

---

### Post by clever forum name on 2006-11-16
Thanks Jacen. I'll try the new ATI driver. I had been trying to get  the 8.30 release up. A glimmer of hope comes in the form of a new driver release. The release notes make no mention of a related fix, but I am hopeful in any case.
_CFN

---

### Post by wolfear on 2006-11-16
00:0e.0 0300: 1002:5157

00:0e.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

No tweaks
I got the "no screens" error for 2 days using every configuration and fix option listed till I moved the card from PCI slot 3 to slot 1.
Fired right up no problem using the driver and config provided in Edgy.

---

### Post by 56phil on 2006-11-19
MOBILITY X700 RADEON on a Gateway M680.
```

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

Added desired screen resolutions to /etc/X11/xorg.conf file.

This got the full screen resolution but now the system hangs on shutdowm. So, I had to replace 'quiet splash' with 'vga=788' in the /boot/grub/menu.lst file. Now, I'm happier.:)

---

### Post by RobNyc on 2006-11-20
SAPPHIRE RADEON X1600 PRO 512MB AGP 

Went to ati.com got the ati-installer since it has a newer version. 

Installed it and followed their instructions simple

---

### Post by kvonb on 2006-11-20
Simple.....

Installed Edgy, and left it standard.  No messing about at all.

ALL my 3d games work (Wolfenstein, ET, SoF, QuakeII, Cedega-BF1942, Cedega-Half-LifeII, Glest), and Beryl was a breeze!

Go opensource!

---

### Post by daradib on 2006-11-23
1) 01:00.0 0300: 1002:554d
2) ATI Radeon X800 PCI-E
3) Had to install xorg-driver-fglrx and fglrx-control (sudo apt-get install xorg-driver-fglrx fglrx control) and configure (sudo aticonfig --initial) followed by (sudo aticonfig --overlay-type=Xv). Then I had to add the following to the bottom of /etc/X11/xorg.conf to enable 3D, DRI, and OpenGL support by disabling composite extensions.

Section "Extensions"
Option "Composite" "false"
EndSection

---

### Post by OmegaNine on 2006-11-24
ATI X1400 Mob in a Dell 1505
Used the howto here.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a)

---

### Post by to4i on 2006-11-25
Ati X700
Used the howto: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by sabertooth_cat on 2006-11-25
I tried following some of the guides as well as installing and running both EasyUbuntu and Automatix without success re: the Radeon R350 NH [Radeon 9800 Pro] ATI driver. Got error messages like "couldn't find RGB GLX visual" and "double buffered visual".

I managed to "break" X and get the  "fatal user error: no screens found" in the process-managed to get X up and running again and finally found [SIZE="4"][this]("http://ubuntuforums.org/showpost.php?p=415297&postcount=17")[/SIZE] post by [SIZE="4"][COLOR="DarkOrange"]joscar[/COLOR][/SIZE] that I followed (without reinstalling Dapper).

> I must have done about 10 installations of ubuntu and I have yet to fail at getting this to work. If you follow these directions you should have this working. I will do a step by step for you of what got this working for me. Follow exactly please. do as root

1. After a clean install enable all necessary repositories.

2. apt-get update and reboot

3. do uname -r to verify the current kernel

4. go to synaptic. System - Administration - Synaptic Package Manager.

5. search for and install : fglrx-kernel-source, linux-headers and linux-kernel-headres for the kernel version uname -r gave you.now reboot

6. apt-get install xorg-driver-fglrx

7. gedit /etc/X11/xorg.conf and change the driver under device to " fglrx "

8. at this point log out or reboot . doing a fglrxinfo should tell you the ATI drivers are there. This is exactly how i have done it many times so give this a try after a clean install and you should be ok.

I finally got to see:
[PHP]
glxinfo | grep rendering
direct rendering: Yes[/PHP]

[SIZE="4"] Thank You [COLOR="DarkOrange"]joscar[/COLOR][/SIZE]

Here is the result of grep fglrx. I'm new to this, so don't know if my settings are 100% correct or not,but imagine that I'm much farther along than before. Maybe I'm being overly optimistic and this shouldn't be posted here, any feedback would be appreciated. In the event that this is the proper setting (I'm a little worried about "Have to use kernel AGP support to avoid conflicts",but am not done researching that yet) , I'm going to need to figure out how to back this up before I move on to getting my sound working:

[PHP]
sudo dmesg | grep fglrx
Password:
[17179598.144000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologie s, Starnberg, GERMANY' taints kernel.
[17179598.144000] [fglrx] Maximum main memory to use for locked dma buffers: 929  MBytes.
[17179598.144000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179599.240000] [fglrx] Internal AGP support requested, but kernel AGP support  active.
[17179599.240000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179599.240000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps o f chipset)
[17179599.244000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179599.252000] [fglrx] total      GART = 134217728
[17179599.252000] [fglrx] free       GART = 118222848
[17179599.252000] [fglrx] max single GART = 118222848
[17179599.252000] [fglrx] total      LFB  = 128970752
[17179599.252000] [fglrx] free       LFB  = 122679296
[17179599.252000] [fglrx] max single LFB  = 122679296
[17179599.252000] [fglrx] total      Inv  = 0
[17179599.252000] [fglrx] free       Inv  = 0
[17179599.252000] [fglrx] max single Inv  = 0
[17179599.252000] [fglrx] total      TIM  = 0[/PHP]

---

### Post by bonzini on 2006-11-28
I have a Toshiba Satellite A70 laptop with an ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP) (according to the Xorg.log).

1) lspci -n | grep 0300

```
01:05.0 0300: 1002:5835
```

2) lspci | grep VGA

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
```

3) Tweakings required:

After much goofing around with fglrx (in Breezy, Dapper,and Edgy) I went back to the ATI driver in Edgy, and followed the instructions on the Wiki to the letter:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The reason for not using fglrx is that apparently the ATI Linux driver does not support DRM.

---

### Post by Star-x on 2006-11-29
Ok I did post this in different section and then I found this place. So here it is again it wont hurt. Hope it will make more people Happy running 3D

I made my 3D work follow this and you my be lucky like me. [www.just.homelinux.com](www.just.homelinux.com)

ATI RADEON 9600 XT GIGABYTE Motherboard Intel Pentium 3.0 GHz 
:-D

---

### Post by viking777 on 2006-11-29
I have had problems with the ATI Radeaon Xpress 1600 on my new laptop right up until just now. 
Here is how I cured them:

First I went here: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) and filled in the required details (I know it says it is for amd processors and I have an Intel one but it works OK!)

That led me to here: [http://ati.amd.com/support/drivers/linux64...x64-firegl.html](http://ati.amd.com/support/drivers/linux64...x64-firegl.html) from where I downloaded the ATI driver installer.

Then I went here:[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6-inst.html)

and followed the automatic driver install instructions.

1 reboot later and I have a proper graphics system.:D :D :D

---

### Post by the_ace on 2006-12-01
Heres the info on my card:

```

lspci -n | grep 0300
01:00.0 0300: 1002:4152

```
```

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

```

The driver I´m using is version 8.31.5 from ATI. I used the instructions in the section ¨Ubuntu 6.10 using drivers from ATI.com¨ from the [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a")

---

### Post by Forceflow on 2006-12-03
Ati Radeon X1600 AGP edition, with dual screen setup.

Edgy Eft 6.10 clean install
Installed the binary drivers using synaptic.
```
sudo depmod -a
sudo aticonfig --initial=dual-head
sudo aticonfig --overlay-type:Xv
```
After that, I added my monitor refresh rate to the xorg.conf manually, to get the exact resolution and refresh rates i wanted for each monitor. Runs fairly well.

Also, I disabled the Composite extension in my xorg.conf

---

### Post by hvc123 on 2006-12-04
do you have screensavers that work and does 3d work within your wine ????

all my configs and info for my x700 states that 3d acceleration is on yet my screensavers suck and i have no acceleration within wine.

oh my distro is edgy

---

### Post by kinohead on 2006-12-07
HP dv8000 Laptop - 1.8 ghz Turion AMD, 1GB RAM, 80 and 40 GB HDD (dual boot w XP), Broadcomm wireless (not working yet)...

Dapper Drake 6.06 Stable 2.6.15-27-386  (yes 32 bit on a 64 bit machine)
older ati-driver-installer-8.24.8-x86

Bios settings on XPRESS 200M set to +256 shared RAM  

No tweaking;  used the 2nd method AS STATED at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") except I used the 8.24.8-x86 installer NOT the current ATI driver, as it caused system instability and crashes (hard locks).

Took about a bizillion tries to get it right...](*,) 


lspci -n | grep 0300
0000:01:05.0 0300: 1002:5955

lspci | grep VGA
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

I now can run Quake 3 effortlessly at higher resolutions!  yeah!


THANK YOU :mrgreen: to all the gurus who posts assured me even I could do it... eventually!  Thanks!  :-D


PS;  If you do it via the manual install using the older ATI driver, you will have to reisit automatic updates via Apt-get or you will BREAK the driver and have to go back and do it all over again... at least, I think it will...

---

### Post by cos4 on 2006-12-07
I've just installed the ubtuntu package(xorg-driver-fglrx or so) and it worked really well. Some time ago(when there wasn't such a package or I was unaware of it, I built my own deb package from the installer which also worked well. It took some time but all in all installing and using fglrx didn't cause that many problems.

---

### Post by MajEST1c12 on 2006-12-07
1)01:00.0 0300: 1002:4153


2)ATI Technologies Inc RV350 AS [Radeon 9550]

3)[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

---

### Post by qsuc on 2006-12-07
> **MajEST1c12 said:**
> 1)01:00.0 0300: 1002:4153


2)ATI Technologies Inc RV350 AS [Radeon 9550]

3)[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

Method #1 or #2?

---

### Post by qsuc on 2006-12-08
01:00.0 0300: 1002:5653
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

I wrote my own directions, because I had to combine about three different How-Tos: **(email me at nick27-at-gmail.com if you want the document, much better formatted.)**

Download the original attachment
Installing Ubuntu on ATI-hardware

   1. Breathe. This is going to be easy. Every step is as equally important as the last, just check off the steps you've finished with a sharpee.
   2. Download Ubuntu Alternative CD from [http://mirrors.csumb.edu/ubuntu/edgy/ubuntu-6.10-alternate-i386.iso.torrent](http://mirrors.csumb.edu/ubuntu/edgy/ubuntu-6.10-alternate-i386.iso.torrent)
   3. Burn Alternative CD
   4. Installing:
         1. Boot from the CD
         2. Choose Text Install
         3. Answer its questions, press the keys to identify your keyboard, etc.
         4. Give it an easy user/pass (char 'z' for example, you type it a lot while setting up)
         5. Partitioning: (General idea)
               1. 50MB for /boot, using ext3, set as bootable
               2. >5GB for /, using ext3
               3. 1.5x(your RAM) swap area (select 'last on drive, and type swap)
               4. The rest is up to you. Mine looks like:
               5. 15GB for Vista (FAT32, /windows)
               6. 18GB for stuff (FAT32, /stuff)
         6. Use spacebar to select your screen resolution
         7. Remove CD and boot but SIT AT ATTENTION and follow the next steps.
   5. First boot!
         1. Press ESC right after BIOS (while loading GRUB)
         2. Load the RECOVERY option
         3. Lots of scrolling text, etc, until finally: ~:! [sudo makes you the root/superuser so you can run these commands. Step by step, patience!]
         4. sudo vim /etc/apt/sources.list
               1. Enable the Universe and Restricted repositories by removing the '#' at the start of the lines.
         5. sudo apt-get install linux-restricted-modules-common-$(uname -r) [exactly as I wrote it!]
         6. sudo vim /etc/default/linux-restricted-modules-common
               1. Edit DISABLED_MODULES = “fglrx”
         7. sudo vim /etc/X11/xorg.conf
               1. Add these lines to the bottom of the file:
               2. Section “Extensions”

                  Option “Composite” “Disable”

            EndSection

         8. sudo apt-get update ['y' to all installation questions... you'll get it.]
         9. sudo apt-get upgrade
        10. sudo apt-get dist-upgrade
        11. Find a place to make a new directory (/Desktop/ati/ for example) and mkdir it.
        12. Have a friend give tinyurl you the link to the ati driver you need.
        13. [while in your ati folder] sudo wget [http://tinyurl.com/whateverthefuckthelinkis](http://tinyurl.com/whateverthefuckthelinkis)

Installing the ATI Driver

Install necessary tools:

sudo apt-get update

sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r)

Create .deb packages:

sudo ln -sf bash /bin/sh 
[note the “bash” here, not sudo! and use TAB to finish file names, just like on HORNET]

bash ati-driver-installer-*whatever*.run --buildpkg Ubuntu/edgy

sudo ln -sf dash /bin/sh

Install .deb packages:

[TAB to finish these file names, not *whatever*]

sudo dpkg -i xorg-driver-fglrx_*whatver*.deb

sudo dpkg -i fglrx-kernel-source_*whatever*.deb

sudo dpkg -i fglrx-control_*whatever*.deb

Remove any old fglrx debs from /usr/src/:

sudo rm /usr/src/fglrx-kernel*.deb

Fix a possible error:

sudo mkdir /usr/src/modules/fglrx/linux

sudo touch /usr/src/modules/fglrx/linux/config.h

Compile the kernel module:

sudo module-assistant prepare

sudo module-assistant update

sudo module-assistant build fglrx

sudo module-assistant install fglrx

sudo depmod -a

Configure xorg.conf:

sudo vim /etc/X11/xorg.conf 
[go to Device, and change driver to “fglrx”]

sudo aticonfig --overlay-type=Xv

Now make sure it's going to run and reboot:

sudo vim /etc/modules 
[add fglrx on a new line, no quotes just fglrx] 
sudo shutdown -r now
Confirm that it worked

$ fglrxinfo

display: :0.0  screen: 0

OpenGL vendor string: ATI Technologies Inc.

OpenGL renderer string: RADEON 9700 Generic

OpenGL version string: 2.0.6174 (8.31.5)

$ glxinfo | grep render

direct rendering: Yes

If your direct rendering is disabled, do this:

sudo mkdir /usr/X11R6/lib/modules

sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/

---

### Post by mjm01010101 on 2006-12-11
Just now I followed the guide "whatever" posted (3rd post) except for edgy eft, and it worked wonderfully.  Really appreciate it, most of the other guides I had found seemed iffy and I was afraid to take it on...
ATI Mobile Radeon 9600
01:00.0 0300: 1002:4e50


Thanks guys, I'm a windows admin, but have switched over to ubuntu at home full time.  :)

---

### Post by DonQuixote on 2006-12-12
MJM,

What method did you use?

---

### Post by cosine7 on 2006-12-12
Never worked for me in 5.10 6.06 or 6.10, but i did a clean install (Kubuntu 6.10) and it worked using this [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by mjm01010101 on 2006-12-12
> **DonQuixote said:**
> MJM,

What method did you use?

[This method.]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Originally I had started on ubuntu a long time ago, but on my Alienware Area 51 I couldn't install X right unless I used some arcane switch.  Eventually I dban'ed it, rebuilt with dapper, got in at 1024x768 with no acceleration, remembered that the laptop was capable of higher, looked at various tweaks that I was afraid to do, updated to edgy, and then finally bit the bullet with the above linked guide.

---

### Post by TDsai on 2006-12-13
lspci -n | grep 0300
01:00.0 0300: 1002:4150

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

Ubuntu Edgy Eft 386
Experience: Ubuntu N00b


first i tried fglrx-XGL-Beryl and everything seems to work great except i cant get direct rendering and i cant open google earth and probably some other 3D apps which require Direct rendering.. Enemy Territory works perfectly though and beryl animations are awesome. I was pretty much satisfied since i only surf the net and watch videos most of the time. I got the dual head working fine too!

After reading alot of good things about open source drivers for radeon and how far more better Aiglx then the XGL one, i backed up my drive and reinstall a fresh copy of Edgy and set it up to use AiGlX and Beryl, but i wasn't very much impressed as with my previous combo. Yes i got Direct Rendering ON, Composite enabled, but Firefox is sluggish while scrolling, i get a lot of flickering on my screen, drop shadows doesn't werk so well, ugly and very slow blur effects, mouse trash trails when using third mouse button, beryl slow animations, problems with resolutions and refresh rates (always going back to 85 when i set it to 75).. im not blaming anyone.. could be my setup that screws my system up,  so im not giving up finding solutions. but im sticking with fglrx for now so i can enjoy and explore more this kick *** OS!

Edit: I just realize the title of this thread is NOT "the whine thread" lol. both of these methods worked but not 100% at least not yet.

1) fglrx-XGL-beryl [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

2) AiGlx-beryl [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by mcduck on 2006-12-13
1) 01:00.0 0300: 1002:71c5
2) 01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5
(It's Mobility Radeon x1600, using RV530 GPU)

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

Then I added this to xorg.conf:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

..and rebooted. Worked perfectly. That was even easier than in Windows, if you ask me :D

I have Mobility Radeon X1600 on my laptop and Radeon 9600XT on my desktop. The info in the beginning is about the laptop as the desktop machine is about 1000km from where I am now ;)

---

### Post by qsuc on 2006-12-13
01:00.0 0300: 1002:5653
ATI Technologies Inc Radeon Mobility X700 (PCIE)

I have a Sager NP4880, so send to me at nick27 -monkey- gmail for any help.

I stuck with getting the in-built open-source radeon driver working. Here's my /etc/X11/xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"radeon"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"drm"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Option "MonitorLayout" "NONE, LVDS"
	Identifier	"X700"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"X700"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		ViewPort	0 0
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Need to change my AGP speed up and some other tweakings, but now I'm running Ubuntu Edgy with AIGLX on "radeon" open-source and Beryl 0.1.3!

---

### Post by Hendrixski on 2006-12-13
Wow that was easy! I followed the directions off of the first link and was done in 5 minutes (including the time it takes to reboot, this is a kernel upgrade after all).

----

"Do you pine for the days when men were men and wrote their own device drivers?" - Linus Torvalds

No I don't, I can't wait for the day when all driver installs will be single click operations.

---

### Post by EminNew on 2006-12-13
01:00.0 0300: 1002:5964 (rev 01)
ASUS 9200se 128 Mb

Following instructions at:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Installing_Edgy.27s_Included_Driver_.288.28.8.29](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Installing_Edgy.27s_Included_Driver_.288.28.8.29)
solved my troubles.

Here's how:
```
sudo gedit /etc/X11/xorg.conf
```
Add this at the end of opened file:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
Save and close file.

Make sure Restricted repository is enabled in /etc/apt/sources.list/ before entering following commands:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Reboot your computer.

---

### Post by IanW on 2006-12-14
FYI ATI drivers just went up to version 8.32.5, mostly bug fixes plus support for xorg 7.2

---

### Post by pormogo on 2006-12-19
this time I installed it based on experiance I got from the ubuntu wiki around the time of Breezy Badger release. I installed the driver via apt-get and then specified the fglrx driver in /etc/X11/xorg.conf and the rest is history.

---

### Post by QOLIM on 2006-12-23
worked with

tseliot's repo

and this for the latest version (8.32.5)
```
sudo ln -sf bash /bin/sh
sudo apt-get remove fglrx-kernel-2.6.17-10-generic
bash ati.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
sudo dpkg -i xorg-driver-fglrx_*.deb
sudo dpkg -i fglrx-kernel-source_*.deb
sudo dpkg -i fglrx-control_*.deb
sudo rm /usr/src/fglrx-kernel*.deb 
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
sudo cp libGL.so.1.2 /usr/lib/

```

---

### Post by Hendrixski on 2006-12-27
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

The Ubuntu package didn't work on this one, I tried twice.  :( and Google Earth doesn't exactly work without the 3d acceleration.  Haven't tried the ones from ati's website yet, probably won't have a chance to.

---

### Post by Mateo on 2006-12-28
Used this guide:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you are having problem using the synaptic method, try this guide and compile manually.  It will pay off in the end.

---

### Post by NT4usB on 2006-12-29
ct@wimp:~$ lspci -n | grep 0300
01:00.0 0300: 1002:4150

ct@wimp:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

It worked right out of the box... Kind of weak though.
ct@wimp:~$ glxgears -printfps
1270 frames in 5.2 seconds = 243.427 FPS
1254 frames in 5.3 seconds = 238.161 FPS
1254 frames in 5.4 seconds = 231.765 FPS
ct@wimp:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


Gigabyte GA-8IHXP v3.0 P4 3.0 1GB PC1066 Rambus RIMM

---

### Post by ovidescu on 2007-01-01
```
lspci -n | grep 0300
```
01:00.0 0300: 1002:7142
```
lspci | grep VGA
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]

How I got it to work ? Not that easy.
I followed many HOW-TOs but all I ended up with was the MESA driver and frame drops with fullscreen videos. How I finally did it: uninstalled xorg-driver-fglrx and dependent packages  using Synaptic. Rebooted in recovery mode (where it auto logs in as root) and ran ```
dpkg-reconfigure xserver-xorg
``` from where I chose the "ati" driver and kinda used the defaults for the rest of settings. Rebooted again, in recovery mode, again. ```
nano /etc/X11/xorg.conf
``` found the Device section, Driver line, changed "ati" to "fglrx", then, at the end of file, added the following 
```
Section "Extensions"
Option "Composite" "0"
EndSection
```
Ctrl+X to close the file, **don't forget to save it**.
I already had the restricted repository enabled, so went ahead with the following
```
apt-get update
apt-get install linux-restricted-modules-$(uname -r)
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv
shutdown -r now
```
I attached my xorg.conf file.
Hope this helps.

Ovidiu

---

### Post by NT4usB on 2007-01-01
> **ovidescu said:**
> ```
lspci -n | grep 0300
```
01:00.0 0300: 1002:7142
```
lspci | grep VGA
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]

How I got it to work ? Not that easy.
I followed many HOW-TOs but all I ended up with was the MESA driver and frame drops with fullscreen videos. How I finally did it: uninstalled xorg-driver-fglrx and dependent packages  using Synaptic. Rebooted in recovery mode (where it auto logs in as root) and ran ```
dpkg-reconfigure xserver-xorg
``` from where I chose the "ati" driver and kinda used the defaults for the rest of settings. Rebooted again, in recovery mode, again. ```
nano /etc/X11/xorg.conf
``` found the Device section, Driver line, changed "ati" to "fglrx", then, at the end of file, added the following 
```
Section "Extensions"
Option "Composite" "0"
EndSection
```
Ctrl+X to close the file, **don't forget to save it**.
I already had the restricted repository enabled, so went ahead with the following
```
apt-get update
apt-get install linux-restricted-modules-$(uname -r)
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv
shutdown -r now
```
I attached my xorg.conf file.
Hope this helps.

Ovidiu

I tried it your way (along with every other tootorial and instructions on these boards) except that I used Alberto's drivers, and I still have mesa. 
Going to switch to the Edgy ones and try again...

---

### Post by NT4usB on 2007-01-04
Finally, after many attempts using various methods and (my own neub) variations of methods, I got it using:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Every other way ended up one big mesa.

ct@wimp:/etc/X11$ lspci -n | grep 0300
01:00.0 0300: 1002:4150

ct@wimp:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6234 (8.32.5)

ct@wimp:/etc/X11$ glxgears --printfps
Warrning: unknown parameter: --printfps
ct@wimp:/etc/X11$ glxgears -printfps
2475 frames in 5.0 seconds = 495.000 FPS
2484 frames in 5.0 seconds = 496.425 FPS
2485 frames in 5.0 seconds = 496.986 FPS
2476 frames in 5.0 seconds = 494.826 FPS
2477 frames in 5.0 seconds = 495.387 FPS


Gigabyte GA-8IHXP v3.0 P4 3.0 1GB PC1066 Rambus RIMM

---

### Post by ovidescu on 2007-01-05
Sweet !

---

### Post by blu3sman on 2007-01-05
Installing the ATI drivers has been a major headache for me ( as it has no doubt been for many ), since day 1 of installing Ubuntu. Originally i d/loaded the 8.32.5 drivers from ATI and used their howto but always ended up with the "Mesa" driver.

I'm now on my fourth install, ( Edgy 64bit ) and this time i tried something different. I had been following the TSELIOT thread on trying to get them working, but i think because i had installed the 8.32 drivers, i was having no luck. So upon this fresh install i found this howto
in the 64bit forum. [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)
using the Ubuntu way,

AND IT WORKED LIKE A CHARM!!! :)

Not only did i get this,
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

but XGL/Beryl work like a charm also ( howto get XGL/Beryl working on same link )

Hope this helps someone :)

---

### Post by Kubunteando on 2007-01-06
My model is an ATI Mobility Radeon 9000 rev (02) with 32MB Video RAM.

I tried first the ATI drivers 8.28.8 with flgrx (same as the Ubuntu ones in the repositories for  edgy). But the use of the CPU when playing 3D games was very high, even it was disturbing the movement of the mouse. Unfortunately there is no newer drivers for this card, as they are the last ones ATI will release.

So I changed to Open Source Mesa with DRI (Direct Rendering Hardware acceleration) following the "building" guide in:
[http://dri.freedesktop.org](http://dri.freedesktop.org). Which requires some compilation. Although I did not find any issues when following the guide (only that with the current kernels there is no need to compile DRM, since the kernel includes already the DRM modules. Only it was needed to compile the libDRM and MESA)

Now almost all the games perform better. Less CPU use and higher Frames per Second.
Only in big maps in Sauerbraten the FPS go down (still playable), since it seems that the Open Source do not have "Occlusion Query" support because ATI has not provided info about how is implemented in the ATI cards.

Just some hints so you don't brake your head:

- Regnum Online seems to crash in Edgy, while working well in Dapper
- With the Mesa Open Source Drivers with DRI GoogleEarth works. No way with the ATI drivers.

It seems that Mesa 6.5.2 works even better.
In a resolution 1400x1050 I get around 2200 FPS with "glxgears -printfps" with the default window size.

---

### Post by puccaso on 2007-01-06
```
mahir@jt-laptop:~$ lspci -v | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA])

mahir@jt-laptop:~$ lspci -n | grep 0300
01:00.0 0300: 1002:7145





```

im having to use binary drivers and thus cant use compiz..

---

### Post by Absurd on 2007-01-08
As an update to my thread [here](http://www.ubuntuforums.org/showthread.php?t=332431). I got the ATI driver to work with my custom kernel by installing the driver manually using the tutorial [here](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide). However, there was a problem during the comple because there was an error that "linux/config.h" was not found. So, what I did was I went into the directory of my custom kernel's source into include/linux/ and did "sudo touch config.h". Direct rendering now works with my custom kernel. :D

---

### Post by japser on 2007-01-10
I'm running feisty fawn

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6234 (8.32.5)


lspci -v | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE) (prog-if 00 [VGA])

lspci -n | grep 0300
01:00.0 0300: 1002:5653

my xorg.cong for the device and screen

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	#ChipID		0x5652
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	#Option  "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	#option         "AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option 		"Composite" "Disabled"
EndSection

 glxgears
23596 frames in 5.0 seconds = 4719.185 FPS
23997 frames in 5.0 seconds = 4799.216 FPS
24187 frames in 5.0 seconds = 4837.384 FPS
24201 frames in 5.0 seconds = 4840.167 FPS
24152 frames in 5.0 seconds = 4830.341 FPS

i had to move some mountains to install fglrx, the best quide (i followed so many) is the wiki edgy tutorial in the end the thing that was holding fglrx back was in /etc/modules  #drm had to be commented out to let fglrx work!

---

### Post by Absurd on 2007-01-10
Did you build a custom kernel or did you stick with the ubuntu kernel?

---

### Post by haggus on 2007-01-11
02:00.0 0300: 1002:4153

02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

No tweaking installed using easy ubuntu

---

### Post by rj686 on 2007-01-12
I'm running 8.33.6 Drivers From Ati's Site.

Followed the Wiki article on how to compile them into .deb packages and install it :)

---

### Post by Hendrixski on 2007-01-14
When I first installed the drivers on the wiki at the begining of this article they worked great for things like GoogleEarth, but when I tried to update XGL recently they weren't doing so well, so I got the latest ones from the ati website and now everything is working really smoothly.
There's an even more helpful wiki here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by v.ipe.r on 2007-01-15
```
$ lspci -n | grep 0300
01:00.0 0300: 1002:4a50
```

I followed the [URL="https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2"]BinaryDriverHowto/ATI 
[/URL] and installed the 8.33.6 Drivers From Ati's Site.

```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.6286 (8.33.6)

$ glxinfo | grep render
direct rendering: Yes
 GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
```

Thanks to every one who contributed to that wiki!:D

---

### Post by jaywhy13 on 2007-01-17
Just some gerenal tips

Make sure that the symlinks are right... it's been spoken about many times
As best as possible... try to install the drivers when X is not running... that has helped me
So go Ctrl+Alt+F1 and sudo su and then install the drivers.
After install do this
module-assistant prepare,update
module-assistant build,install fglrx

That usually works each time....

Always do cat /var/log/Xorg.0.log | grep fglrx to see what errors you're getting

Always try apt-get dist-upgrade before and apt-get install linux-restricted-modules-$(uname -r) and apt-get install linux-headers-$(uname -r) to make sure that the headers are nice... then run module-assistant thingy I showed above again

Always check that compositing it off... that is
Section "Extensions"
 Option "Composite" "0"
EndSection

That can stop beryl from loading

---

### Post by online14230 on 2007-01-18
FINALLY got it working. Dell Optiplex GX150, 320MB SDRAM, ATI Radeon 9200SE, Dell 17" monitor, USB KB and mouse + ps2 KB. :)
I used the 8.28 ATI driver and a combination of howto's.
Still have 1 problem though: Monitor is too bright and no idea how to turn it down. Everything shines, cant see icons and can barely make out text. Havent had a chance to try a vid yet. I had overclocked the videocard via winXP using ATITOOL but have since returned it to normal. In windows, the monitor seems to be a tad dark, but thats not a problem...
Also, from the time I power up, tvout is on. I see the grub menu onscreen, the bootup sequence and everything else, as displayed on the monitor. The TV seems to be quite vivid, ie color saturation is quite high. Any ideas how I could fix this would be welcome, or should I just switch back to the mesa driver?

Tseliot, sorry about the q's in your thread. And, once again, All kudos and props and everything to you, thanks for your dedication to the Ubuntu Community and especially for this thread!

---

### Post by je1117 on 2007-01-19
Holy crap. I got it to work. Anyone with a radeon 9200 I HOPE you should have to look no further if you are experiencing THESE symtoms:

1. Open source drivers aren't working for you.
2. Closed source drivers boot you to a black screen. (also, my computer wasn't even getting to the login screen. I couldn't hear the drums. I don't know if this matters.)
3. You are about to bash your skull looking for an answer.

My solution was quite simple. I followed [THIS GUIDE]("http://www.ubuntuforums.org/showthread.php?t=204910") to the tee. Since this how I!!! got this to work, i'm going to say, if you are the same as me, adding "fglrx" to linux-restricted-modules-common is going to get you jack.

After you type in this command sudo aticonfig --overlay-type=Xv, in the guide, reboot into recovery mode and type:

sudo nano /etc/X11/xorg.conf

navigate to where your fglrx section is and above the other options listed, put this:

Option         "BusType" "PCI"

Reboot, check fglrxinfo and glxinfo in the terminal. That one line has been seperating me from my sanity. I truly hope this helps someone who was in my position with a 9200, probably the same for a 9250 or 9200se.

<3ubuntu(now)

---

### Post by gingerj on 2007-01-20
Hi all I'd just like to confirm that I got the ATI Mobility Radeon X1300 to work on Ubuntu 6.06 following these steps:

1) Open Synaptic and download the fglrx drivers,
2) sudo depmod -a
3) sudo aticonfig --initial
4) sudo aticonfig --overlay-type=Xv
5) sudo shutdown -r now

Was pretty simple and now I can my Ubuntu partition at a great resolution and my even get the 3D desktop stuff working.

Hope that helps anyone!

---

### Post by iammeagain on 2007-01-23
#1)

code:
 lspci -n | grep 0300
01:00.0 0300: 1002:5960 (rev 01)


#2)
code: 
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)


#3) A live DVD called Sabayon. It automatically found my card and set everything up, i just hit one button.
I know this probably doesnt cound cuz its not on ubuntu but just incase anyone else trying with the same card at least wants a taste of the eye candy

---

### Post by yusufk on 2007-01-23
I've been through 100's of guides and howtos and I still can't get it to work.

At the moment I've installed the debs created by ati-driver-installer-8.32.5-x86.x86_64.run

I've created /usr/bin/startxgl.sh with:

```

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
DISPLAY=:1
exec gnome-session

```

and /usr/share/xsessions/xgl.desktop with
```

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```

and appended
```

DISABLED_MODULES="fglrx"

```
to  /etc/default/linux-restricted-modules-common

and my xorg.conf:
```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "HP LCD"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "MetaModes" "1920x1200-1600x1200"
#	Option	    "OverlayOnCRTC2" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "HP LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1920x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1920x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1920x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1920x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1920x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1920x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

```

Now, when I choose Xgl from the GDM menu at login, there is a pause and then I get:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "yusuf"
/etc/gdm/Xsession: Beginning session setup...

Fatal server error:
no screens found

(gnome-session:9522): Gtk-WARNING **: cannot open display:

```

glxinfo | grep rend yields:
```

direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY FireGL V5000 Pentium 4 (SSE2) (FireGL) (GNU_ICD)

```

and fglrxinfo gives:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FireGL V5000 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.6234 (8.32.5)

```


So, does anyone have any clues? Surely the amount of posts on the topic and failed attempts demonstrates a major problem that somehow needs to be addressed because ppl want the special effects.

](*,)

---

### Post by Homunculi on 2007-01-24
lspci -n | grep 0300
0000:01:00.0 0300: 1002:7142
________________________________________________________
glxinfo | grep render
direct rendering: Yes
    GLX_ATI_render_texture
OpenGL renderer string: Radeon X1300 Series Generic
_________________________________________________
[17179602.820000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179602.824000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179602.824000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179604.432000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179604.432000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179604.432000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179604.432000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179604.444000] [fglrx] total      GART = 134217728
[17179604.444000] [fglrx] free       GART = 118222848
[17179604.444000] [fglrx] max single GART = 118222848
[17179604.444000] [fglrx] total      LFB  = 261091328
[17179604.444000] [fglrx] free       LFB  = 250605568
[17179604.444000] [fglrx] max single LFB  = 250605568
[17179604.444000] [fglrx] total      Inv  = 0
[17179604.444000] [fglrx] free       Inv  = 0
[17179604.444000] [fglrx] max single Inv  = 0
[17179604.444000] [fglrx] total      TIM  = 0
____________________________________________________________
 glxgears -printfps
10011 frames in 5.0 seconds = 2002.151 FPS
10838 frames in 5.0 seconds = 2167.455 FPS
10846 frames in 5.0 seconds = 2169.106 FPS
________________________________________________________________-
detecting video ram ( set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
2793 MHz CPU
1008 MB System Memory
64 MB Video Memory
Async thread started
WARNING: Couldn't load image: models/monsters/burn_misc_sm
Unknown command '--help'
guid set to otdz5I0JcK0
WARNING: idSession: triggering mainmenu watchdog
------------ Game Map Shutdown --------------


i thought i had the card installed correctly 
everything look so clean and good from quake 2 to rtcw quake3
but that last output is out of the quake 4 term window .. i noticed that after getting it installed and everything looked fine untill the graphics got a little heavy and then it got choppy ... very hard to play .. 
i seen the new driver on the web page from jan 10 2007 ... if there is a walk though for that i might give it a try 
it also says that fglrx is no longer a part of the driver ... :confused:

---

### Post by RobNyc on 2007-02-04
I installed the 8.33 drivers following the guide on my x1600 pro 
Rebooted and my **** was just all weird. in Linux Mint 2.2 beta 
gonna try on Ubuntu 6.10 and then Ubuntu herd and see

---

### Post by jcolonel on 2007-02-04
My video driver in Feisty Alpha 3

01:00.0 0300: 1002:5961 (rev 01)

Worked out of the box. I have tried two Ati cards and they both work on
Dapper, Edgy, and Feisty with no tweaking.

---

### Post by LostPavek on 2007-02-04
1)  01:00.0 0300: 1002:71c2
2)  Sapphire Radeon X1600 PRO AGP 512mb
3)  First: I followed the directions found in the Ubuntu Documentation for Ubuntu 6.10 located here:  [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html#installatidriver](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html#installatidriver)
(Note: I used Synaptic to install the xorg-driver-fglrx package.)

Second: I needed to add the following to my xorg.conf file:
```

Section "Extensions"
	Option "Composite" "false"
EndSection

```

Third: I needed to lower the AGP Aperture setting in my BIOS to 128mb.  It was initially set to 256mb but there were **Weird Graphical Problems*.  After setting the AGP Aperture to 128mb, everything worked perfectly and has direct rendering.  This was the crucial step for me and I could not find it documented elsewhere.  I only stumbled upon this after 2 days of tinkering.

* Weird Graphical Problems - The computer would only draw the bottom and top 20% of the screen, the computer would also draw the middle portion of the screen if I used the mouse or keyboard to highlight text.

---

### Post by RobNyc on 2007-02-04
> **jcolonel said:**
> My video driver in Feisty Alpha 3

01:00.0 0300: 1002:5961 (rev 01)

Worked out of the box. I have tried two Ati cards and they both work on
Dapper, Edgy, and Feisty with no tweaking.


I got the new iso.. I'm gonna get it installed then

---

### Post by koldfiya on 2007-02-06
I'm new here, (to the forum and new to Linux/Ubuntu), so please take it easy on me...

I've been trying for the past couple of days to install the ATI driver for Raedon Xpress 200G, but everytime, (and this has happend a good 10 or more now), that I get to the restart part of each toturial, my monitor won't come on after the "Ubuntu Load screen"

I don't want to reformat the HD again just to get the OS back up... I've spent too much time downloading stuff.

Any suggestions?
ANY help would be appreciated...

---

### Post by SoundOfPoetTree on 2007-02-06
Ubuntu 6.10 Edgy Eft
```
**lspci -n | grep 0300**
01:00.0 0300: 1002:7149
```
Card Model: ATI Radeon Mobility x1300
Kernel: 2.6.17-10-generic

No tweaks necessary. I used the [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a") to a T. The only difference between what I did and what the guide suggests is that I did NOT use the 8.33.6 (newest) ATI driver. I could not, for the life of me, get that driver to properly work (3d-acceleration and DRI would not work). Using the [8.28.8 driver]("http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html") from ATI's previous driver database, for some reason, made things work like a charm.

---

### Post by calman on 2007-02-07
1.)  01:00.0 0300: 1002:7142
2.)  ATI Radeon X1300 Pro
3.)  Followed these instructions:

```
# sudo apt-get install xorg-driver-fglrx
# sudo dpkg-reconfigure xserver-xorg (make sure to select the "fglrx" driver instead of "vesa")
# sudo gedit /etc/X11/xorg.conf

Make sure you have the following settings

--------------------------------------------

Section "Device"
	Identifier	"ATI Graphics Adapter"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	BusID		"PCI:1:0:0"
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "False"
EndSection

--------------------------------------------

After reboot you can test that the accelerated driver is really used with the following command:

# glxinfo | grep -i direct
direct rendering: Yes

```

---

### Post by Arthur75 on 2007-02-08
The guide didn't work for me on a radeon 9200 SE hooked up on DVI on a Dell 1920x1200 with Edgy

On restarting the X server I get a blank screen, (I can still hear ubuntu by pressing some keys though   )

And that's it ....
Same on reboot

So how do I move from here ? :confused:

---

### Post by jtapper on 2007-02-11
1) 0000:01:00.0 0300: 1002:4150

2) lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

3) No tweaking at all.

DIrect rendering was working out of the box, but with fglrx performance is much better. Haven't tried dual screen yet though.

---

### Post by Butcher_swe on 2007-02-11
1 
magnus@magnus-desktop:~$ lspci -n | grep 0300
01:00.0 0300: 1002:5d57
magnus@magnus-desktop:~$ 
2
magnus@magnus-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)]
magnus@magnus-desktop:~$ 
3
Guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Works like a dream:guitar:

---

### Post by palmerthegeek on 2007-02-13
Good morning all,

I used the Wiki ATI Radeon HowTo:.....and a few of the various ATI/ beryl treads.

Any how here is the lspci stuff:

01:00.0 0300: 1002:5460

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]


Have a great day all!

---

### Post by jocheem67 on 2007-02-13
Section "Monitor"
	Identifier   "Philips 190S"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:4:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Monitor    "Philips 190S"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


That&#347; the working confuguration for me. I had to manually change "ati" into "fglrx" ,and not use the ativonfig -- initial thingie... that would result in two monitor-sections and a black screen when rebooting. I had to make sure that my monitor-settings would be kept.

Now it works!

---

### Post by magichsjx on 2007-02-13
> a) 0000:01:00.0 0300: 1002:5046
b) 0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

no special tweaks needed.

---

### Post by TLoockx on 2007-02-15
Card Model: Sapphire Radeon X1950Pro
Kernel: 2.6.17-10-generic

Tried a lot of things (and got really frustrated) but this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.33.6_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.33.6_Driver_Manually")
(using method 2) worked just fine.

---

### Post by seamus7 on 2007-02-17
I'm using the ATI Radeon Mobile X1300 with 128MB of video ram on an Intel Centrino Core 2 Duo processor. I am now using fglrx 8.28.8 successfully. The trick seems to be booting into Recovery Mode and configuring everything there. Don't ask me why. Otherwise, the method is similar to most other methods successfully used with this card. Thanks to ovidescu for _[COLOR="Blue"]**[step by step instructions]("http://ubuntuforums.org/showpost.php?p=1955179&postcount=120")**[/COLOR]_ posted earlier in this thread.

:KS  01:00.0 0300: 1002:7149

:KS  01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7149

:KS  all tweaks are described in ovidescu's _[COLOR="Blue"]**[step by step instructions]("http://ubuntuforums.org/showpost.php?p=1955179&postcount=120")**[/COLOR]_.

---

### Post by Ren McCourtey on 2007-02-17
[LIST]
[*]lspci -n | grep 0300
05:00.0 0300: 1002:7109


[*]05:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800]
(Sapphire Radeon X1800XL 256MB)


[*]I used Method 2 described here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
That means fglrx 8.33.6. Only thing not working is fsaa, still analysing. Even ATi control panel supposed broken in 8.33.6 is working.
[/LIST]

---

### Post by Kevf on 2007-02-18
> **jocheem67 said:**
> Section "Monitor"
	Identifier   "Philips 190S"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:4:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Monitor    "Philips 190S"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


That&#347; the working confuguration for me. I had to manually change "ati" into "fglrx" ,and not use the ativonfig -- initial thingie... that would result in two monitor-sections and a black screen when rebooting. I had to make sure that my monitor-settings would be kept.

Now it works!

I have the exact same problem! Can you tell me which tut you used and did you skip these steps? 

```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

---

### Post by dsimpson on 2007-02-24
lspci -n | grep 0300

0000:01:00.0 0300: 1002:5246

edited /etc/X11/xorg.conf
changed "device" - driver from ati to "vesa". that was the only one that worked. "fglrx" totally failed,as well as "ati".

---

### Post by xchric on 2007-02-24
01:00.0 0300: 1002:554b
01:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]

follow method 2 here
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)
without applied 
DISABLED_MODULES="fglrx"

---

### Post by LKN4SPACE on 2007-02-25
I'm trying to get the ATI Radeon 9550 driver installed by following: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But when i type in: sudo apt-get update in the terminal it gets to 99% and times out. Do i keep trying to run this at a later time? Maybe the server is down? Don't quite know what to do - any advice?

Thanks.

---

### Post by h0lix on 2007-02-26
1) 0000:01:00.0 0300: 1002:4e48
2) ATI Radeon 9800 Pro
3) installed fgrlx-control and xorg-driver-fgrlx through apt-get
4) changed "vesa" to "fgrlx" in xorg.conf
5) restarted X and refresh rate and resolution worked great

---

### Post by dantum on 2007-02-27
Just managed to install the latest drivers from ATI. 8.34.8 with my custom 2.6.20 kernel on hp nx6125 with express M200 card.

Here is what i did.


Get the patch from:

mkdir 8.34

wget [http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.34.8-for-2.6.20.patch](http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.34.8-for-2.6.20.patch)

*get driver from ati site.*

sh ati-driver-installer-8.34.8-x86.x86_64.run --extract my_folder_name

*go into* " my_folder_name/common/lib/modules/fglrx/build_mod "

patch -p0 <   /patch_location/fglrx-8.34.8-for-2.6.20.patch 
(note: this is the usual way to patch but there other ways. just make sure you type it correctly)


get to back to root of 8.34 folder 

*go into my_folder_name*

*create ubuntu specific files.*

sudo sh ati-installer.sh 8.34.8 --buildpkg Ubuntu/edgy

install the packages 

sudo dpkg -i xorg-driver-fglrx_8.34.8-1*.deb
sudo dpkg -i fglrx-kernel-source_8.34.8-1*.deb
sudo dpkg -i fglrx-control_8.34.8-1*.deb

*remove old junk if present*

sudo rm /usr/src/fglrx-kernel*.deb

Install the kernel module

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

Added
As noted below you need to disable composite extension support in xorg.conf and also AIGLX rendering. 

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

REBOOT.

Hope this helps. From what i heard the next version of ATI drivers is out on 14th of march and will include the 2.6.20 kernel support. So patching won't be needed.

Sorry for my rather basic tutorial and I hope everyone understands it.


Info Sources used:
[http://www.linuxespanol.com/ftopic17881.php](http://www.linuxespanol.com/ftopic17881.php)
[http://ati.cchtml.com/show_bug.cgi?id=566](http://ati.cchtml.com/show_bug.cgi?id=566)
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by onaka_the_kaka on 2007-02-28
Wow! This patch finally fixed my Ati Mobility Radeon x1300 that's in my Dell Inspiron 6400 (same as e1505). Thanks to whoever made the patch and this guide! 

About the guide: I had to execute the patch -p0 command like this:
patch -p0 <patchfile> <file to be patched>
e.g:
patch -p0 fglrx-8.34.8-for-2.6.20.patch firegl_public.c

This wasn't all clear in the guide but maybe there is another way to do it as well? I also had to disable composite in xorg.conf, so don't forget that or this won't work!:-)

---

### Post by tomten on 2007-02-28
When I first installed Edgy, the xserver crashed at startup with the default 'ati'-driver. After some reading in this [thread]("http://ubuntuforums.org/showthread.php?t=190133") I finally got the 'fglrx'-driver to work.

I had major problems getting direct rendering with the 8.28-version, so I downloaded the latest driver from ATI and followed the instructions EXACTLY in this [HOWTO]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

The installation went flawless and direct rendering now works perfectly with the latest 8.34.8-drivers on my radeon 9800 Pro. But I must admit that the performance under windows xp is significantly better than in linux, atleast when watching hidef-video. I guess I have some optimizing left to do.

---

### Post by clownshoes19 on 2007-03-01
I am using a bleeding edge version of Feisty Fawn (kernel 2.6.20-9-generic).
> lspci -n | grep 0300
01:05.0 0300: 1002:5955
> lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)


> 
glxgears
4708 frames in 5.0 seconds = 941.531 FPS
6637 frames in 5.0 seconds = 1327.246 FPS
6629 frames in 5.0 seconds = 1325.779 FPS
6601 frames in 5.0 seconds = 1320.115 FPS
6638 frames in 5.0 seconds = 1327.578 FPS
6646 frames in 5.0 seconds = 1329.178 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 39 requests (38 known processed) with 0 events remaining.


I changed [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) to account for 2.6.20.* patches.  I finally got my 200M to work using these instructions.  I need some people to test my instructions.  Apparently, somebody on this thread already posted instructions on how to use the patch, but I feel mine are more complete and easier to follow.

Still a no go with Beryl, but I haven't tried exceptionally hard, point-of-fact being I most likely could have gotten it to work with another fifteen minutes of effort and a little motivation--fact of the matter is I don't want beryl till its added to Ubuntu out of box.

---

### Post by f3nol on 2007-03-02
1) 01:00.0 0300: 1002:4150
2) ATI Radeon 9600
used this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
no tweaking needed after that (using Edgy)

---

### Post by Memocjro on 2007-03-21
Did like dantum said here: [http://ubuntuforums.org/showpost.php?p=2221323&postcount=162](http://ubuntuforums.org/showpost.php?p=2221323&postcount=162)

Except that i added 
the 
DISABLED_MODULES="fglrx"
in restricted modules.

The results:

```
memo@memo-desktop:~$ lspci -n | grep 0300
01:00.0 0300: 1002:5b63
```
```
memo@memo-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
```
```
memo@memo-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)
```
```
memo@memo-desktop:~$ glxgears
14645 frames in 5.0 seconds = 2928.831 FPS
14633 frames in 5.0 seconds = 2926.414 FPS
14686 frames in 5.0 seconds = 2937.166 FPS
14673 frames in 5.0 seconds = 2934.543 FPS
14687 frames in 5.0 seconds = 2937.330 FPS
14675 frames in 5.0 seconds = 2934.809 FPS
14683 frames in 5.0 seconds = 2936.447 FPS
14634 frames in 5.0 seconds = 2926.689 FPS
```

The only thing that is curious to me is that now i have two updates available:
fglrx-control (from 8.34.8-1 to 8.34.8+2.6.20.3-12.11)
fglrx-kernel-source (from 8.34.8-1 to 8.34.8+2.6.20.3-12.11)

Should i install them? Should i not? :D I am afraid i will break my "toy" :rolleyes:

---

### Post by Afkpuz on 2007-03-27
1.) 0000:01:00.0 0300: 1002:5653

2.) 0000:01:00.0 VGA compatible controller: ATI Technologies Inc**_ Radeon Mobility X700_** (PCIE)

3.) Normal install disc would lock up before anything installing happened.  Had to use alternate disc just to get into set up.  Then, had to follow wiki to get into Xserver.  []("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Finally, in order to get dual screen support, I had to install driver from ATI site.  I used auto-installer from their site and it worked great.  However, I have noticed that now, my screensavers lag very badly.  They didn't before I installed ATI's driver.

---

### Post by LCC on 2007-03-28
On ubuntu 6.10 with the sript 
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

IOn feisty trough the same script but the XGL/Beryl didn`t work this time,  DRI was made way easier trough the restricted driver (but used the script first time), the dual monitor by installing trough synaptic ATI control   and using the following command

sudo aticonfig --initial=dual-head --screen-layout=right

---

### Post by bonedog73 on 2007-03-29
> **gonesolo said:**
> 

ATi Radeon X1600 (PCIe) (512Mb)

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

Reboot.

Worked first time.

This also worked perfect for me too!!

I'm using Ubuntu **Feisty** on my AMD4600+ running an **ATI Radeon X1950 Pro PCIE Video Card**. 

Feisty didnt recognize my VC right away and I tried a few other things, then I saw this above and badda-boo-badda-bing!

Now if I can get my Creative X-FI sound card going I'd be in business.

Rock n Roll!

---

### Post by thechanklybore on 2007-04-03
8.35.5 Working perfectly on a generic X1300 in Dual-head 2560x1024 with Beryl/XGL here.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually)

I've been using the above instructions to install ATI/AMD drivers for about a year, and it's worked for across several different ATI cards/Ubuntu installs. TBH I often wonder how it can NOT work considering it builds the kernel module, but ho hum.

Anyway with the new Catalyst Control Center in 8.35.5 you'll probably find you can do ALL of your dual-head/TV setup without using aticonfig at all! Sweet!

AMD have really pulled their collective fingers out for this release.

---

### Post by japser on 2007-04-03
ATI X700 Mobility / Toshiba Satellite laptop using **AIGLX** with **Beryl**

**uname -r**
```
2.6.20-13-generic
feisty fawn
```

**lspci -n | grep 0300**
```
01:00.0 0300: 1002:5653
```

**lspci | grep VGA**
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
```

**glxgears**
```
10270 frames in 5.0 seconds = 2053.831 FPS
10693 frames in 5.0 seconds = 2138.505 FPS
10718 frames in 5.0 seconds = 2143.488 FPS
10714 frames in 5.0 seconds = 2142.666 FPS
18247 frames in 5.0 seconds = 3646.555 FPS
16417 frames in 5.0 seconds = 3283.363 FPS
23784 frames in 5.0 seconds = 4756.761 FPS
10788 frames in 5.0 seconds = 2157.515 FPS
10809 frames in 5.0 seconds = 2161.718 FPS
10687 frames in 5.0 seconds = 2137.269 FPS

**and now with beryl loaded :( **

2983 frames in 5.0 seconds = 593.128 FPS
4741 frames in 5.1 seconds = 938.157 FPS
2730 frames in 5.0 seconds = 545.993 FPS
219 frames in 5.3 seconds = 41.473 FPS
459 frames in 5.0 seconds = 91.752 FPS
1732 frames in 5.0 seconds = 346.371 FPS
3069 frames in 5.0 seconds = 611.304 FPS
215 frames in 5.0 seconds = 42.656 FPS
6240 frames in 5.0 seconds = 1247.913 FPS
9076 frames in 5.0 seconds = 1814.995 FPS
7752 frames in 5.0 seconds = 1542.878 FPS
8202 frames in 5.0 seconds = 1640.198 FPS
11503 frames in 5.0 seconds = 2300.514 FPS
9304 frames in 5.0 seconds = 1860.652 FPS
10530 frames in 5.0 seconds = 2105.965 FPS
```

---

### Post by eluzi on 2007-04-05
After a lot of work, I managed to get my ATI Radeon X1300 Pro to work under Ubuntu, and also got XGL + Beryl working perfectly, the steps taken were those under this thread:

[http://ubuntuforums.org/showthread.php?t=291464](http://ubuntuforums.org/showthread.php?t=291464)

  Any further questions, fell free :D

---

### Post by jonberling on 2007-04-07
> **gerbman said:**
> Card: Radeon 9500 Pro
Guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Tweaks: none needed, even for dual screen

This method worked like a charm. Never had my ATI X700 work so well with linux.

---

### Post by thinketch on 2007-04-16
lspci -n | grep 0300
0000:00:10.0 0300: 1002:5046
lspci | grep 0300
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

Debian Etch PPC on a Mac G4.
In order to get a working 1440x900 with my Samsung Syncmaster 906bw I posted the xorg.conf on this page:

[http://ubuntuforums.org/showthread.php?p=2461040#post2461040](http://ubuntuforums.org/showthread.php?p=2461040#post2461040)

It is working great now. before xorg was chopping off the bottom half inch of the screen and the text looked too thin.

Cheers Ubuntu!

---

### Post by surfjdh on 2007-04-17
1)0000:01:00.0 0300: 1002:5964 (rev 01)
2)ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
3)using xorg-edit, make sure driver is set to Ati, check all x server settings, make sure they match your usage..., ( link-http://sourceforge.net/project/showfiles.php?group_id=169700 )
4)enjoy

---

### Post by siloh on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				1) 01:00.0 0300: 1002:554d

2) Sapphire RADEON X800 XL (AGP)
seen as "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)" under lspci

3) AGP card was not detected by agpgart (see bug 78684)

As a soft workaround, blacklisting the EDAC modules has worked perfectly.
=> add the following two lines at the beginning of /etc/modprobe.d/blacklist:
blacklist i82875p_edac
blacklist edac_mc

And now desktop effects (wobbly+cube) work like a charm with the open source RADEON driver.

---

### Post by RichardM33 on 2007-04-20
I use Dapper on a dual processor motherboard. I was using an old SIS rev305 card which was the only one which would boot with the Live CD. I purchased a used ATI Radion 9200SE to provide more video ram.

First I downloaded the ATI driver using Synaptic. Highlight the driver to see a list the cards supported in the description.

Then I ran the aticonfig utility using the following:

          aticonfig  --initial --/etc/X11/xorg.conf  (run aticonfig w/o parameters to see options)

BTW, aticonfig makes a backup xorg.conf automatically.

Shutdown, install ATI card and reboot. Life is good. Good luck.

---

### Post by ph0neman on 2007-04-23
i was at my wits end with this dell e1505 duo core w/ x1300 mobility.   first it was the wireless broadcom card i struggled with and then it was the video card!!!!

i could not get beryl to work with it.  i tried every tutorial i could find and had a different error with each one.  

i ended up stumbling over an article discussing [[COLOR="Red"]_[SIZE="6"]envy[/SIZE]_[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html") and i picked the ATI configuration and installation option allowing it to auto configure my card.  well to my surprise it worked.  

 i really was rather disappointed that i couldnt get it to work but at this point... i am just glad its working.  beryl is pretty cool... sort of buggy but its fun to play with (its a nice addition to to OS)

thanks to everyone that took the time to post suggestions and what worked for them.  this what makes the linux community so great, the willingness to share and pitch in to help others.

---

### Post by greymongrey on 2007-04-23
> **thechanklybore said:**
> 8.35.5 Working perfectly on a generic X1300 in Dual-head 2560x1024 with Beryl/XGL here.


Same here but I used Envy.

---

### Post by m1 grant on 2007-04-24
Mobility X1600 on my W3J is working well as far as I can tell

---

### Post by ijn on 2007-04-27
adi@ubuntu:~$ lspci -n | grep 0300
01:00.0 0300: 1002:7149
adi@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [ATI Mobility Radeon X1300]
adi@ubuntu:~$   
changed xorg.conf (after I tried, "disable" and "0") in "false". it did't workd after reboot. so I type sudo dpkg from tty in recovery mode boot, and reconfigure my X. choose FGLRX 5.36, and resolution 1440X900 (the right one for my dell inspiron 6400, duo2 2ghz, ati x1300, kubuntu feisty final version,  Xorg 7.2, kernel 2.6.20.15) and reboot.
it works with the right resolution,,,but no direct rendering and the output of the commands glxinfo and fglrxinfo are at this link:[http://ubuntuforums.org/showthread.php?t=424569](http://ubuntuforums.org/showthread.php?t=424569)
ciao

---

### Post by jhwilliams on 2007-04-27
> [QUOTE]8.35.5 Working perfectly on a generic X1300 in Dual-head 2560x1024 with Beryl/XGL here.
Same here but I used Envy.[/QUOTE]

Can anyone who has 2560x1024 beryl dual monitors working please post their xorg.conf ?

I have Beryl running at 2048x768 with mergedFB on an ATI Radeon 9800 Pro using the open source R300-based radeon driver. I would like to be running at 2560x1024.

Should I...

(a) Change to the proprietary drivers,
(b) Stop using MergedFB and switch to Xinerama,
(c) Both
(d) Neither; forget about the idea, cause it won't happen.

Thanks,
Jameson

---

### Post by Ferri on 2007-04-27
ATI 9200SE working with open-source driver, AIXGL+Beryl.

lspci -n | grep 0300
01:00.0 0300: 1002:5964 (rev 01)

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

I followed [_*this guide*_](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon).

---

### Post by ammu on 2007-04-30
(1).01:00.0 0300: 1002:7109
(2.)01:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800]
                    (its ati radeon X1800XL  suffered alot to get it work but atlast it was only 2 lines work no need to do anything...atleast for me its more faster and easier than in window....:lolflag: )
   ```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

after that i need to edit xorg.conf file so i type in terminal
```
sudo gedit  /etc/X11/xorg.conf
```
and add these lines at the bottom
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
        and reboot and checked and it works like charm fps are quite good ...i used ubuntu .....and now using kubuntu its hot but i got hard time to install my card but its good as its done.thanks all.

---

### Post by stchman on 2007-05-01
I have a procedure to get ATI drivers working here:

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

Radeon Xpress 200M laptop.

Or I use Envy.

---

### Post by to4i on 2007-05-08
I've just installed the Ati driver by using **Restricted Drivers Manager**.

# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: **RADEON X700**
OpenGL version string: 2.0.6334 (8.34.8 )

After I installed Feisty, downloaded newly updates, and just click on Restricted Drivers Manager -> the install went fine -> restart. And I'm happy that it was so easy, just click and run.

Great!

---

### Post by Sladi on 2007-05-08
Here's a link to my post describing how I got my card to work. :) I installed the newest Ati drivers manually according to method#2 in the wiki. 
It's an X800XL and I use two displays (LCD and CRT) @ 1280*1024.  
```
01:00.0 0300: 1002:554d
```
[Ubuntu wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

[link]("http://www.driverheaven.net/linux-radeon-display-drivers/135944-dual-monitor-faq-wiki-agp-speed-screensaver-questions.html")

---

### Post by dziki on 2007-05-09
1 - dziki@ubuntu-feisty:~$ lspci -n | grep 0300 -> 05:00.0 0300: 1002:7142
2 - dziki@ubuntu-feisty:~$ lspci | grep VGA -> 05:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
3 - no tweakings needed

works fine with fglrx driver, but not with unsupported new drivers 8.35 & 8.36. I cannot get direct rendering with these newer ones :-(

---

### Post by andrew4558 on 2007-05-09
02:00.0 0300: 1002:7142
02:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
Tried several drivers and finally this driver 8.36.5-1_i386 worked.

---

### Post by dziki on 2007-05-10
> **andrew4558 said:**
> 
Tried several drivers and finally this driver 8.36.5-1_i386 worked.

How did you get direct rendering ? Please ...:???:

---

### Post by willix on 2007-05-14
1) 01:00.0 0300: 1002:5460

2) 01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]

3) 
installed the driver
> sudo apt-get install xorg-driver-fglrx

replaced  
   Driver "ati" 
 with
   Driver "fglrx"
in xorg.conf

> sudo aticonfig --overlay-type=Xv

appended 
Section "Extensions"
        Option      "Composite" "0"
EndSection
to xorg.conf

and finally
mkdir -p /usr/X11R6/lib/modules
ln -s /usr/lib/dri /usr/X11R6/lib/modules

and that did it

---

### Post by theaceoffire on 2007-05-16
Card: ATI Radeon 9250, which is listed as an ATI Radeon 9200.

1)lspci -n | grep 0300
> 00:02.0 0300: 8086:2582 (rev 04)
02:03.0 0300: 1002:5960 (rev 01)

2)lspci | grep VGA
> 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

3) This video card CRASHES all linux OS's, including Live CD's. They Hang, without completing.
Tweaking to get it to work:
1. Change BIOS to use the onboard video instead of pci.
2. I backed up my /etc/X11/xorg.conf to /etc/X11/xorg.conf_bak
3. used sudo gedit /etc/X11/xorg.conf. I commented out my first Device, and added this:
> Section "Device"
	Identifier	"ATI Technologies Inc RV280"
	BusID		"PCI:2:3:0"
	Driver		"vesa"
EndSection

I also commented out the original driver and set it to my new one.
> Section "Screen"
	Identifier	"Default Screen"
#        Device         "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Device 		"ATI Technologies Inc RV280"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection
4. Once I made sure that my video card wouldn't CRASH my OS or Xserver, I then added in the following:
> Section "Device"
	Identifier	"ATI Technologies Inc RV280"
	BusID		"PCI:2:3:0"
#Changed to the radeon driver (Open source)
	Driver		"radeon"
#Begin Options.
	Option		"GARTSize" "64" #By default this is kinda small
        Option 		"EnablePageFlip" "true" #LargerCache?
	Option 		"ColorTiling" "on"
#End Suggested options.
	Option		"AccelMethod" "XAA" #XAA\EXA, XAA is default and most stable.
	Option          "XAANoOffscreenPixmaps" #Enables 3d
	Option		"RenderAccel" "true"
        Option 		"DisableGLXRootClipping" "true"
        Option 		"AddARGBGLXVisuals" "true"
        Option 		"AllowGLXWithComposite" "true" 
  	Option 		"AGPv3Mask" "0x00000002" #Stop Glitches supposedly
EndSection
And at the end of the ENTIRE xorg.conf, I added this:
> Section "Extensions"
        Option "Composite" "Enable"
EndSection
Later on I might try to get fglrx to work again, but it didn't work well.

---

### Post by Xzavier on 2007-05-17
00:02.0 0300: 8086:2562 (rev 01)
01:00.0 0300: 1002:5960 (rev 01)

ATI Technologies Inc RV280 (9200 Pro)

need a correct xorg.conf always crashing xserver. when it works no resolution higher then 800x600 60hz

---

### Post by jerrylamos on 2007-05-17
I think this is a pretty simple card.  For my purposes runs great.  xorg.conf says:
Section "Device"
        Identifier      "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection
It "just works".  The display is  an old "Philips 150P" LCD, 1024x768, from computer show.
Cheers, Jerry

---

### Post by eye208 on 2007-05-18
- install Ubuntu 7.04
- open restricted drivers manager
- click checkbox for accelerated ATI graphics driver
- optional: run "sudo aticonfig --ovt Xv" to enable Xvideo overlay
- reboot

Piece of cake. Edgy's default driver (8.28.8) still required turning the boot splash off and configuring "AlwaysRestartServer=true" in gdm.conf to prevent crashes. Feisty comes with version 8.34.8 which does not require those tweaks any longer. Installing the ATI driver has never been that easy.

Even better, you can now use the ATI driver in Live CD mode, including direct rendering! Follow these steps:

- boot from Ubuntu 7.04 Live CD/DVD in safe graphics mode
- open restricted drivers manager
- click checkbox for accelerated ATI graphics driver
- ignore reboot request
- optional: "sudo aticonfig --ovt Xv"
- press ctrl + alt + backspace to restart X

This is great for quick demonstrations of applications that require OpenGL 2.0 (e.g. Second Life) on systems with ATI graphics.

---

### Post by WaeV on 2007-05-22
I don't know if this should go here because I used the mesa drivers and not the proprietary drivers.  This was, however, the only way (ie. first of many tries) I could get beryl to work.

I have an All-In-Wonder 9800 Pro

I followed this tutorial:
[URL="http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon"]
http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon[/URL]

I ommitted the second part of step 3 dealing with changing priority from fglrx to the mesa drivers.
I now have no xorg.conf but I have no graphical problems and beryl is working great!:D;) *knocks on wood*

lspci -n | grep 0300
```
01:00.0 0300: 1002:4e48
```

lspci | grep VGA
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
```

PS I now have insanely high resolution.  On fglrx I only got up to 1280 x 1024 but now I have up to 1680 x 1050!!!

---

### Post by moljac024 on 2007-05-22
04:00.0 0300: 1002:5b63

04:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]

I did nothing. Installed Ubuntu 7.04, installed beryl and it worked straight away!

Is this a good thing ?

---

### Post by eye208 on 2007-05-23
> **moljac024 said:**
> I did nothing. Installed Ubuntu 7.04, installed beryl and it worked straight away!

Is this a good thing ?
You are not using the proprietary ATI driver but the OSS driver. It's fine for Beryl but too slow for games.

---

### Post by captainskyhawk on 2007-05-28
1) 01:00.0 0300: 1002:5e4b

2) 01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]

3) No tweaking needed, just installed Restricted Drivers using the manager.  Can run World of Warcraft just fine and can run Beryl with XGL.

---

### Post by Alex Fernandez on 2007-06-01
Radeon XPress 200m (which the same as x300 or 1100 IGP)


Medthod 1 - apt repos drivers (not latest)

1) Use apt to install the needed stuff:

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx

Method 2 - latest drivers from ATI site

1) Download driver from ATI Site

sudo gedit /etc/default/linux-restricted-modules-common
 -- Add fglrx to the restricted list

bash <the ati.run file name> --buildpkg Ubuntu/feisty

sudo dpkg -i *.deb

sudo rm -fr /usr/src/fglrx-kernel*.deb

sudo apt-get -f install

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -ae


THEN FOR BOTH METHODS - do this:

2) Use the aticonfig

sudo aticonfig --initial 
// N.B. You can just edit xorg.conf and change the driver under "Device" from ati to fglrx
sudo aticonfig --overlay-type=Xv

3) Add these 2 things to xorg.conf (in /etc/X11/):

Section "Extensions"
        Option      "Composite" "0"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

4) Reboot / Restart X (CTRL + Alt + Backspace)

And it all works :)

alex@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

Ubuntu 7.04 32bit

---

### Post by mjukr on 2007-06-04
ATI Radeon 9800 w/ 128MB RAM

I'm just using the free "ati" drivers (*not* the restricted drivers) and it works fine, even with Beryl!

---

### Post by mrwasabi on 2007-06-07
I simply installed the restricted driver in the repo and it worked for me.
ATI Radeon X850XT AGP

lspci -n | grep 0300
01:00.0 0300: 1002:4b49

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT]

glrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT
OpenGL version string: 2.0.6334 (8.34.8)


54310 frames in 5.0 seconds = 10861.815 FPS
54297 frames in 5.0 seconds = 10859.220 FPS
54308 frames in 5.0 seconds = 10861.585 FPS
54309 frames in 5.0 seconds = 10861.685 FPS
54300 frames in 5.0 seconds = 10859.982 FPS
54305 frames in 5.0 seconds = 10860.907 FPS
54010 frames in 5.0 seconds = 10801.918 FPS

===========EDIT======================
9.15.07
Ok guys, I recently installed the Beryl desktop without any problem at all, it runs super! However my frame rates have been cut in half!!!! As you can see above I had booming FPS, now with the new setup running Beryl my FPS are 5200FPS give or take. Is there  way to correct this or do I have to live with it? Also the tutorial I used for Beryl is here:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

TIA
Rich

Rich

---

### Post by kelvin spratt on 2007-06-07
Absolutely nothing was needed to make my card work

---

### Post by birdsixone on 2007-06-09
Great Tutorial! Now my card is working perfectly.

---

### Post by mwacky on 2007-06-13
1.) 01:05.0 0300: 1002:5955
2.) 01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
3.) I followed a howto to get it working with Beryl for Edgy: [http://ubuntuforums.org/showthread.php?t=321766]("http://ubuntuforums.org/showthread.php?t=321766")
Then when I updated to Feisty, I followed this using Envy, which was able to handle a kernel update, something I couldn't figure out with Beryl: [http://untuforums.org/showthread.php?t=432554&highlight=ATI+Envy]("http://ubuntuforums.org/showthread.php?t=432554&highlight=ATI+Envy")

---

### Post by netmeteor on 2007-06-21
01:00.0 0300: 1002:4e50

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

no tweaking

---

### Post by arugge on 2007-06-21
followed the tutorial. But i still can't get anything to work in Festy. It says i have a ATI Radeon Xpress 200M but every time i try to enable desktop effects i get a message saying "The Composite Extension is Not available". Any suggestions? I can load beryl as well but i get no effects. 

I'm a fairly newb Ubuntu user and these ATI Drivers are getting old though. On my desktop the Nvidia card i have runs great. But this latop is less then  year old so i have no plans to get rid of it anytime soon.

---

### Post by stevespam on 2007-06-26
ACER Notebook Aspire 5050-3233
Amd Turion 2.0ghz with 1GB Ram
Ubuntu Feisty Fawn 7.04 - Kernel: 2.6.20-16

```

lspci -n | grep 0300
01:05.0 0300: 1002:5975

```

Although my notebook specs says: ATI Radeon Xpress 1100, the grep VGA returns me this model:

```

lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

```

I presume my videocard has just worked Out of The Box, but to get some "cool video features", i had to follow this quite simple tutorial: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy) (which includes installing the restricted driver in the repository).

Right now, BERYL runs pretty fine on my notebook, with all the effects and no "lag" at all. I guess, i did all right and my video card does support 3D.

By the way, I'm using FGLRX:

```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

```

Good Luck all!

---

### Post by rjz35 on 2007-06-27
rjz@D610:~$ lspci -n | grep 0300
01:00.0 0300: 1002:5460
rjz@D610:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]

aixgl + Beryl + Ati driver

xorg.conf
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option 		"ColorTiling" "on" 
	Option 		"AccelMethod" "XAA"  #changed from "EXA"
	Option 		"XAANoOffscreenPixmaps" #changed from EXANoOffScreenPixmaps

tweaked a bit but more or less out of the box, don't know were i found it

---

### Post by Melcar on 2007-07-05
200M.  I can install the drivers using the "Ubuntu way" (driver from the repos) and everything works fine, but dammit, I want to compile my own drivers :p.  I was always able to perform the latter (Edgy and previous versions) by simply following the wiki, but all that has changed with Feisty for some reason.  
Everything goes fine until I try to configure the driver.  Aticonfig corrupts my xorg.conf file for some reason, forcing me to reconfigure it  and fall back to my back ups.  It does it all the time.  I need to know how to manually configure the driver without the use of aticonfig.

---

### Post by Melcar on 2007-07-05
> 
Instructions for 7.04 (Feisty)
Preparation

Although it is possible to use the instructions for 6.10 on 7.04, there is a simpler and possibly more painless way to install of 7.04. First, download the drivers installer (not the rpms) from [WWW] ati.amd.com. It is recommended to save it to an empty directory since the installer will create a bunch of files. Next, in order to build the packages, we need some basic developer tools. To get these tools, first enable the universe and restricted sections of Ubuntu (see AddingRepositoriesHowto for help). Once the repositories are enabled, install the needed developer tools with sudo apt-get install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-generic
Installation

Build Ubuntu packages from the installer by opening a terminal, entering the directory that you saved the installer to, and running bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/feisty

where <version> is the version number of the driver you downloaded. This will take a short time. After finishing, the installer will create several debs. Use the command "dpkg -i <filename>" to install the fglrx-kernel-source<something>.deb and the xorg-driver-fglrx<something>.deb. The other two debs created will be fglrx development headers which you probably will not need and the AMD Control Panel which doesn't work.

After installing the kernel source and xorg driver, you will now need to compile the fglrx kernel module in order to get 3-d rendering. Do so with the following commands:

sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb

Configuration

Ubuntu 7.04 ships with a utility to automate configuration of fglrx. Open it at "System -> Administration -> Restricted Drivers Manager" (you may have to install the restricted-manager and linux-restricted-modules-generic package). Select "ATI accelerated graphics driver" and hit apply. The Restricted Drivers Manager will then automagically change xorg.conf and several other files. However, even at this point, the setup is not finished. At next boot, Ubuntu will load an old version of fglrx, so you have to blacklist it by changing /etc/default/linux-restricted-modules-common to include DISABLED_MODULES="somemodule2 fglrx" where somemodule2 is the old contents of that line. When you have finished this last change, reboot and (hopefully) enjoy your 3-d acceleration. 



That's what I followed and finally got the latest driver (8.38.6 ) working.  Basically, instead of using aticonfig manually I used the restricted-drivers thingy.

---

### Post by mightyteegar on 2007-07-06
[COLOR=Silver]Running Feisty here.  I used the 8.38.6 fglrx driver from [ATI's website]("http://ati.amd.com").  I have a Dell Dimension 9150 with a PCI Express Radeon X300 128 MB video card.   I wanted the ATI drivers because unlike some others in our fine community, I prefer to get my drivers from manufacturers over independent community-driven drivers whenever possible, proprietary or otherwise.

Background: I had been trying for days to get ATI's drivers to install and load consistently.  Sometimes I'd get the right driver with 3D acceleration and all that, but most of the time I kept getting the dreaded "Mesa" output from fglrxinfo.  Often I swore my machine was choosing a driver at random based on its whims and feelings that moment.  

What I finally realized was that despite what every tutorial I read told me, I didn't need linux-restricted modules-* (common, generic, whatever).  They always got in the way, and besides, I'm running an external driver -- why do I need restricted modules from the repositories?  

Here is what I did to get it working.  

1.  First thing I did was start from scratch.  Uninstalled every possible trace of fglrx. 
2.  Uninstalled linux-restricted-modules-*.  
3.  Compiled the ATI driver using the method outlined under the section "Install from ati.com (latest drivers)" from the [Ubuntu BinaryDriverHowTo-ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").
4.  Edited /etc/modules to load agpgart and fglrx on boot.  
5.  Edited /etc/modprobe.d/lrm-video and commented out this line: 
```
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
```**NOTE:*** you should be able to get away with removing /etc/modprobe.d/lrm-video permanently after you uninstall linux-restricted-modules-*.  The "lrm" stands for... this should be obvious... "linux-restricted-modules".  In fact, /sbin/lrm-video ceases to exist once you uninstall LRM*.*

After doing all this I rebooted X five times (Ctrl-Alt-Backspace) and soft-rebooted three times, logged into GNOME, fluxbox and KDE and then ran fglrxinfo from a virtual console in each one.  All eight times I got what I wanted: 

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6474 (8.38.6)

```**Note that uninstalling LRM* and installing the ATI driver may cause Ubuntu's Restricted Hardware Manager to complain at you about needing software.  Guess what package it wants to install.  I simply ignored its "warning" and upon reboot the warning did not come back.  It has not been seen since.**

As I mentioned before, my biggest problem was making the ATI driver "stick."  Mesa kept popping up and making me angry.  This is the ONLY method I have tried thus far that works 100% of the time for me (so far; all these reboots were done yesterday, so my fingers are still crossed).

[COLOR=Red]**UPDATE: Mesa returned yesterday and today, much to my dismay.  I also tried completely removing the proprietary driver and installing from the repo; no luck.  I still get "DRI initialization errors" in /var/log/Xorg.0.log.  **[/COLOR]
[/COLOR]

---

### Post by Manasia on 2007-07-07
I am at my wit ends with Ubuntu Studio (FF 7.04) Let me give some background.

I am a filmmaker who converted to Cinerella because Premiere and FCP suck. I successfully installed Ubuntu Studio on my old laptop a Sony Vaio and everything worked perfectly. 

However, I am now trying to install Cinerella on an AMD Duron, using an ATI RAdeon 9250. Has any successfully gotten the 9250 to work with Studio or FF 7.04?

---

### Post by 6StringKng on 2007-07-16
1) 02:00.0 0300: 1002:4e51

2) 02:00.0 VGA compatible controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600]

3) No tweaking needed (it works with direct rendering with the driver which comes by default with Ubuntu)

---

### Post by Chonnawonga on 2007-07-18
I'm using the Asus K8N motherboard, an ATI Radeon 9600, and a Samsung Syncmaster 931BW. I know other people have had to flash their BIOS down to the 1006 version to get the fglrx driver working, but just for the heck of it, I tried flashing to 1011, and it works just fine! No more mesa crap on fglrxinfo. Aticonfig took care of all my xorg.conf issues.
:)

---

### Post by Canesfan2020 on 2007-07-19
Radeon X700 Pro..installed using Envy..agpgart is not working..no clue why.. reports mode as 0x.

---

### Post by DaH-RaT on 2007-07-21
9800 pro :)
i followed these guides together.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

[http://ubuntuforums.org/showthread.php?t=461209&highlight=9800+pro](http://ubuntuforums.org/showthread.php?t=461209&highlight=9800+pro)

---

### Post by bnderan on 2007-07-22
I'm running Ubuntu 7.04. 
My PC is a Shuttle SB75G2 with an ATI X800PRO card.
It's hooked up to a Dell 2405FPW monitor, via a DVI cable.
I used the official ATI driver, version 8.38.7-x86.

I followed the instructions at: 
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")
Method 1 didn't work for me.
Method 2 worked great, but is a bit scary to follow.

I also had to run the troubleshooting tips for "No 3D acceleration" at:
[http://wiki.cchtml.com/index.php/Troubleshooting#No_3D_acceleration]("http://wiki.cchtml.com/index.php/Troubleshooting#No_3D_acceleration")

fglrxinfo now reports: 
[INDENT][B] display: :0.0  screen: 0
 OpenGL vendor string: ATI Technologies Inc.
 OpenGL renderer string: RADEON X800 PRO
 OpenGL version string: 2.0.6474 (8.38.7)[/B][/INDENT]

glxgears reports: **7263 FPS**

Attached is my xorg.conf file. In the futile hope, that future generations will not suffer the agony of configuring X and fglrx. 

Last note, I set the gamma real low in my config file, because my Dell monitor is like a miniature Sun.

---

### Post by BOK on 2007-07-24
I used the script from the Kantonix-distribution [located here]("http://kanotix.com/files/install-fglrx-debian.sh"), changed the word "edgy" on line 321 to "feisty", made it executable and ran it as root.
Had to unload "fglrx" (rmmod fglrx) by hand and restart GDM, but it has never ever been easier for me like this! \\:D/
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6650 (8.39.4)
```

FYI - glxgears reported a max frames of 2193.762 FPS, fgl_glxgears 402.200 FPS.

---

### Post by Palmstroem on 2007-07-27
```
$ lspci -n | grep 0300
04:00.0 0300: 1002:7146
$ lspci | grep VGA
04:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 2.0.6650 (8.39.4)
```

Followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"), method 2. Method 1 did not work. System: Dual AMD Opteron, 64bit Feisty.

---

### Post by Rmantingh on 2007-08-01
$ lspci -n | grep 0300
03:00.0 0300: 1002:5b60

$ lspci | grep VGA
03:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6650 (8.39.4)

Like palmstroem I used his instructions, however before I started I removed ALL references
to existing fglrx and ati files on my system (uninstalling and even rm-ing remaining files).
I then reverted back to a default VESA driver in my xorg.conf and rebooted the system before I began.
Only then was I able to install the ATI driver the manual way.

---

### Post by paulatreides on 2007-08-20
$ lspci -n | grep 0300
01:05.0 0300: 1002:5954

$lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6747 (8.40.4)

$glxinfo | grep "direct rendering"
direct rendering: Yes

$cat cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"



i used both envy and allow some gutsy depôts to be able to use the ATI driver with kernel 2.6.22-9. it seem to work fine except this: (from Xorg.0.log)

	erreur	fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7


other info from dmesg

$dmesg | grep fglrx
[   90.850244] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   90.854253] [fglrx] Maximum main memory to use for locked dma buffers: 865 MBytes.
[   90.854260] [fglrx] USWC is disabled in module parameters
[   90.854265] [fglrx] PAT is disabled!
[   90.854989] [fglrx] module loaded - fglrx 8.40.4 [Jul 31 2007] on minor 0
[   70.460000] [fglrx] total      GART = 130023424
[   70.460000] [fglrx] free       GART = 114032640
[   70.460000] [fglrx] max single GART = 114032640
[   70.460000] [fglrx] total      LFB  = 67108864
[   70.460000] [fglrx] free       LFB  = 17551360
[   70.460000] [fglrx] max single LFB  = 17551360
[   70.460000] [fglrx] total      Inv  = 0
[   70.460000] [fglrx] free       Inv  = 0
[   70.460000] [fglrx] max single Inv  = 0
[   70.460000] [fglrx] total      TIM  = 0

(sorry if my english is bad, i am not:lolflag:)

---

### Post by MrChips on 2007-08-22
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The guide from the first post was a snap with my  X1600 Radeon.

$ lspci -n | grep 0300
05:00.0 0300: 1002:71c2

$ lspci | grep VGA
05:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)



Horizontal desktop and all!

After trying a few other distros with such utter failure with the ATI drivers I couldn't believe how easy it was.  *whew*

3700 fps with glxgears in Ubuntu as compared to 500 to 600 with others.

---

### Post by soxs on 2007-08-25
> **Palmstroem said:**
> ```
$ lspci -n | grep 0300
04:00.0 0300: 1002:7146
$ lspci | grep VGA
04:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 2.0.6650 (8.39.4)
```

Followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"), method 2. Method 1 did not work. System: Dual AMD Opteron, 64bit Feisty.

Did you do that on a fresh install of feisty or did you have any drivers installed before?
Edit: Method 1 didn't work for me.
Edit: Method 2 didn't work either.
Edit: **[COLOR="DarkGreen"]Envy works like a charm![/COLOR]** ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

---

### Post by Lapeth on 2007-08-26
I had to compile the kernel module for my ATI Radeon 9600 myself, because apparently the kernel module supplied in the repos won't work... :-k

Anyways, here's my info after I got it working:
```
$ lspci -n | grep 0300
01:00.0 0300: 1002:4e50
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)
```

Install from repos:
xorg-driver-fglrx
xorg-driver-fglrx-dev (not sure it's necessary)
fglrx-kernel-source

Now for the compiling stuff...

fglrx-kernel-source gave me this file:
/usr/src/fglrx-kernel-source.tar.gz

Unpack in /lib/modules. Make sure you put the folder called fglrx in /lib/modules, or a symlink to it.
Go to the build_mod folder (/lib/modules/fglrx/build_mod) and run

./make.sh verbose

If you get an error about "version-*.h" not found, open the make script (/lib/modules/fglrx/build_mod/make.sh) and edit line 225 from

```
    UTS_REL_COUNT=`cat $linuxincludes/linux/version-*.h | grep UTS_RELEASE -c`
```

to

```
    UTS_REL_COUNT=`cat $linuxincludes/linux/version.h | grep UTS_RELEASE -c`
```

Also, if you get the error "Error: could not resolve matching ip-library.", as I did, it's because LIBIP_PREFIX as default has been set to "." (current folder, see line 152 in make.sh). Set it manually:

$ export LIBIP_PREFIX="/lib/linux-restricted-modules/2.6.20-16-generic/fglrx"

If you get some other errors, try to look into the make script and see where it fails.

At some point the compilation should be successful. Go one folder up and run make_install.sh

And of course have the standard stuff set in your /etc/X11/xorg.conf, like
```

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
	Option  "AIGLX" "Disable"
EndSection
```

Should be good to go now.

---

### Post by CarpmanVPTR on 2007-08-27
ATI 9800 XT
Asus p4c800-e Deluxe

This board has an intel chipset. I was pulling my hair out trying to get Direct Rendering running. As it turns out, the module i82875p_edac was preventing intel_agp from starting up correctly. Once I blacklisted it and edac_mc, fglrx bound to intel_agp and the rest is history.

---

### Post by streetsurfer on 2007-09-01
anyone able to get the x1600 pro to have TV-OUT?

---

### Post by grimmson on 2007-09-02
thanks again Mr. Elliot. You've made my ati life easier again. Envy 0.9.7 worked with a clean, updated feisty install on a toshiba satellite m115 w/o any tweaks. Muchos grassyass again. (Sure wish I was a wiz kid.)

---

### Post by newman on 2007-09-02
** Post the way you got the ATI driver to work **

I installed Windows!

---

### Post by phreadom on 2007-09-03
> **Canesfan2020 said:**
> Radeon X700 Pro..installed using Envy..agpgart is not working..no clue why.. reports mode as 0x.

I have DRI working etc... but same problem with the AGP bus reporting 0x speed, so performance is still very poor.

Radeon x1600pro 512mb.

I'd really like a solution to the 0x AGP problem, which appears to be affecting a number of people for the last few kernel/xorg revisions. :(

largo@rom:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]

largo@rom:~$ lspci -n
01:00.0 0300: 1002:71c2
01:00.1 0380: 1002:71e2

largo@rom:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6747 (8.40.4)

largo@rom:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6747 (8.40.4)

largo@rom:~$ glxgears
6633 frames in 5.0 seconds = 1326.454 FPS
5793 frames in 5.0 seconds = 1158.485 FPS
6291 frames in 5.0 seconds = 1258.169 FPS
6279 frames in 5.0 seconds = 1255.651 FPS
6287 frames in 5.0 seconds = 1257.397 FPS

That speed should be like 10x as fast. :(

the ATI drivers are reporting a 0x AGP speed that seems to be the cause of the terrible 3d performance.

---

### Post by phreadom on 2007-09-03
I've found out some more information on this.

The ATI Radeon x1### series AGP cards use a PCI-E engine with an internal PCI-E to AGP bridge in order to use the AGP interface on the
motherboard.

It appears that the fglrx driver is detecting the card as a PCI-E card and incorrectly initializing it, thus resulting in the AGP 0x
bus speed being set and the performance being absolutely horrid.

Not to mention that in my case, I have the Radeon X1600Pro 512mb card, but the drivers are only detecting half of my video RAM. :(

(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.40.4
        ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)

(--) PCI:*(1:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xc0000000/28, 0xd1000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xd1010000/16

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.40.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.402
(II) ATI Proprietary Linux Driver Build Date: Jul 31 2007 22:20:14

(--) Chipset Supported AMD Graphics Processor (0x71C2) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed

(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1600 Series" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x030b)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xd1000000
(==) fglrx(0): ROM-BIOS at 0x000c0000

(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.40.4
        ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): _VideoRAM: 262144 kByte, Type: DDR2_
(II) fglrx(0): **PCIE card detected**
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)

---

### Post by WA_Mozart on 2007-09-05
01:00.0 0300: 1002:5960 (rev 01)
ATI Technologies Inc RV280 [Radeon 9200 PRO]

I have an AM2NF3 Asrock motherboard with nForce3 chipset and discovered I couldn't get AGP to work on Linux after a cold boot. Only after rebooting from Windows XP my 3D was recognized. I updated to the most recent BIOS version and my problem was fixed.

You have this bug when you do a dmesg | grep agp and get
    agpgart: Detected AGP bridge 0
    agpgart: Setting up Nforce3 AGP.
    agpgart: aperture base > 4G

This bug is described in 
[http://wiki.archlinux.org/index.php/ATI_Radeon_&_Kernel_2.6]("http://wiki.archlinux.org/index.php/ATI_Radeon_&_Kernel_2.6")

I then used this link
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
to configure xorg.conf and to get Beryl working.

---

### Post by darkpark on 2007-09-05
Have you tried to manually set the speed of the AGP  bus to 8x?   My gigabyte motherboard has that options whose defaults was auto.   Once I set it to 8x than I at least got the fglrx driver to load, although DRI won't load.   Still, it's better than the blank screen I was getting previously.    Anyway, manually setting the agp bus to 8x might help you.

my specs:
sapphire X1950Pro AGP 512MB
Gigabyte K8NSC-939 nforce3 250 chipset
AMD Athlon X2 64 4400+

Here's the interesting part of my Xorg.0.log:

```

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7cdb000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

---

### Post by keskew on 2007-09-06
1) 01:05.0 0300: 1002:5955

2) 01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

3) I followed the instructions at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Yellow Pasque on 2007-09-16
I wrestled with my box all weekend after I tried to install the latest ATI driver and had it destroy my setup(Gutsy64 Tribe4). So I bit the bullet and did a fresh reinstall, but still couldn't get my onboard video (X1250 via AMD 690G chipset) working.

I did manage to get my old X300SE add-in card working, but that one doesn't have AVIVO or DVI output and I didn't want to compromise. After a lot of attempts at editing xorg.conf, I realized my kernel was still referring to the video card as "Generic video card". I went out to the shell and ran 'lspci', and it greeted me with a lot of unknown devices or generic names.

This was the command that finally fixed my problem.:
```
sudo update-pciids
```

After that, I reinstalled ATI's 8.40.4 driver package, rebooted, and prayed.

---

### Post by mjpolifka on 2007-09-18
1) 01:00.0 0300: 1002:71c1 (rev 9e)
2) ATI Radeon X1650 PRO... lspci says ATI...unknown  device 71c1, but it doesn't seem to affect anything
3) I installed by running the binaries I dled from ATI on a fresh install, deselecting the catalyst (I have no idea if this affects anything, just saying what I did) and then running aticonfig --initial --force.  I then rebooted and everything worked perfectly, fglrx running, direct rendering on, 1500FPS from glxgears

---

### Post by CulleyS on 2007-09-26
05:00.0 0300: 1002:554d
05:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)

Feisty Fawn 7.04 x86_64

I tried several methods.  AIGLX how to's, fglrx how to's, using the Synaptic Package Manager, and finally this is what worked best.

Uninstalled xorg-fglrx within Synaptic.

Downloaded binaries from ATI Linux Propietary driver page.  As of 13 Aug 2007, current version was ati-driver-installer-8.40.4-x86.x86_64.run.

Ran *sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run* from terminal prompt.

Followed auto-install instructions, rebooted.

*Update

By doing this method, I was given an ATI Catalyst Control Center like I was used to from Windows.  This allowed me to run dual monitors without configuring xorg.conf.  *However, I am looking into switching gfx cards at this point for the following reasons:

1. At this time, ATI does not support resolution higher than 1280x800 for Linux.
2. At this time, ATI does not support indepependent resolutions for dual monitors for Linux.

One of my monitors is a 20" LCD, the other is my TV, a 42" Plasma TV.  In Windows, I run my 20" LCD at 1600x1200@60 and my Plasma at 1900x1080.  

When running at a resolution of 1600x1200, I notice a lot of double-imaging and flickering.  At 1900x1080, video flickers and jumps.  It's not horrible, but isn't watchable by my standards.  Much better for me to boot into Windows and run dual monitors that way.  Not what I want to do, but will continue to do things this way until I can get Ubuntu to work for me.

I believe I will switch back to either the AIGLX or FGLRX driver for the time being.  While I couldn't figure out dual monitors, I was able to run at 1600x1200@60 with little trouble.

---

### Post by Dubbayoo on 2007-09-30
I used Envy 0.9.7-11 after using Envy 0.9.7-6 had failed. 

1. 
steve@ubu:~$ lspci -n | grep 0300
01:00.0 0300: 1002:7142

2.
ATI Radeon X1300 PRO 256MB AGP 8x

3. 
no tweaking

---

### Post by Lulu58e2 on 2007-10-16
Sapphire HD2600XT :)

1) me@puter:~$ lspci -n | grep 0300
   01:00.0 0300: 1002:9588

2) me@puter:~$ lspci | grep VGA
   01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9588

3) No tweaking needed! :) 

me@puter:~$ glxgears
33718 frames in 5.0 seconds = 6743.443 FPS
33797 frames in 5.0 seconds = 6759.285 FPS
33801 frames in 5.0 seconds = 6760.166 FPS
33795 frames in 5.0 seconds = 6758.937 FPS
33800 frames in 5.0 seconds = 6759.916 FPS
33799 frames in 5.0 seconds = 6759.789 FPS

me@puter:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.0.6849 Release

Followed the tutorial at [http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843) and it worked even after I'd messed around a bit

Lulu

---

### Post by PGHammer on 2007-10-19
> **CulleyS said:**
> 05:00.0 0300: 1002:554d
05:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)

Feisty Fawn 7.04 x86_64

I tried several methods.  AIGLX how to's, fglrx how to's, using the Synaptic Package Manager, and finally this is what worked best.

Uninstalled xorg-fglrx within Synaptic.

Downloaded binaries from ATI Linux Propietary driver page.  As of 13 Aug 2007, current version was ati-driver-installer-8.40.4-x86.x86_64.run.

Ran *sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run* from terminal prompt.

Followed auto-install instructions, rebooted.

*Update

By doing this method, I was given an ATI Catalyst Control Center like I was used to from Windows.  This allowed me to run dual monitors without configuring xorg.conf.  *However, I am looking into switching gfx cards at this point for the following reasons:

1. At this time, ATI does not support resolution higher than 1280x800 for Linux.
2. At this time, ATI does not support indepependent resolutions for dual monitors for Linux.

One of my monitors is a 20" LCD, the other is my TV, a 42" Plasma TV.  In Windows, I run my 20" LCD at 1600x1200@60 and my Plasma at 1900x1080.  

When running at a resolution of 1600x1200, I notice a lot of double-imaging and flickering.  At 1900x1080, video flickers and jumps.  It's not horrible, but isn't watchable by my standards.  Much better for me to boot into Windows and run dual monitors that way.  Not what I want to do, but will continue to do things this way until I can get Ubuntu to work for me.

I believe I will switch back to either the AIGLX or FGLRX driver for the time being.  While I couldn't figure out dual monitors, I was able to run at 1600x1200@60 with little trouble.
In my case, I did things a bit differently (7.10 Feisty Fawn via Wubi; however, this method is by-the-book and should therefore work for any Wubi-driven install).

I am using the FGLRX driver available from the FF restricted libraries (it's also available via either apt-get or Synaptic; though I downloaded it via Synaptic, I installed it via apt-get).  Instead of rebooting the system, I simply restarted X (Ctrl+Alt+Backspace).  DRI Success!

Graphics card: ATI Radeon X1650 PRO 512 MB AGP (while manufactured and branded by ATI, it's sold by Visiontek Products, LLC)

Unusual surprise: I normally run at 1280x1024 (my 17" CRT's tallest non-interlaced resolution); glxgears doesn't change speeds a whit, regardless of how much I scale the window.  Freaky.

---

### Post by PGHammer on 2007-10-19
> **CulleyS said:**
> 05:00.0 0300: 1002:554d
05:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)

Feisty Fawn 7.04 x86_64

I tried several methods.  AIGLX how to's, fglrx how to's, using the Synaptic Package Manager, and finally this is what worked best.

Uninstalled xorg-fglrx within Synaptic.

Downloaded binaries from ATI Linux Propietary driver page.  As of 13 Aug 2007, current version was ati-driver-installer-8.40.4-x86.x86_64.run.

Ran *sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run* from terminal prompt.

Followed auto-install instructions, rebooted.

*Update

By doing this method, I was given an ATI Catalyst Control Center like I was used to from Windows.  This allowed me to run dual monitors without configuring xorg.conf.  *However, I am looking into switching gfx cards at this point for the following reasons:

1. At this time, ATI does not support resolution higher than 1280x800 for Linux.
2. At this time, ATI does not support indepependent resolutions for dual monitors for Linux.

One of my monitors is a 20" LCD, the other is my TV, a 42" Plasma TV.  In Windows, I run my 20" LCD at 1600x1200@60 and my Plasma at 1900x1080.  

When running at a resolution of 1600x1200, I notice a lot of double-imaging and flickering.  At 1900x1080, video flickers and jumps.  It's not horrible, but isn't watchable by my standards.  Much better for me to boot into Windows and run dual monitors that way.  Not what I want to do, but will continue to do things this way until I can get Ubuntu to work for me.

I believe I will switch back to either the AIGLX or FGLRX driver for the time being.  While I couldn't figure out dual monitors, I was able to run at 1600x1200@60 with little trouble.

No support for higher than 1280x800?  Don't tell my CRT that (which runs at 1280x1024, it's tallest NI resolution), and I'm using the ATI FGLRX driver avilable for Feisty x86 (7.04).  It's also as sharp as a tack.

---

### Post by remonzo on 2007-10-27
Hello all! The following quoted [COLOR="Red"]**[BOK]("http://ubuntuforums.org/showpost.php?p=3074730&postcount=220") **[/COLOR]tip worked \\:D/ also For me: 

> **BOK said:**
> I used the script from the Kantonix-distribution [located here]("http://bok.xs4all.nl/weblog/go.php?http://kanotix.com/files/install-fglrx-debian.sh"), changed the word "edgy" on line 321 to "feisty", made it executable and ran it as root.
Had to unload "fglrx" (rmmod fglrx) by hand and restart GDM, but it has never ever been easier for me like this! \\:D/
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6650 (8.39.4)
```

FYI - glxgears reported a max frames of 2193.762 FPS, fgl_glxgears 402.200 FPS.

My ATI model: 
```
$lspci -n | grep 0300
01:00.0 0300: 1002:4150
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
```

differences from what BOK did: 
 - changed the word from "edgy" to "gutsy" on line 321
 - run the script as root from tty1 (ctrl+alt+F1) and with gdm stopped (/etc/init.d/gdm stop)

Here is the result:
```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

$ glxgears
12934 frames in 5.0 seconds = 2586.602 FPS
$ fgl_glxgears
Using GLX_SGIX_pbuffer
2387 frames in 5.0 seconds = 477.400 FPS
```

[SIZE="5"]Thanks to **tseliot** for the thread and to **BOK** for the tip!=D>=D>[/SIZE]

---

### Post by Morton's Red Stapler on 2007-10-27
01:00.0 0300: 1002:5653
ATI Radion x700mobility on an Acer Trvelmate 8100 laptop
installed with the restricted drivers manager in Gusty
had to install xorg-xgl to get desktop efects working properly in ubuntu 7.10, did with the code
```
sudo apt-get install xorg-xgl
```
once that was done all worked perfectly.
note: i did a clean install of gutsy, so if you are working from n upgrade, you may to do additional configuration

---

### Post by Michael Longval on 2007-10-29
*This is a repost about this subject.  Originally I wrote this in another thread.*

System: IBM ThinkPad T41, Radeon 9000 (r250) @ 1400 x 1050, 1 Gig RAM

OS: **Ubuntu 7.10 (Gutsy Gibbon)**

X worked "Out of the box" but to get Compiz working here is what I did:


Compiz + 7.10 + ATI Radeon 9000 working! (at last)


I pulled my hair out for a day trying to get the proprietary ATI drivers (fglrx) to work.  

Simply put: (at the time of this post) the drivers from ATI **DO NOT WORK WITH THE RADEON 9000**.

My suggestion if you have a Radeon 9000 based card is **DO NOT INSTALL** the fglrx driver.  
Otherwise you will get stuck in a rut because of the OpenGL libraries (libMESA) (they are hard to remove..?)

Ok.  So after pulling my hair out for a day (I said that already)... I REINSTALLED Gutsy.

With a fresh install, it was more or less easy.

I changed xorg.conf (after reading many many posts) to this:

==== Relevant sections of xorg.conf ====

```
Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```
==== End Relevant sections of xorg.conf ====

The driver is set to "ati" and the AIGLX option is set to "true" and Depth is 24.

In THEORY that should do it. (wouldn't life be great if it was that simple)

But running compiz in a terminal window gets me: (btw do NOT run compiz as root)

doc@T41:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity

Very discouraging.... but the bad part is NOT the "Checking for Xgl: not present" as I first thought, this is normal it seems.  

The bad part is "Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed."

This it turns out is a bug in the file /usr/bin/compiz

Then after reading this thread: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519)

I tried running compiz with SKIP_CHECKS=yes 

It works, compiz runs but the screen is all garbled on the right hand side (about a quarter of the screen).
  
FINALLY the answer became: 

1: change the Default Depth in xorg.conf to 16 (big thanks to Glenn Slotte on lauchpad.net [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519/comments/16](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519/comments/16))

2: run compiz with SKIP_CHECKS=yes (ie:  $ SKIP_CHECKS=yes compiz )

3: you might want to install package Emerald + the compiz control programs (...forgot the package names...) before you run compiz


So here is the final WORKING xorg.conf file:

==== Relevant parts of xorg.conf ====

```
Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    16              
        SubSection      "Display"
                Depth   16
                Modes   "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection


```==== End relevant sections ====

I hope this helps those who are trying to get compiz to work with their r250 (radeon 9000) based systems.  I must say that I am really impressed with the Ubuntu Community here in the forums and at launchpad.net ... I was able to troll around and find a lot of usefull info that helped me finally fix my system.

Keep it comin' guys!

Michael Longval
------------------------------------
Ubuntu 7.10 on ThinkPad T41
PowerBook 15" MacOSX 10.4.9

---

### Post by Hhkmac on 2007-10-31
02:00.0 0300: 1002:7146

ATI Radeon X1300

Tried every method I could find on this, so far, 25 page forum... nothing worked until I tried ENVY.

All working fine now, but still no Compiz, very very slow when running... so gave up on it and now just settling for the fact that I got it installed ... phew!

---

### Post by wiseguyxp on 2007-10-31
> **PGHammer said:**
> In my case, I did things a bit differently (7.10 Feisty Fawn via Wubi; however, this method is by-the-book and should therefore work for any Wubi-driven install).

I am using the FGLRX driver available from the FF restricted libraries (it's also available via either apt-get or Synaptic; though I downloaded it via Synaptic, I installed it via apt-get).  Instead of rebooting the system, I simply restarted X (Ctrl+Alt+Backspace).  DRI Success!

Graphics card: ATI Radeon X1650 PRO 512 MB AGP (while manufactured and branded by ATI, it's sold by Visiontek Products, LLC)

Unusual surprise: I normally run at 1280x1024 (my 17" CRT's tallest non-interlaced resolution); glxgears doesn't change speeds a whit, regardless of how much I scale the window.  Freaky.

I am also running the exact same video card (ATI Radeon X1650 PRO 512 MB AGP), but I'm having problems with my driver.  I downloaded and installed the one that ATI had on their site, then initialized it like the aticonfig utility told me to to update xorg.conf.  The resolution is fine (I'm running 2048x1536 on a 21" CRT), but even screensavers have a really horrible framerate.  Playing any games is out of the question (which is what I want to be able to do).  Can anyone help?  In my Catalyst Control Center, it shows my Bus Speed as 0x (is this normal?).  And yes, I have tried running screensavers/games at a lower resolution and it has no effect.

update:  reinstalled drivers from ati website and it now shows 8x, but no video acceleration is apparent, games and screensavers still lag horribly

---

### Post by ubu-lemon on 2007-11-03
-

---

### Post by hendoc on 2007-11-03
hendoc@Exena:~$ lspci -n | grep 0300
01:05.0 0300: 1002:5954
ATI Radeon 200 (on board)
 After the Gutsy install, fonts were washed out with brightness coming from the left side, making it impossible to read the first few letters of any line of internet text or text documents. Go to Restricted Drivers Manager in Administration and enable the restricted ATI driver you will find there. After installation and a restart, your problem will be cured.

---

### Post by Takster on 2007-11-08
After 3 days i finally got everything working in harmony, first i uninstalled absolutely anything to do with the fglrx drivers in the synaptic manager, and i mean everything! 

then i reboot into the desktop and followed this tutorial to the letter: _[fglrx 8.42.3]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#")_ and hey presto everything is flying.

Radeon 9600 on an ASUS p4p800 motherboard, no worries now.

> 
**tak@Ubuntu:~$ glxgears**
14996 frames in 5.0 seconds = 2999.167 FPS
14971 frames in 5.0 seconds = 2994.031 FPS
16004 frames in 5.0 seconds = 3200.783 FPS
16008 frames in 5.0 seconds = 3201.584 FPS
15906 frames in 5.0 seconds = 3181.143 FPS
15866 frames in 5.0 seconds = 3173.047 FPS
16008 frames in 5.0 seconds = 3201.529 FPS
16004 frames in 5.0 seconds = 3200.737 FPS
15942 frames in 5.0 seconds = 3188.338 FPS


> 
**tak@Ubuntu:~$ fglrxinfo **
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release



> 
**tak@Ubuntu:~$ modinfo fglrx**
filename:       /lib/modules/2.6.22-14-386/misc/fglrx.ko
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany


> 
tak@Ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon



> 
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


=D>

---

### Post by tongpeng on 2007-11-08
01:00.0 0300: 1002:94c9
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c9

---

### Post by francis_sandow on 2007-11-08
Here's what I did with a Radeon X1950GT (AGP Version) and a fresh install of 7.10:

-Installed ATI Binary X.org driver from Add/Remove.
-Enabled ATI Radeon Restricted Driver from the Restricted Drivers menu.
-Rebooted.
-Installed XGL from the command line. (sudo apt-get install xorg-xgl)
-Logged Out.

When I logged back in, everything was nice and fast and unbuntu had switched me automatically to the fglrx driver, everything appears to work perfectly and 3D performance is pretty good so far though I won't really know until I install quake 3 for linux or something like that to really test the performance.

I grappled with trying to get this driver to work for hours and hours in Feisty to no avail. This was so easy, it's made me into an Ubuntu evangelist.

---

### Post by criskat777 on 2007-11-08
> **bluntu said:**
> I gave up on ATI Radeon 9000 Pro so I went out and purchased "ATI Radeon X1300"

I installed Ubuntu and then without updating anything I restarted the comp and entered Recovery mode and did this:

-----------------------------------------
$ apt-get update
$ apt-get install xorg-driver-fglrx
$ sudo aticonfig --initial
$ sudo shutdown -r now
-----------------------------------------

Someone posted that around here so I decided to try that on my Radeon X1300 and it works. Doing:

$ fglrxinfo

shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)
---------------------------------------------------------------

Keep in mind that this was a FRESH install. Even though it works fine, I however still would like to tweak it so that it can run at its max. Anyone here knows how to tweak ATI card under LINUX?

I don't understand y u gave up  on the 9000 pro mine worked perfect with compiz fusion and AWN out of the box did i say all 3D works sweet. no twk nothing :guitar:

---

### Post by murat13 on 2007-11-08
Hello all

I'm little bit confused here.I have ati 9200 with open soruce drivers ( &#305; guess).Gutsy otomaticaly handled everything.Direct rendering is ok compiz fusion works well, wow works with wine but when i installed cedega video test fails it says 3d acceleraiton is not working.Also some other games are not working for the same reason.So as a newbie i wonder is there something wrong with my drivers.Any idea will be appreciated.Thanks and regards

---

### Post by wounded on 2007-11-09
> **murat13 said:**
> Hello all

I'm little bit confused here.I have ati 9200 with open soruce drivers ( &#305; guess).Gutsy otomaticaly handled everything.Direct rendering is ok compiz fusion works well, wow works with wine but when i installed cedega video test fails it says 3d acceleraiton is not working.Also some other games are not working for the same reason.So as a newbie i wonder is there something wrong with my drivers.Any idea will be appreciated.Thanks and regards

Interestingly I have a Radeon 9200 and Gutsy did NOT set up my direct rendering (Feisty did every single time though).

It set me up using the ATI driver, will FGLRX let my ld card use direct rendering again?

---

### Post by Yellow Pasque on 2007-11-09
> **tongpeng said:**
> 01:00.0 0300: 1002:94c9
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c9
Care to elaborate? Run:
```
sudo update-pciids
```
------------------------------------------------------------------------------

murat13,
Try installing the latest driver (8.42.3) from the ATI site. See guide [here]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#")

------------------------------------------------------------------------------

wounded,
yes, you should be able to use direct rendering with the proprietary driver.

---

### Post by murat13 on 2007-11-09
Thank you for the reply Temüjin.But i thought the latest driver for ati 9200 was 8.28 . I tried to install it but it gave me a strange error and broke my system. I did a fresh gutsy install. Still have direct rendering but no 3d acceleration.But im gonna check your guide and see what happens.

---

### Post by Yellow Pasque on 2007-11-09
> **murat13 said:**
> Thank you for the reply Temüjin.But i thought the latest driver for ati 9200 was 8.28 . I tried to install it but it gave me a strange error and broke my system. I did a fresh gutsy install. Still have direct rendering but no 3d acceleration.But im gonna check your guide and see what happens.

I've heard mixed things about older cards and the new driver. Some people are saying it's supported and some (namely the ATI Release Notes) say no joy.

---

### Post by murat13 on 2007-11-09
Couldn't make it work.does open source drivers support 3d acceleration? if not i will give up on this and maybe buy a better nvidia video card

---

### Post by hughjake on 2007-11-15
01:00.0 0300: 1002:9400
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9400
Not sure about that 9400 as the card is ATI 2900XT
This was a fresh install of gutsy with a few library updates
that the system recommended.
This is the result:
hugh@boxone:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2900 XT
OpenGL version string: 2.0.6958 Release

hugh@boxone:~$ glxgears
48083 frames in 5.0 seconds = 9616.569 FPS
48186 frames in 5.0 seconds = 9637.121 FPS
48173 frames in 5.0 seconds = 9634.586 FPS
48555 frames in 5.0 seconds = 9710.855 FPS
48821 frames in 5.0 seconds = 9764.149 FPS

and this is THE guide:
[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#comments](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#comments)
Where I cut and pasted his code to my terminal (no slip ups)
rebooted and it all works.
For compiz I needed to do this:
sudo gedit /etc/xdg/compiz/compiz-manager
and add this line
WHITELIST=fglrx

Before discovering this site I was stuffing around for 3 months in feisty
and gutsy, now I have compiz fusion with all the bells and whistles.
Hope your mileage doesn't vary.

hugh

---

### Post by Fittersman on 2007-11-17
on my friends dell laptop with a ati x1400 all i had to do was download the driver from ati's site and install that and the graphics card works great.

---

### Post by TedGarvin on 2007-11-18
I finally got the drivers installed, but it's a gift of the magi story.  Here's what I did for my ati 9600. ( 01:00.0 0300: 1002:4e51)
Using the synaptic package manager, I did a search for fglrx and removed everything that came up.  Then I followed [http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support")
which installed everything, but no compiz.  I added:

[B]Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection[/B]

to my xorg.conf file and I compiz works.  GREAT!!  But I get a horrible flicker on 3d applications and my video isn't as smooth as before. NOT SO GREAT.  I'm looking around for an answer now, but I hope this helps someone.

---

### Post by Wartz on 2007-11-20
01:00.0 0300: 1002:7280
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro]

I installed the binary fglrx drivers offered in the restricted drivers manager. No extra tweaking was needed besides adding:

Option "Composite" "Enable" 

to xorg.conf

---

### Post by TedGarvin on 2007-11-20
> **TedGarvin said:**
> I finally got the drivers installed, but it's a gift of the magi story.  Here's what I did for my ati 9600. ( 01:00.0 0300: 1002:4e51)
Using the synaptic package manager, I did a search for fglrx and removed everything that came up.  Then I followed [http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support")
which installed everything, but no compiz.  I added:

[B]Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection[/B]

to my xorg.conf file and I compiz works.  GREAT!!  But I get a horrible flicker on 3d applications and my video isn't as smooth as before. NOT SO GREAT.  I'm looking around for an answer now, but I hope this helps someone.
Well I ran this way for a couple of days.  Rebooting and restarting and then yesterday, I booted in a white screen.  I have no idea what happened.  Nothing changed.  I used sudo dpkg-reconfigure -phigh xserver-xorg and changed the driver back to fglrx in xorg.conf and everything went back to normal.  Strange.

---

### Post by meindian523 on 2007-11-20
```
easwarh@l1nuxr0cks:~$ lspci -n | grep 0300
01:05.0 0300: 1002:5a61
easwarh@l1nuxr0cks:~$ 

```
```

easwarh@l1nuxr0cks:~$ lspci | grep VGA.
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
easwarh@l1nuxr0cks:~$ 

```

I am using fglrx.no tweaking required.....C-F runs fine....
I wanted the "effects",so I can't comment on the open-source driver,,,,,

---

### Post by pacanukeha on 2007-11-20
I have a fresh install of Gutsy, a Macbook Pro v2 with ATI mobility radeon x1600.
I downloaded the driver from ati and run the executable.
I rebooted and enabled restricted drivers
I rebooted and installed xgl-server and dependencies
I rebooted and installed compiz-fusion and dependencies
I rebooted
everything "just works" including compiz except amdcccle
to get amdcccle working properly, I simply run:
DISPLAY=:0 amdcccle

---

### Post by stunner on 2007-11-20
TedGarvin - I recommend nonXgl ([http://ubuntuforums.org/showthread.php?t=176636]("http://ubuntuforums.org/showthread.php?t=176636")) for running totem, vlc, etc and 3d apps.

---

### Post by Mjölner on 2007-11-21
Hi

 > lspci -n | grep 0300
01:05.0 0300: 1002:791e

>  lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series


I have an Asus M2A-VM motherboard with Integrated ATI Radeon X1250-based graphics card.

Card worked fine with the bundled driver but there was always a nasty green flash just between logon and the desktop screens.
I found a page on the main site that told me to install the "ATI binary X.Org driver" in Add/Remove Applications. I did that and then enabled the restricted driver in System>Admin.>Restricted drivers manager, and now I don´t get it happening any more.
All GUI and no terminal:)

If you want any more info, send me a message.

---

### Post by Dynar on 2007-11-26
Hello everyone, 

I'm having trouble with my ATi Radeon 9550. I can't seem to get any graphic rendering (Games-wise), meaning no OpenGL. I've been at it for hours, browsing through tutorials and can't seem to get anything working properly. Right now, I have the eye candy I want, but gaming is important too. Can anyone help me out with a step by step and correct way to install my graphics card, so I also know the source is reliable.

I heard that they have troubles with 9550 drivers, it being bugged or something and that I should wait for the next release, 7.11. Is there anything I can do temperarly, because I don't want to install Windows just to play games.

I don't know where to begin.. I think I changed to much to even know what is standard.

---

### Post by terribletrouble on 2007-12-13
IBM T42 Laptop:

```
$ lspci -n | grep 0300
01:00.0 0300: 1002:4e50
```

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

This was the biggest pain I have ever had in my life. I want the laptop to always have it's display just like normal, 1400x1050, and when I plugged in another monitor, I wanted it to have it's own resolution, native: 1680x1050. So I grabbed ATI's latest driver, what a piece of junk! 2 days, until I eventually went back to the fglrx driver that ships with Gutsy, and the smallest xorg.conf file I have ever seen, and it works like a charm. It is setup just like a regular dual head, with screen1 rightof screen0 and so on. No modelines, no modes, bare.

---

### Post by lamadredelsapo on 2007-12-14
I followed method 2 from this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by MrKirby on 2007-12-22
Radeon x1600 Pro 512MB AGP 8X

The method I used to install ATI's proprietary drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
[B]

Use method 2, and follow and read closely![/B]  The link to their updated driver is on this page, and it appears to update every time they update their drivers.  At the time of posting it gives you the ati-driver-installer-8.443.1-x86.x86_64.run file that includes catalyst control center.  I was unable to get it work properly unless I installed the most recent driver as of the 20th.

I also uninstalled fglrx almost completely before reinstalling my previous version with the new ones without a logout or reboot, if that makes any diff.

After following the directions, the driver and CCC worked well.  It would be working perfectly if I didn't want to use Compiz's Extra Effects.  There were a few problems with that still remaining, which seem to simply be things yet to be developed by ATI.

I am NOT using xgl_server, but instead using AIGLX.

**Problems:**

-Using AIGLX with any Compiz effects turned on makes scrolling very slow in applications such as Firefox.  Not as slow as it was with prev. driver using xgl.

-Videos played in a window are all flickery, but do not flicker when in fullscreen.

-I seem to have a 10-second period of a black screen with strange colorful flashing scan lines at about half-second intervals at random heights and widths across my screen after I log out and when I boot up before login.

**lspci -n | grep 0300**

```
01:00.0 0300: 1002:71c2
```

**glxinfo**

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7170 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

**fglrxinfo**

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7170 Release
```

**xorg.conf**

```


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
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc101"
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
	VendorName   "Compaq"
	ModelName    "Compaq S900 Color Monitor"
	HorizSync    30.0 - 95.0
	VertRefresh  50.0 - 160.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BoardName   "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedXrender" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2048 1536
		Depth     24
		Modes    "1600x1200@60" "1600x1200@75" "1600x1200@65" "1600x1200@70" "1400x1050@75" "1792x1344@60" "1400x1050@60" "1856x1392@60" "1280x960@75" "1920x1440@60" "1280x1024@60" "2048x1536@60" "1280x1024@85" "1280x960@85" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
	EndSubSection
End Section

```

**/usr/bin/compiz**

```
COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2972" # i965 (x3000)
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS=""
#unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS=""
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()
{
	if [ "x$VERBOSE" = "xyes" ]; then
		printf "$*"
	fi
}

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 0;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}

# Check for non power of two texture support
check_npot_texture()
{
	verbose "Checking for non power of two support: "
	if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then
		verbose "present. \n";
		return 0;
	else
		verbose "Not present. \n"
		return 1;
	fi

}

# Check for presence of FBConfig
check_fbconfig()
{
	verbose "Checking for FBConfig: "
	if [ "$INDIRECT" = "yes" ]; then
		$GLXINFO -i | grep -q GLX.*fbconfig 
		FB=$?
	else
		$GLXINFO | grep -q GLX.*fbconfig 
		FB=$?
	fi

	if [ $FB = "0" ]; then
		unset FB
		verbose "present. \n"
		return 0;
	else
		unset FB
		verbose "not present. \n"
		return 1;
	fi
}


# Check for TFP
check_tfp()
{
	verbose "Checking for texture_from_pixmap: "
	if [ $($GLXINFO 2>/dev/null | grep GLX_EXT_texture_from_pixmap -c) -gt 2 ] ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		if [ "$INDIRECT" = "yes" ]; then
			unset LIBGL_ALWAYS_INDIRECT
			INDIRECT="no"
			return 1;
		else
			verbose "Trying again with indirect rendering:\n";
			INDIRECT="yes"
			export LIBGL_ALWAYS_INDIRECT=1
			check_tfp;
			return $?
		fi
	fi
}

# Check wether the composite extension is present
check_composite()
{
	verbose "Checking for Composite extension: "
	if xdpyinfo -queryExtensions | grep -q Composite ; then
		verbose "present. \n";
		return 0;
	else
		verbose "not present. \n";
		return 1;
	fi
}

# Detects if Xgl is running
check_xgl()
{
	verbose "Checking for Xgl: "
	if xvinfo | grep -q Xgl ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		return 1;
	fi
}

# Check if the nVidia card has enough video ram to make sense
check_nvidia_memory()
{
	MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')
	if [ $MEM -lt $NVIDIA_MEMORY ]; then
		verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";
		return 1;
	fi
	return 0;
}

# Check for existence if NV-GLX
check_nvidia()
{
	if [ ! -z $NVIDIA_INTERNAL_TEST ]; then
		return $NVIDIA_INTERNAL_TEST;
	fi
	verbose "Checking for nVidia: "
	if xdpyinfo | grep -q NV-GLX ; then
		verbose "present. \n"
		NVIDIA_INTERNAL_TEST=0
		return 0;
	else
		verbose "not present. \n"
		NVIDIA_INTERNAL_TEST=1
		return 1;
	fi
}

# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
	TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
	RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
	VRES=$(echo $RESOLUTION | sed 's/.*x//')
	HRES=$(echo $RESOLUTION | sed 's/x.*//')
	verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
	if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
		verbose "Failed.\n"
		return 1;
	fi
	verbose "Passed.\n"
	return 0
}

# check driver whitelist
running_under_whitelisted_driver()
{
	LOG=$(xset q|grep "Log file"|awk '{print $3}')
	if [ -z "$LOG" ];then
		verbose "AIEEEEH, no Log file found \n"
		verbose "$(xset q) \n"
	return 0
	fi
	for DRV in ${WHITELIST}; do
		if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
		   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG; 
		then
			return 0
		fi
	done
	verbose "No whitelisted driver found\n"
	return 1
}

# check pciid blacklist
have_blacklisted_pciid()
{
	OUTPUT=$(lspci -n)
	for ID in ${BLACKLIST_PCIIDS}; do
		if echo "$OUTPUT" | egrep -q "$ID"; then
			verbose "Blacklisted PCIID '$ID' found \n"
			return 0
		fi
	done
	OUTPUT=$(lspci -vn | grep -i VGA)
	verbose "Detected PCI ID for VGA: $OUTPUT\n"
	return 1
}

build_env()
{
	if check_nvidia; then
		ENV="__GL_YIELD=NOTHING "
	fi
	if [ "$INDIRECT" = "yes" ]; then
		ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "
	fi
	if check_xgl; then
		if [ -f ${LIBGL_NVIDIA} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"
			verbose "Enabling Xgl with nVidia drivers...\n"
		fi
		if [ -f ${LIBGL_FGLRX} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"
			verbose "Enabling Xgl with fglrx ATi drivers...\n"
		fi
	fi

	ENV="$ENV FROM_WRAPPER=yes"

	if [ -n "$ENV" ]; then
		export $ENV
	fi
}

build_args()
{
	if [ $INDIRECT = "yes" ]; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
	fi
	if check_nvidia; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
	fi
}

####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
	test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
	test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
	test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
	test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# Don't use compiz when running the failsafe session
if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then
	abort_with_fallback_wm
fi

if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then
	INDIRECT="yes";
fi

# if we run under Xgl, we can skip some tests here
if ! check_xgl; then
	# if vesa or vga are in use, do not even try glxinfo (LP#119341)
	if ! running_under_whitelisted_driver || have_blacklisted_pciid; then
		abort_with_fallback_wm
	fi
	# check if we have the required bits to run compiz and if not, 
	# fallback
	if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then
		abort_with_fallback_wm
	fi

	if check_nvidia && ! check_nvidia_memory; then
		abort_with_fallback_wm
	fi

	if ! check_fbconfig; then
		abort_with_fallback_wm
	fi
fi

# load the ccp plugin if present and fallback to plain gconf if not
if [ -f ${PLUGIN_PATH}libccp.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"
elif [ -f ${PLUGIN_PATH}libgconf.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"
fi

# get environment
build_env
build_args

# start the gtk-window-decorator if present
if [ -x ${COMPIZ_BIN_PATH}emerald ] && [ "$USE_EMERALD" = "yes" ]; then
	verbose "Starting emerald\n"
	${COMPIZ_BIN_PATH}emerald --replace &
elif [ -x ${COMPIZ_BIN_PATH}gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
	verbose "Starting gtk-window-decorator\n"
	${COMPIZ_BIN_PATH}gtk-window-decorator --replace &
elif [ -x ${COMPIZ_BIN_PATH}kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then
	verbose "Starting kde-window-decorator\n"
	${COMPIZ_BIN_PATH}kde-window-decorator --replace &
	FALLBACKWM="${KWIN}"
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS
```

---

### Post by perixx on 2008-01-02
[COLOR="Blue"]**Graphics card: ATI / Palit XpertVision X1950 GT**[/COLOR]

> lspci -n | grep 0300
01:00.0 0300: 1002:7288 (rev 9a)
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7288 (rev 9a) 

In this post I've described my way through the problems toinstall the new ATI 8.443.1 driver:
[http://ubuntuforums.org/showthread.php?t=647087&page=2]("http://ubuntuforums.org/showthread.php?t=647087&page=2")

Neither the commonly used method manual installation method with: 
```
sudo bash ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy
```
nor 'ENVY' worked properley - there was no OpenGL support (just 'Mesa').

:arrow: Simply **running the installer as superuser worked** flawlessly, inspite of many other opinions (and also disposed of the 'Mesa-mess').
**[COLOR="Blue"]Rem.: I had uninstalled the old ATI proprietary driver first (with Envy)![/COLOR]** 
Not sure, but "sudo apt-get remove xorg-driver-fglrx" before installation might serve the same purpose...
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1950 GT
OpenGL version string: 2.1.7170 Release

Direct Rendering is enabled by default:
> grep -i "Direct rendering" /var/log/Xorg.0.log
(II) fglrx(0): Direct rendering enabled

Further settings can be done without trouble through the GUI
'**[COLOR="Blue"]amdcccle[/COLOR]**' (AA / AF / Color / VSYNC)...

':!:VSYNC always on' (amdcccle) is the ONLY option that will result in a good _video experience without tearing_.
Adding the usual options like to xorg.conf won't help: 
```
Section "Device"
	Identifier  "Standardgrafikkarte"
	Driver		"fglrx"
	BusID       	"PCI:1:0:0"
	Option		"VideoOverlay"	"on"     **<=by ATI, still tearing!**
	Option		"OpenGLOverlay"	"off"    **<=by ATI**
	Option		"XaaNoOffscreenPixmaps"  **<=added myself**
	Option		"UseFastTLS"	"2"      **<=added myself**
#       Option	    	"TexturedVideoSync" "on" **<=on by default, thus commented out!**
```
But the drawback of VSNC (or 'wait for vertical refresh') is a slightly blurred video picture and most of all a great loss of 3D-performance + 'mouse-lag' and often worse graphics in games. Some advanced manager like 'ATT' under Windows might serve a good purpose here.

**_Summary:_**
3D gaming performance is quite good but maybe not quite at the level the Windows-drivers are delivering, especially with higher AA + AF settings. E.g. UT2004 is really ok in single player mode - but horrible in multiplayer mode, even with all effects disabled (maybe network interface load is playing a major role here...).

[COLOR="Red"]Add experience note:[/COLOR] having had a more thorough testing phase now, I can tell that the 3D performance of the 8.443-1 ATI-drivers is no match for the Windows-pendant at all. Those are by far superior and provide good performance even with goodies enabled. What's more, some games (like freedroidRPG or Serious Sam 2) won't start at all anymore (older driver worked) - though SS2 wouldn't last very long, even with an Nvida card so far. 

**- Enabling 'Compositing'** will work, but results in a very sluggish desktop handling (not 'Composite' in xorg.conf - can be set to 'Enabled').
**- AIGLX** seems to work properly (turned on by default):
> grep -i "AIGLX enabled" /var/log/Xorg.0.log
(**) AIGLX enabled
**- Disabling the old 'fglrx'-drivers** should be done by the installer, if not, add/change 
```
gksudo mousepad /etc/default/linux-restricted-modules-common
DISABLED_MODULES="fglrx"
```

[COLOR="Blue"]**ADDITION:**[/COLOR] 'libgl open: permission denied' - no direct rendering. Encountered after re-installation. Solution: running > sudo dpkg-reconfigure -phigh xserver-xorg + resetting keyboard settings manager to appropriate localization. When still not working, try setting 'Composite' to 'Disable' in xorg.conf.
**[COLOR="Red"]WARNING:[/COLOR]** Certain apps/games won't seem to run at all with driver version 8.443.1 (e.g. Serious Sam 2 / freedroidRPG) -- maybe a problem with OpenGL implementation?

perixx

---

### Post by wesswei on 2008-01-04
1) 02:00.0 0300: 1002:4150
2) Radeon 9600 Pro AGP
3) installed fglrx as described at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
4) Had to > mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager as on the cchtml wiki to get desktop effects to work because whitelisting doesn't help. 

Tweaks: I have my own custom xorg.conf

Notes: Experiencing *double free or corruption* issue as well as no desktop effects while using dual monitors, but ONE monitor works with all the bells and whistles. Unsolved.

Also: Uninstalled native ubuntu (gutsy) "proprietary graphics drivers" and "restricted-modules" FIRST then installed ATI fglrx manually. On previous installs, if I didn't do that, I was left with 'safe graphics modes'

---

### Post by BMWDriver on 2008-01-15
1) 02:00.0 0300: 1002:4150
2) 02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
an ATI 9600 Pro with 128 MB AGP card if you will.

3) Downloaded and installed Catalyst 7.11 and issued command "aticonfig --resolution=0,1650x1050"

Catalyst 7.12 did not recognize my screen's optimum resolution off the bat, so I went for 7.11 instead, and problem solved. Enabled desktop effects by whitelisting "ati fglrx radeon".

---

### Post by n-alexander on 2008-01-29
I have Asus EAX1300 pro, which is Ati Radion X1300 chip. Does it means that ATi driver should work?

So far, after running ati-driver-installer-8.31.5-x86.x86_64.run and aticonfig --initial, X server fails back to safe mode and won't leave unless I remove the config file from /etc/X11/

I tried installing the opensource ATi driver with same result.

Needless to say, OpenGL doesn't work.

Or is it a question of some settings being incorrect?

(Ubuntu 7.10)

Thanks,
Alex

---

### Post by nasov on 2008-01-30
_1_
nasov@Lucy:~$ lspci -n | grep 0300
03:00.0 0300: 1002:7183
_2_
nasov@Lucy:~$ lspci | grep VGA
03:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
_3_
Well, this is a long story! First I had to tweak myself with a lot of patience and cofee for those long nights and days I spent trying to get it all working.
For catalyst 8.01 i followed the method2 guide at wiki.cchtml.com plus I had to create the symlinks which guide tells you to do only if something doesn't work. Plus compiz stopped working due to a path change - so i had to change the path in the compiz config files and whitelisting fglrx in the same file. For some reason I had xgl still installed so I had to get rid of that.
The installation isn't much different to what it was with any earlier version of fglrx (some minor changes maybe)

Sorry, if the tweak list is a bit vague but I used so many guides so it is hard to remember it all. These are however the major problems i had to face after installing catalyst.

---

### Post by najames on 2008-01-31
1)  lspci -n | grep 0300
01:05.0 0300: 1002:791e

2)  lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series

After 4 long nights, I finally have 1680x1050 fglrx "accelerated video" working on the Biostar TA690G onboard ATI 690G video in Mint Daryna. 

0) I realized that Ubuntu and Envy installed the old ATI video driver version, limited to 1280x1020 max
1) uninstalled Intel 915 and 810 video stuff installed by default in Mint, it complained of conflict
2) installing ATI drivers according to the method2 guide at wiki.cchtml.com
3) Learned to NEVER use the "Test" button to check if the video works.  It shows EVERY video setting as corrupted (WTF?) just choose settings, click OK, and pray that it works.
4) the first set of parameters didn't have 1680x1050 listed, it took some more hacking around in monitor selections to find it and make it stick.
5) Using Quit button in Mint yielded a black screen and a totally locked, searching shows an ATI daemon borked it, oops.  I read how to disable the daemon, Quit works again.
6) testing with glxgears will kick you out of the desktop, back to the logon screen, huh?
7) stuff like scrolling in Firefox is slower.  Not sure why.
8) just tested playing a Hogans Heroes mpg and it plays worse, not smooth like it did with default driver.  There might be "settings" for this somewhere.
9) no ATI control panel GUI working now

I'm sorry, but it shouldn't be this hard to change video "drivers".

Now I'm ready to pull my other HP w2207 out of the box and spend another 4 nights trying to make dual monitors work.

---

### Post by n-alexander on 2008-01-31
> **najames said:**
> 1)  lspci -n | grep 0300
3) Learned to NEVER use the "Test" button to check if the video works.  It shows EVERY video setting as corrupted (WTF?) just choose settings, click OK, and pray that it works.


I found that, on my machine, it actually fails every time I try an option once. Second time it'll work ok. So just hit Test, wait for it to fall back, and hit again.

---

### Post by Statix0 on 2008-01-31
My graphics card is the Radeon X800 and my mobo is the Asus K8N-E Deluxe. There was an odd incompatibility with my bios version, which I had updated to the beta 1012 version. I reverted to bios 1006 and it worked perfectly. (Including direct rendering.)

Installed my ati drivers using
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
Method 1, manual config

This explains the bios problems:
[http://wiki.cchtml.com/index.php/Troubleshooting#nForce_3_AGP_Issues](http://wiki.cchtml.com/index.php/Troubleshooting#nForce_3_AGP_Issues)

---

### Post by najames on 2008-02-02
> **n-alexander said:**
> I found that, on my machine, it actually fails every time I try an option once. Second time it'll work ok. So just hit Test, wait for it to fall back, and hit again.

The "test button" is batting a perfect 1.000.  It generates a nice bunch of video garbage every single time and fails every single time and doesn't matter if I have selected vesa, Radeon, or anything else.  It doesn't matter what resolution I chose either.

The ONLY time it has worked was with the latest 8.01 (?) ATI driver installed as in the link below.  ATI config panel did not work.
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Last night and tonight I have been hacking on trying to make dual monitors work.  I thought I lost my Minty Daryna box last night, but it bounced back tonight after stripping out everything and starting over with Mesa default setups and at the wrong 1280x1024 resolution I saved the xorg.conf for.  Xrandr didn't seem to work either, says its for Intel stuff.

So far I got my mouse across the two screens once before the PC went nuts, but the displays were messed up, different resolutions on each one, etc.  Ouch, my eyes hurt.  The PC was so slow that it was basically unusable.  Clicking on the quit button took 25 seconds for it to come back with the menu.

---

### Post by perixx on 2008-02-02
Hello!

I'm having big trouble getting new Ati drivers to work, ever since I've had a Nvidia 6800XT with 169.09 driver in my system temporarily - some parts of that remained on my system, somehow seeming to block ATI drivers from installing properly... at first, I wanted to install the 8.01 drivers with my X1950 GT, but I'm not sure anymore, if they'll install on Feisty at all (due to DKMS) - but also 7.11 won't install now!

I'm afraid I've misplaced my initial thread; since it concerns both Nvidia and Ati issues, I'll repost it twice & link to my more detailed problem-thread (it's not too long - yet). According to a post in this thread, ATI 8.01 drivers are not made for the 'X'-series cards, so not for me... I dunno, if 8.01 is supposed to install under Feisty at all:
[http://ubuntuforums.org/showthread.php?t=685476]("http://ubuntuforums.org/showthread.php?t=685476")

**ADD: **As far as I can tell, I've removed all Nvidia crap that has obviously totally borked my symlinks before:
[http://ubuntuforums.org/showthread.php?t=679086]("http://ubuntuforums.org/showthread.php?t=679086")

perixx

---

### Post by najames on 2008-02-03
I finally have both w2207 monitors working with the onboard ATI x1250 video.  I am using Mint Daryna ~ Gutsy. 

]I used Envy to delete all ATI driver stuff I previously installed, checked to make sure video seemed to be behaving normally, Mesa running. 

I tried to setup a** generic** xorg.conf file that looked right for dual monitors.  There are a million versions of this online, many not dated when they did it and some are out of date and don't work, some had commands in them that caused aticonfig to reject them.  You've been warned.

I downloaded the current ATI drivers here (8.1 18Jan08 version).
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I installed them like it says here, use Method 2 info and stopped after the sudo aticonfig --initial.  I skipped the build essiental fakeroot command and the install -f command because I am using a 32bit OS.
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

After running sudo aticonfig --initial, I rebooted and got a dual screen 1680x1050 in clone mode.  I then ran Catalyst Control Center, which crashed before, works great now.  fglrx was very slow scrolling in Firefox before, fast now.   Apps took forever to open before, fast now.  glxgears crashed before, runs smooth now.   I clicked on display manger and changed from clone to Big Desktop and now have dual screens working at 3360x1050, very nice.

Minime:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7276 Release

Minime:~$ glxgears
2265 frames in 5.0 seconds = 452.818 FPS
2542 frames in 5.0 seconds = 508.293 FPS
2545 frames in 5.0 seconds = 508.972 FPS
2544 frames in 5.0 seconds = 508.763 FPS
2541 frames in 5.0 seconds = 508.124 FPS


To do:
This PC starts in clone mode and I need to run CCC, not static, but it only takes a few clicks and I have on the fly big desktop.

I tried to play a Hogan's Heros MPG file that worked before and it crashes with any video player.  I likely need some more of the instructions in the install guide.

My xorg.conf looks like it shouldn't even work, but it does.  I left in known working 1280x1024 parameters, but it is displaying each monitor at 1680x1050 like it should anyway, huh?  Clone off but it still does it anyway. ATICONFIG looks like it added in what it wanted to and is ignoring all the stuff I wrote, smart move ATI!!  I bolded what I originally wrote so you can see what I did and what ATICONFIG did.  This xorg.conf stuff needs to die.

# xorg.conf (xorg X Window System server configuration file)
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

#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	[B]Option	    "clone" "off"
        # DualHead means two monitors
	Option	    "DesktopSetup" "3360 1050"[/B]
# Uncomment if you have a wacom tablet
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
[B]
Section "Monitor"
	Identifier   "HP w2207 0"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "HP w2207 1"
	Option	    "DPMS"
EndSection[/B]

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

[B]Section "Device"
	Identifier  "ATI Radeon x1250 0"
	Driver      "vesa"
	Option	    "UseEdidFreqs" "false"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "ATI Radeon x1250 1"
	Driver      "vesa"
	Option	    "UseEdidFreqs" "false"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection[/B]

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
EndSection

[B]Section "Screen"
	Identifier "Screen 0"
	Device     "ATI Radeon x1250 0"
	Monitor    "HP w2207 0"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024@60" "1152x864@60" "1024x768@60" "800x600@60" "640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen 1"
	Device     "ATI Radeon x1250 1"
	Monitor    "HP w2207 1"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024@60" "1152x864@60" "1024x768@60" "800x600@60" "640x480@60"
	EndSubSection
EndSection[/B]

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

---

### Post by sa87 on 2008-02-20
$ lspci -n | grep 0300
01:00.0 0300: 1002:5d57
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)]


How I did it:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) (first method)
then 
```
sudo aticonfig --dtop=horizontal --overlay-on=1
```
to enable big desktop followed by changing the screen resolution to 2560x1024 to actually get the bigdesktop working on 2 monitors.

---

### Post by BXA121 on 2008-02-24
i have an ATI 9800 pro card. 

on my searches, i found  a really simple way to install proprietry drivers! 

install Envy and it will complie and install the right driver automatically
here is the guide

[http://www.ubuntu1501.com/2007/12/in...ti-driver.html](http://www.ubuntu1501.com/2007/12/in...ti-driver.html)

So simple! i tried to use the guides to manually activate my driver to no end - i failed - i searched around and foudn this dell guide ( i dont have a dell) and it worked fine. 

hope this helps.

---

### Post by white_eagle-mk on 2008-02-24
1) 01:05.0 0300: 1002:5a62
2) 01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]  --- 64 MB
3) First I installed the fglrx drivers, like usual, but I didn't get direct rendering (so say bye to quake III arena and other games), but then I discovered the ATi's official drivers and how to install them, originally I followed this guide [http://ubuntuforums.org/showthread.php?t=589637](http://ubuntuforums.org/showthread.php?t=589637) , but then the new drivers came up, I removed the old ones via Synaptic, and again followed this guide, but with the new driver downloaded and the numbers replaced with the newer ones y'know. 
'N thats all...

---

### Post by msarro on 2008-02-25
Mine was actually fairly painless. I'm using a radeon 9800xt with Ubuntu desktop.
 I followed the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The repos driver didn't work for me and it kept defaulting to the MESA renderer. I downloaded the ati driver and used dkms a la the above link. I built the gutsy package and installed as explained in the guide. The only issue I ran into afterwards was upon my first reboot. I got a solid white screen and could do nothing.

After a bit of searching i found this fix (first post in thread):
[http://ubuntuforums.org/showthread.php?t=417161](http://ubuntuforums.org/showthread.php?t=417161)

> I have a radeon 9800 card.

I got white screen because of the following bug: [https://bugs.launchpad.net/ubuntu/+s....20/+bug/78684](https://bugs.launchpad.net/ubuntu/+s....20/+bug/78684)

This is how I got things working:

1. Make sure you have open source "ati" drivers (howto: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver))

2. Do "lsmod | grep edac". If you get output containing i82875p_edac and edac_mc, blacklist them:

Code:
```
sudo gedit /etc/modprobe.d/blacklistAdd lines
```

Code:
```
blacklist i82875p_edac
blacklist edac_mc3. Reboot and try desktop effects.
```

I also hadn't direct rendering working before doing this (not with "ati" nor with "fglrx" drivers). Hopefully this would resolve someone other's problems too.

After the reboot it worked like a charm. Sadly however I still get flickering issues, but then again, doesn't everyone using ATI?

---

### Post by JoePits on 2008-03-03
found this on phoronix forums

guy made a script that automagically gets the 8.02 install file and makes it work on gutsy.

[http://www.phoronix.com/forums/showthread.php?t=7193](http://www.phoronix.com/forums/showthread.php?t=7193)

then all i had to do was the 
/etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false 

and suspend works for the first time in a while with the fglrx driver (didnt work for me wtih default fglrx and these options...works with the 8.02 with that script and then changing the options)

---

### Post by Kivech on 2008-03-05
Well, my card worked out of the box with the default proprietary drivers that came with Ubuntu 7.10 x64.

lspci -n | grep 0300:
> 01:00.0 0300: 1002:7249

lspci | grep VGA
> 01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)

My remaining problem is this:

glxinfo | grep rendering:
> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

No install guide that I've found over the past weeks manages to solve this issue. I'm starting to think it's a driver issue because there are for sure others with the same problem. 
It would be really nice if I can use direct rendering, but like I said, no suggestion came up with any result so far.

I made about 5 posts about the subject and so far, no one showed up with a solution that worked. So I'm about to give up on direct rendering.
And no, the install guide for the lastest ATI driver litterally just messes up my whole system. I'm baffled as to how it can work for others while I was forced to reinstall my system from scratch twice in a row trying to install the latest ATI driver.

About time ATI starts making proper drivers for Linux. It's nuts that it is even possible that people have to go through so much effort to get their "very" expensive hardware to work properly.

Kivech

---

### Post by bobdob20 on 2008-03-13
I finally managed to get my x1950 pro.

I used the guide for hardy, since im using kernel 2.6.24.12.
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

lspci -n | grep 0300

```
02:00.0 0300: 1002:7280 (rev 9a)
```

lspci | grep VGA

```
02:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
```

fglrxinfo

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7412 Release
```

glxinfo

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
```

---

### Post by SLK55_AMG on 2008-03-27
root@cisco:/home/ryan# lspci -n | grep 0300
01:00.0 0300: 1002:94c1

ryan@cisco:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c1


Followed this guide:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by SGAZ on 2008-03-28
01:00.0 0300: 1002:9505
Radeon HD3850 (grep VGA says card is ATI and unknown)

No tweaks (so far)
Default install vid drivers worked fine. Except for screen resolution limited to 1400x900 on a 1680x1050 monitor.
Ubuntu Restricted Driver Management would not recognize card as needing Restricted Drivers
Installed ATI Proprietary drivers 8.3 from this guide: [[COLOR="DarkGreen"]Gutsy ATi Efforts[/COLOR]]("http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts") 
*Still limited to 60Hz refresh rate despite CCC saying more is available and Monitor Specs call for 1600x1050@75Hz* -**  DVI Input Limitation in Monitor (all modes are 60Hz apparently)**

Tweak:  Fix Video Flicker during DVD playback in Compiz-Fusion [ http://ubuntuforums.org/showthread.php?t=723860]("http://ubuntuforums.org/showthread.php?t=723860")

---

### Post by jucas_lo on 2008-03-29
1) lspci -n | grep 0300
01:00.0 0300: 1002:5653
2) Ati Mobility Radeon x700
3) Used the envy package for Hardy Heoron
Worked better than the driver installed with the restricted drivers manager....but I have flickering problems with Totem (not with Mplayer or VLC) and also when I try to play games like Pinguin Racer....
Compiz-fusion effects work great

no tweaking made...had no look with anything to stop my screen from flickering (any suggestion would be appreciated)

---

### Post by SGAZ on 2008-03-29
Fix Flicker in Totem :  [http://ubuntuforums.org/showthread.php?t=723860]("http://ubuntuforums.org/showthread.php?t=723860")

Worked really well for me.

---

### Post by PoopyTheJ on 2008-03-30
I know this forum isn't for asking about Envy, but I used envy to install my video card on Ubuntu 7.10, easy peasy. I'm using an ATI 3850HD

---

### Post by Saint Angeles on 2008-03-30
with gutsy, i could only use november's fglrx (7.11)

with hardy heron, i d-loaded the LATEST fglrx from the ATI website. then i went to terminal and did: ```
sudo sh ati. [tab]
```

tab of course finishes the filename. the automatic installer worked fine for me ( as well as i blacklisted the fglrx module from the ubuntu-restricted-modules ( i don't remember the exact filename)...

i now get exceptional framerate with full screen video, compiz, and glxgears.

ubuntu - i love you

---

### Post by Kivech on 2008-04-02
Ok, for all those Hardy users out there....

I'm on Kubuntu Hardy with KDE 3.5 x86_64.

I installed EnvyNG and got a famous "white screen" as a result.

Rebooted into safe mode and had it reconstruct the X configuration and continued with a regular boot.

Then I followed part of the steps indicated here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

At the terminal:
> sudo depmod -a
then
> sudo nano /etc/X11/xorg.conf
enter in the Device section
> Driver "fglrx"
then in the terminal again
> sudo aticonfig --initial -f

Reboot and you are set.

As opposed to following only the steps listed in the wiki, this method allows your computer to shut down/reboot after installation of the driver. So practically this method solves two issues:
1) White screen when installing with EnvyNG
2) No more working shutdown/reboot when following the other guide I've listed here.

Good luck!

Kivech

---

### Post by Neodymion on 2008-04-05
$ lspci -n | grep 0300
02:00.0 0300: 1002:71c1 (rev 9e)
$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)

motherboard = Abit NF7-S2G
cpu = Athlon 2GHz

On Ubuntu 7.10 I had to downgrade fglrx several versions, which meant I can't use compiz. Mind you I had to do the same on Windows XP. Possibly there's something wrong with my PC.

Now on Hardy Heron the VESA driver supports 1680x1050 so I'm sticking to that.

---

### Post by Supersaiyan.IV on 2008-04-10
$ lspci -n | grep 0300
01:00.0 0300: 1002:5460
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

Used a combination of "Instructions for Ubuntu 7.10 (Gutsy) with ATi 8.443.1-1 and above binary drivers" & "nstructions for Ubuntu 7.10 (Gutsy) with ATi 8.42.3 Binary and AIGLX, for Compiz" & "Instructions for 7.04 (Feisty)". Apart from those I had to:

$ sudo dkms remove -m fglrx -v 8.452.1 --all -c /var/lib/dkms/fglrx/8.452.1/build/dkms.conf

As you see I had to specify the dkms.conf location because it wasn't in the standard directory, tricky. After the old kernel-module (ATI 8.452.1)  was removed, and new one was compiled as told in the tutorials everything worked like a charm.

Also my xorg has "TexturedVideo" "off" added to fix video playback flicker. Some 3D animations still flicker at times. Adding another line in xorg could fix that.

$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7412 Release

---

### Post by buried on 2008-04-10
Just update the system, thats how :)

---

### Post by jameskeagie on 2008-04-14
I had problems with flickering video.  

I installed the most recent proprietary drivers on a clean Ubuntu install following the standard HowTo's.

Here's my info on how I got it to work.

1.) 01:00.0 0300: 1002:7145
2.) 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
3.) To get mine to work I had to do the following modifications to xorg.conf.  I wrote up step by step instructions here:

[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

### Post by EdGato on 2008-04-30
Default Xubuntu installation:

00:0b.0 0300: 1002:5157
01:00.0 0300: 1039:6330
00:0b.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Don't like the resolution, though... need bigger characters, but 640x480 doesn't show enough of the characters... must go buy a new monitor.

I forgot to add:
Whenever Xubuntu boots, it automatically changes resolution three times, which probably means the default resolution is three steps higher than the one my monitor can handle. Could be the frequency too.

---

### Post by UgniusS on 2008-04-30
Got an old laptop with GPU: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64), I am using Fluxbuntu. 
Got graphics card working out of the box, except for direct rendering, after a day of googling and trying to get help on #fluxbuntu or #ubuntuforums irc (noone seemed to be interested to help much with this, may be I just asked inproperly), found out that card uses mach64 driver for direct rendering. mach64 is not included as default, do not know the real reason why, but I thought I'll have to compile it myself. After few unsuccessfull attempts to compile it I finally stumbled upon this page: [http://www.bakarasse.de/mach64-howto.html]("http://www.bakarasse.de/mach64-howto.html") and it saved me much time, it has a link to precompiled mach64.ko driver for Gutsy (using kernel: 2.6.22-14-generic), everything worked. Now I'm trying to set up compiz on this box (crazy). 
So far I've tried to use fglrx driver instead of ati and X fails to load with this setting.

I'm pretty new to linux, and english is not my native, so sorry for any mistakes here.

---

### Post by jsedwards on 2008-05-01
jsedwards:~$ lspci -n | grep 03.0
01:00.0 0300: 1002:715f
01:00.1 0380: 1002:717f
jsedwards:~$ lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc RV505 CE [Radeon X1550 64-bit]
01:00.1 Display controller: ATI Technologies Inc Unknown device 717f

I have an unusual situation with this card as it is a replacement.  I had a nVidia GeForce 8300 card (nVidia Corporation G80 [GeForce 8300 GS]) which I originally ran with the standard "nv" driver.  When I tried to watch any video on Kaffeine it would stutter horribly.  I installed the restricted nvidia driver (sudo apt-get install nvidia-glx nvidia-kernel-common) but never could get it to work: [http://ubuntuforums.org/showthread.php?t=764907]("http://ubuntuforums.org/showthread.php?t=764907")

Then I decided to try an ATI card to see if that worked any better.  I bought this 1550 card and installed it.  I edited the xorg.conf file and changed the ID to "ATI Technologies Inc RV505 CE [Radeon X1550 64-bit]" and the Driver from "nvidia" to both "radeon" and "ati".  Neither one worked.

Then I installed the restricted ATI driver (sudo apt-get install xorg-driver-fglrx).  I edited the xorg.conf file again and changed the Driver from "ati" to "fglrx".

I was able to startx then, but the resolution was way too high for my monitor (1920x1080).  I then edited the xorg.conf file again and added the following subsection to the "Screen" section:

        SubSection      "Display"
                Depth   24
                Modes   "1680x1050"
        EndSubSection

X windows is now working.  Unfortunately it did NOT make Kaffeine work any better, in fact it is worse as now it seg faults: [http://ubuntuforums.org/showthread.php?t=776865]("http://ubuntuforums.org/showthread.php?t=776865")

---

### Post by jsedwards on 2008-05-01
This is a follow up to my previous posting above.

I uninstalled the restricted driver (sudo apt-get remove xorg-driver-fglrx) and downloaded the driver: ati-driver-installer-8-4-x86.x86_64.run (dated April 16th) from the ATI website, made it executable and ran it.  It didn't have any errors and now Kaffeine plays almost all of the video files I have tried (it did still seg fault on a couple of odd ones).  It is certainly better than the xorg-driver-fglrx because Kaffeine crashed on every video with it.

---

### Post by NJC on 2008-05-04
Ubuntu 8.04, kernel 2.6.24-16-generic

1/ 01:00.0 0300: 1002:5159

2/ 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [**Radeon 7000/VE]**

3/ No tweaking although flickering and bizarro screen at times.

---

### Post by lungten on 2008-05-06
Ubuntu 8.04 LTS (Hardy Heron): Linux  2.6.24-16-generic
1. 01:00.0 0300: 1002:3154 (rev 80)
2. ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)
3. 3D effects worked after installing the restricted drivers but I experience some flicker while playing videos and the CPU usage goes very high as well while playing videos.

---

### Post by erginemr on 2008-05-06
> **lungten said:**
> Ubuntu 8.04 LTS (Hardy Heron): Linux  2.6.24-16-generic
1. 01:00.0 0300: 1002:3154 (rev 80)
2. ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)
3. 3D effects worked after installing the restricted drivers but I experience some flicker while playing videos and the CPU usage goes very high as well while playing videos.

Without getting too much off topic, for the flickering phenomenon, please refer to:
[http://ubuntuforums.org/showpost.php?p=4512042](http://ubuntuforums.org/showpost.php?p=4512042)
[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

### Post by Mijoker on 2008-05-07
#1   03:00.0 0300: 1002:4150
#2   03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
#3   Ugh, cant get it to work, and haven't found 03:00.0 0300 in any of the search strings...

---

### Post by mrtomservo on 2008-05-08
01:00.0 0300: 1002:71c1 (rev 9e)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)

Clean install of Ubuntu 8.04.  Ubuntu recommended proprietary drivers. I used the Hardware Drivers GUI and the install worked just fine.  The ATI proprietary drivers are working fine.  However, I am experiencing the compiz/opengl flicker problem.

I have tweaked my xorg.conf according to another post here:

[http://ubuntuforums.org/showthread.php?t=754712]("http://ubuntuforums.org/showthread.php?t=754712")

```
Section "Device"
	........
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
        .........
EndSection
```

Sadly this did not solve the flickering.  I have to disable compiz to stop the flickering.

---

### Post by rcorbish on 2008-05-08
Yet another one: Radeon 1300 - lots of reboots but mayb save a reinstall or two

1) fresh Hardy install

2) Go to ATI website & download the Linux drivers

3) reboot

4) white screen of death ( WSOD )

5) reboot & drop to root prompt

6) aticonfig --initial  & reboot

7) use catalyst to set big desktop - reboot

8) wrong left & right hand monitors -correct this ( reboot )

9) Woo hoo - 2 monitors 

OK so I rebooted too many times, but prior to this I had installed too many times - which is faster - it's your call

I hope this helps at least one other person

---

### Post by mravljica on 2008-05-09
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7412 Release


Fresh Hardy install, then from ATI site took the latest (8.4) driver and install:
#sudo bash *driver-8.4.run

#Reboot

For compiz to work, a file /usr/bin/compiz need some changes [http://ubuntuforums.org/showpost.php?p=3993442&postcount=5](http://ubuntuforums.org/showpost.php?p=3993442&postcount=5)

Tested with Alien-arena and it is working nice.

---

### Post by guildofghostwriters on 2008-05-09
1. 02:00.0 0300: 1002:4e48
2. 02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
3. I tried every method I could find here and elsewhere a few weeks ago and eventually gave up. I decided to try again today using the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) (which I had tried several times previously without success) and eventually got it working. The main 'tweak' was to remove my second monitor and forget about dual head because that just knackers it however I try to make it work. The only other thing I needed to do was, when following the instructions, at the point where I needed to edit xorg.conf, gedit wouldn't work because it said something about a screen not being available so I used nano instead. I suppose I should be wary of counting chickens because it's been running about 30 minutes so far but touch wood it seems to be okay so long as I don't try to extend my desktop onto that second monitor.

---

### Post by kagashe on 2008-05-10
~$ lspci -n | grep 0300
01:05.0 0300: 1002:4337

$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

No tweaking needed but external VGA monitor does not work on this card in Hardy Heron.

External monitor is vital for me since the LCD display is broken.

I tried to reconfigure the external VGA monitor through xrandr but could not.

I went to bugs.freedesktop.org and found a bug for my card. I also submitted a bug report.

Since dpkg-reconfigure xserver-xorg does not work in Hardy I wrote xorg.conf file and used vesa driver to make the external VGA monitor work.

kagashe

The bug regarding external monitor has been closed. The updated ati driver is available in Debin Sid. I have downloaded the required drivers from Debian Sid repositories and they are working on Hardy:
xserver-xorg-video-ati_6.8.192-1_i386.deb
xserver-xorg-video-mach64_6.8.0-1_i386.deb
xserver-xorg-video-r128_6.8.0-1_i386
xserver-xorg-video-radeon_6.8.192-1_i386

I have deleted xorg.conf file, xrandrr -q is showing VGA-0 and LVDS outputs and I could turn off LVDS.

---

### Post by flnhst on 2008-05-15
$ lspci -n | grep 0300
01:00.0 0300: 1002:7280 (rev 9a)
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)

Motherboard: Asus K8V SE DELUXE

I had a black screen problem just after the Ubuntu loading screen. A symptom of the problem is that the Xorg log does not get created. The kernel log does not provide anything usefull. The fglrx module loads without a problem.

Using the following in the Device section in the xorg.conf file got me 2d acceleration. 

 Option "nodri"

I eventually found out that the AGP aperture size in the BIOS setup was set wrong. I tried the highest value (256 MB) and the lowest (32 MB). They both did not work. The value that did work was 128 MB.

---

### Post by markbuntu on 2008-05-15
Hardy 8.04 386i LTS

lspci -n | grep 0300
01:00 0300 1002:9598

fglrxinfo
display:  :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc
OpenGL renderer string: ATI Radeon HD 3600 Series
Open GL version string: 2.1.7412 Release

from Xorg.0.log
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.471                    
(II) ATI Proprietary Linux Driver Build Date: Feb 25 2008 21:22:09

Video Card: VisionTek HD 3650 PCI Express, 
1GB Ultra High Speed DDr2 memory

Computer HP Pavilion a1330n Media Center
AMD Athlon64(s) 3800+  2.8GHZ
3GB PC 3200 400Mhz Ram
ATI Radeon Xpress 200M on board (disabled)
AC97 on board sound
320GB SATA (Ubuntu)
250GB SATA (XP)

I bought this card because I wanted to eventually install another monitor and my on board 200m did not support that.

What I did:

Installed the card and disabled the 200 in the bios. . Ubuntu saw the new card and installed the Vesa driver. No problem so far except the bios disabled the on board AC97 so I had to go in there and re-enable it, again, no problem.

 Installed the restricted driver to get acceleration and 3D and then the problems began. I spent a week trying everything everyone suggested everywhere. I eventually got Compiz working but it was through mesa and so the cpu was handling all the processing which became excruciatingly slow and crash prone. 

I eventually threw in the towel and reinstalled the entire Ubuntu system from scratch, a new clean install with the same cd I used for the original install. Then I got the latest  restricted drivers as you can see above and everything is absolutely perfect. I did not have to do ANY fooling around with anything.


fglrxdrm is handling the direct rendering
glxgears is reporting around 5000fps
Compiz works fabulously, fastest I have ever seen
cpu load is non-existent
very stable, even with firefox.

I wish I had done that a week ago.

just a little unrelated (I hope) problem with sound...


UPDATE:

bought my second monitor, a SOYO 24inch 1920x 1200. ATI Catalyst Control Center recognized it right off as a generic and got the modelines right but would not let me configure the 2 monitor setup. I could get the big desktop in the login screen but only clone anywhere else and when I tried to change the settings it all sorts of weird stuff would happen. Sometimes it would change the resolution and sometimes it wouldn't, sometimes it would change the left right configuration and sometimes it wouldn't. Sometimes it would just freeze up.

So, I did a new clean install and everything works great, even compiz though it does stress the processor with its indirect rendering.
btw, I had the sound problem fixed before I did this.

Now, if only I can drag my windows to the left...they get stuck at the edge of the extended viewport and won't go past it. But they go to the right all the way around the cube.

Update: Update : I accidentally reinstalled with an amd64 iso. Maybe that is why everything works so much better. compiz no longer uses 100% cpu when working...hmmmm...

---

### Post by lnpkural on 2008-05-18
@ first poster :lolflag:

My hardware : 

1) > 01:05.0 0300: 1002:4337
2) > 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

2.1) ```
ss@ss-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
```

3) Compiz now working with the Visual effect. But i tried hardly to find a solution.. The solution came from nowhere..

My current OS : Ubuntu 8.04 linux generic kernel (installed via a usb key):)
My laptop: HP Pavilion ze5300 (pretty old, but still working perfectly on a dual boot..Linux-XP, just the cdrom drive is at 75% broken, anyway it is a nice a laptop ! )

I installed Hardy yesterday. And i wanted some effects and 3d support, so I installed compiz and emerald but nothing was working, no effects, no 3d.

I was really disappointed. But as I'm a maniac and always looking for everything to get work, i tried to solve the problem, and succeed after struggling with my patience :popcorn: Now I'm so happy that i even created an account here to help people or give some tricky advices, and i so hope that it would help the ATI people, or at least the people with the same graphic card than me. 

My solution is : Install EnvyNG-gtk via the package manager. Run it writing "envyng -g" , then try to install the ati driver automatically, for the people with the same card than me but it will say something like "card not supported by the driver", so try the manual installation.. Boom, installation finished. Reboot.. I was not surprised to get a blank screen like. (But still you can configure , and select another driver)

So when you get this blank screen like, select by manufacturer "Ati - Radeon (fglrx)" and select Proprietary Driver (not opensource driver) then start. It will launch xserver normally, and you will be able to enter your username and password.

Now comes the tricky part. 

1.sudo gedit /etc/X11/xorg.conf 

In the device section change "fglrx" to "radeon"
In the monitor and screen sections change the resolution, by example to 1024×768

My current xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
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
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"radeon"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "1024×768@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024×768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"dri"
	Load		"v4l"
EndSection
[COLOR="Red"][B]Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	1
	Vendorname	"ATI"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection[/B][/COLOR]
Section "ServerFlags"
EndSection 
```

What is in bold red , IS USELESS. You can remove it. Save the edit and close gedit.

Now it is nearly finished, in order to get compiz and visual effects working you need to "whitelist" the open fglrx driver as it by default blakclisted in Ubuntu Hardy (its explain why i never had such a problem with previous Ubuntus) 

Enter this in a terminal : sudo gedit /etc/xdg/compiz/compiz-manager

and add this line ```
SKIP_CHECKS=yes

``` save and close gedit.

Now try to activate the visual effect , it should work ! Good luck to everyone who will try this method.

Linux rocks :guitar:
Windollar sucks :(

---

### Post by wootah on 2008-05-22
tripp@eclipse-desktop:~/Desktop$ lspci -n | grep 0300
02:00.0 0300: 1002:4152
tripp@eclipse-desktop:~/Desktop$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]

(*ATI Radeon 9600/x1050. It's a fanless AGP Saphire card*)

No real problems, got the ATI Propritary driver, followed instructions, updated Xorg (also installed the control centre) and had to fiddle with the TV-Out (listed below) settings.

9600/x1050 users that want composition might want to check out: [http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts]("http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts") as it talks about how to whitelist fglrx and some other issues/problems/fixes that might help get compiz-fusion rolling :)

Anyone having problems with TV-Out ? See this tutorial/howto: [http://ubuntuforums.org/showthread.php?t=803724]("http://ubuntuforums.org/showthread.php?t=803724")

---

### Post by kofing on 2008-05-24
> **guildofghostwriters said:**
> 1. 02:00.0 0300: 1002:4e48
2. 02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
3. I tried every method I could find here and elsewhere a few weeks ago and eventually gave up. I decided to try again today using the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) (which I had tried several times previously without success) and eventually got it working. The main 'tweak' was to remove my second monitor and forget about dual head because that just knackers it however I try to make it work. The only other thing I needed to do was, when following the instructions, at the point where I needed to edit xorg.conf, gedit wouldn't work because it said something about a screen not being available so I used nano instead. I suppose I should be wary of counting chickens because it's been running about 30 minutes so far but touch wood it seems to be okay so long as I don't try to extend my desktop onto that second monitor.

I have the same card (128MB). I can confirm that removing the second display fixed the white screen issue I was getting before. All I had to do was enable the restricted drivers after that.

---

### Post by josta7 on 2008-05-25
I have a ATI Radeon 2600 Pro.  
After much :-k ](*,), I was finally able to get everything working by using the newest (8.5) driver and this How-To:  [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)  WOOHOO!  (took me 3 weeks of forum-searching to even find that...makes sense b/c it was just edited today!)  Everything works like a charm now.  :):KS

---

### Post by oedha on 2008-05-26
mine :==> GigaByte GV-RX155128D-RH  ( RV505 )
and :==> on MSI K9AGM3-FIH Mobo...had an integrated ATIRadeon X1250 

to activate both :==> just enable ATI on hardware drivers ( to install xorg-driver-fglrx ) then reboot

walah....both of them are working good :)

---

### Post by cim on 2008-05-28
1. 01:00.0 0300: 1002:94c4

2. 01:00.0 VGA compatible controller: ATI Technologies Inc RV610LE [Radeon HD 2400 Series]

3. Method 2: Manual Method (installing Catalyst 8.5) 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by Beoran on 2008-06-05
Card: Radeon Xpress 1250 onboard on a Gigabyte motherboard.
Monitor: An old, old Vibrant, now TATUNG, conected by a VGA cable.
Guide:

Warning: this is a very radical solution that may be dangerous for your monitor. Don't try it unless you are desperate, and in the same case as me.

I installed the fglrx driver and rebooted, while my screen was connected to my old PC. I hot-plugged my monitor on the new Ubuntu system and all was looking well, even OpenGL was accellearted. But when I rebooted again, thistime with the monitor connected, I got thrown into low resulution mode. 

The X Windows log fields showed me that the fgrlx driver crashed every time with the dreaded PreInitDal Failed error. After reading around an checking many things, I realised that the problem was my moitor sending crappy EDID (monitor identification data) to the computer that the driver could not handle. So I would have to start every time with my monitor disconnected or completely powered down. Not good.

But, the EDID data is sent from the monitor to the PC through several wires and pins in the VGA cable, that are not used for anything else. In particular, pin number 15 on the VGA cable, that is, the one on the bottom most right hand side sends advanced data to the mnitor. So, I decided to disconnect that pin, so the EDID data cannot be sent.

To to this ,I kept a new VGA cable handy in case I screwed up. I shut down my computer, disconneted the power on my PC and my monitor, and disconnected my VGA cable on both sides. IMPORTANT, don't do it on a live computer! Then I took my wife's epilation pincer and grabbed pin nr 15 in the one of the heads of VGA cable. I slowely moved it from side to die , taking care not to damage the other pins, until finally after a few minutes, I jimmied it out. Then I used that fixed cable to connect the screen and the Ubuntu computer, and powered on eveything. And, voila, X  Windows started without any problems, because the EDID data was not sent anymore. 

On this web site you can see on the right hand side an example of an VGA cable layout, so you can understand which pin is pin nr 15.
[http://pinouts.ru/Video/VGAVesaDdc_pinout.shtml](http://pinouts.ru/Video/VGAVesaDdc_pinout.shtml)

As I said, this is a very radical solution. You should only need it if your monitor is sending bad EDID data. But I hope some people can be helped by this.

---

### Post by soxs on 2008-06-06
1) 01:00.0 0300: 1002:9501
2) ATI Technologies Inc Radeon HD 3870
3) Running the ati driver installer (8.5)
Tweaking:
Had to edit my xorg.conf to get proper video acceleration(the device section):
```
        Identifier      "RadeonHD3870"
        Driver          "fglrx"
        ## Driver / Performance Options
        Option          "XAANoOffscreenPixmaps" "1"
        Option          "TexturedVideo" "1"
        Option          "TexturedVideoSync"     "1"
        Option          "Textured2D"    "1"
        Option          "TexturedXRender"       "1"
        Option          "DRI"   "1"
        Option          "UseInternalAGPGART"    "1"
        Busid           "PCI:1:0:0"
```

---

### Post by molochi on 2008-06-10
1.) 01:00.0 0300: 1002:4e50
2.) mobile Radeon 9700 64MB
3.) 

a) Basic open ati drivers work as advertised after wubi install. (ie CompizFusion works fine. 3D/OGL games don't work at all.)
b) flgrx install causes black screen (after reboot) at(or slightly after) login. 
c) Boot into Gnome Safe mode, system ok.
d) uninstall proprietary drivers
e) reboot.

---

### Post by markbuntu on 2008-06-10
If you want or need the newest 8.5 driver from ATI you can download it from here:
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

The directions for installing it are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

This last thread tells you to set texturedvideo to "on" but I have found that by setting it to "off" the video players stop flickering (except for xine in a window) and everything plays normally.
The author claims that this disables the Xv direct rendering by my video card and shifts it over to indirect rendering by the cpu but I have not seen that.

I am using a Radeon HD3650 1GB card with 24 and 19 inch monitors in big desktop mode and miro plays HD just fine in a window or full screen with texturedvideo off and gstreamer selected instead of xine. All with compiz running.

Your mileage may vary.

---

### Post by MarkusIggy on 2008-06-16
1) 01:05.0 0300: 1002:5975
2) 01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
3) No tweaking needed. Worked with the restricted driver.

---

### Post by Mega_Mike on 2008-06-16
Using Ubuntu Hardy

1. 01:00.0 0300: 1002:7145
2. Output from fgrlxinfo:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.4 (2.1.7412 Release)

3.  To get the best performance for my card I had to use the following in Section "Device"
	Option	    "DRI" "true"
	Option	    "XAANoOffscreenPixmaps" "true"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
        Option      "Textured2D" "on"

---

### Post by matchstich on 2008-06-16
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)

 lspci -n | grep 0300
01:00.0 0300: 10de:0028 (rev 15)

---

### Post by Canis familiaris on 2008-06-20
I faced lots of problem of installing ATi drivers in Hardy but I managed to do so with the help of other forum members and searching which has been posted here:
[http://ubuntuforums.org/showthread.php?t=832698]("http://ubuntuforums.org/showthread.php?t=832698")

---

### Post by whiteguy1104 on 2008-06-27
> **soxs said:**
> Did you do that on a fresh install of feisty or did you have any drivers installed before?
Edit: Method 1 didn't work for me.
Edit: Method 2 didn't work either.
Edit: **[COLOR="DarkGreen"]Envy works like a charm![/COLOR]** ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

neither did mine i got a x1300 256mb agp

---

### Post by whiteguy1104 on 2008-06-27
01:00.0 0300: 1002:7142

i dont get it mine doesnt say any thing about the card. i have 8.04. help

---

### Post by L337_K3y5 on 2008-06-29
This is what I did to get my card to work:
1) 01:00.0 0300: 1002:9581
2) ATI HD RADEON 2600 (its in a laptop, but its a dedicated 512mb PCI-E card)
3)Not much tweaking needed (it works with indirect rendering with the driver which comes by default with Ubuntu)  I had to get it to work in direct rendering by checking the drivers in the restricted drivers section and restarting my comp.

---

### Post by whiteguy1104 on 2008-06-30
i tried just about all the things that the other radeon x1300 owners did but none of them worked now when i toggle fullscreen on my games it just goes to a big window mot fullscreen

---

