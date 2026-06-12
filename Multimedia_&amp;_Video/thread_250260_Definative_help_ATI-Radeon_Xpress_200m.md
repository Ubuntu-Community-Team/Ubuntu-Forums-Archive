---
title: "Definative help ATI-Radeon Xpress 200m"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by hatchek on 2006-09-03
I've been pulling my hair out for the last few days trying to get true hardware acceleration via the ATI Propreitary drivers (fglrx). I gave up on Gentoo because of the lack of support for the drivers. (infact, a user at the Gentoo forums posted and mentioned Ubuntu users were figuring it out better anyway). 

What I'm looking for is a step by step how to from the begining, noob-safe, "hey, I have an HP dv8000 and I got ATI drivers to work, this is how" on how to get my HP dv8000 laptop up and running with these drivers. The system specs, and stuff I think would be important to mention:
Latest Desktop Kubuntu CD installed. AMD64 (not x86)
AMD Turion 64, (my kernel options: acpi=off, otherwise eth0 doesn't start, install cd set me up with amd64-generic as the kernel)
ATI Radeon Xpress 200M (BIOS: UMA+Sideport)
lspci:
0000:01:05:0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

And before someone yells at me for omgsearchth3forums! Well, theres about 10 million topics for the same thing, so this is >>>HP dv8000

For what its worth, every step I've tried from various other topics always yields a blank screen and unresponsive X server. I have yet to get any version I've tried to not go black and actually be using fglrx. Is there any way to reboot the machine from this state without holding in the power button (and risking screwing up the hard drives)?

~edit: If it would make my life easier, should I switch to x86 instead of AMD64? Theres no ultimate reason I'm using amd64, I dont do crazy applications, so I'm using it just for the helluvit.

---

### Post by Ziox on 2006-09-03
I would suggest switching to x86, simply because there are more software compiled for it than 64 bits...and it might solve your graphics problem...

---

### Post by hatchek on 2006-09-04
Ok, I switched to the X86 version, and I have the same results. 

Its strange though, I was looking over Xorg.0.log.old file and it apparently things fglrx worked. ??

Here is a copy of my log file:
[http://www.bearcreekfire.com/zoids3d/downloads/Xorg.0.log.old](http://www.bearcreekfire.com/zoids3d/downloads/Xorg.0.log.old)

Some interesting parts of it:
```
 (II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.25.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7

```

```
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.25.18
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported

```

```
	[37] 0	0	0xb01203c0 - 0xb01203df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xc0715000 (size=0x078db000)
(II) fglrx(0): UMM area:     0x1e715000 (size=0x078db000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0

```

There are a ton of these making up the bulk of the log file:
XXX stands for some integer number from 0 to 254
```
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/cardXXX
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

```

These last few lines are most intriguing:
```
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete

```

I'd love to post some dmesg output, but I can't get ANYTHING to happen once x starts. I can't switch to another console, I can't do anything. However, there is harddrive activity and the keyboard LEDs still respond to events, so I know the kernel didn't crash.

At this point I am using the generic MESA thing so I do have (crappy) 3D but running glxgears I get this line:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
``` Sooo.... I guess its not really working all that well either.

---

### Post by mrunion on 2006-09-05
Though I'm no Linux Master, I spent the long weekend fighting an HP dv8000, AMD Turon 64 with an ATI X200 in it.  (The actual model is a DV8125nr I believe.)  I finally got it to work!

I am using the x86 kernel, not the AMD64 one.

I followed the instruction in this link, but READ BELOW for the changes I followed!!!

[Installing ATI Drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")

Use the instructions in the "Method 2" section (Method 2: Generating/Installing Ubuntu packages for the 8.28.8 drivers in Ubuntu Dapper Manually ) -- you'll have to scroll down the page a bit to find them.

Now -- and this is the part that made things work for me -- when it links to the 8.28.8 driver, DON'T USE IT!  Use the 8.24.8 driver.  You can download it from ATI's site, but they cleverly hid the old versions amongst a myriad of links. Use the navigation menu on the left to find the Linux Previous Dirvers section.

Follow the instructions in that section and substitute "8.24.8" for "8.28.8" in the commands.  Also keep in mind that you *may* have to edit your xorg.conf file when you are finished.  I checked mine and it appeared fine, but YMMV.

That worked for me!  I was installing drivers every which way from Sunday, but the problem was with the VERSION of the driver I was installing!!  Some would lockup, others would install, but NOT be accellerated.

If you have more questions, post back or send me a note.  I'll try to help you if I can!  (Keep in mind that I'm NOT a Linux guru!)

---

### Post by hatchek on 2006-09-11
Well, tried the posted procedure, and I got the blank screen.

I used 'radeon' instead of 'fglrx' and got a tad more performance, but its still no true hardware accel.

---

### Post by mrunion on 2006-09-15
Here is a copy of my xorg.conf file:

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
	Option	    "XkbLayout" "us"
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
	HorizSync    28.0 - 72.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900"
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

I apologize, but I don't know how to get glxgears to show me the frames per second.  I do know that hardware accelleration is working because before installing the drivers, neverball (3D putt putt game) would be so slow it couldn't work and after it plays just fine.

---

### Post by almahtar on 2006-09-15
Hatchek - I have an HP ZV6130US, and for ages I was getting the same problem as you - everything looks like it works in the logs, but I still get the blank screen and a freeze.

What fixed it for me was completely disabling the sideport memory in bios.  Go all UMA.  I shared 128 MB, and my 3D works - I'm sure one can get away with sharing less though.

Give it a shot, tell me how that goes.

Oh, and I'm using the 8.26.18 drivers and they're working great.  I may try to switch to the 8.28.8 for the heck of it this week.

---

### Post by Stochastic on 2006-09-16
Just out of curiosity, how can you tell if 3d accelleration is working?  I've got fglrx installed and running with this card but I'm a complete noob when it comes to video.  Thanks.

---

### Post by hatchek on 2006-09-16
You can test your 3D by checking either glxgears (if it actually runs) or perhaps using Gnome/KDE's openGL (3D) screen savers. 

If you're using glxgears every so often it will print out a frame rate. If you are using the Mesa Indirect rendering (the default thing X11 uses) you'll get frame rates in the low to mid 100s. If you have true 3D working (with like the ATI drivers) you should see frame rates in the thousands. Or atleast, very close.

Running fglrxinfo will output what system your 3D is running on. If you have working ATIness, It would output something like: Vendor: ATI Technologies FireGL.. or something. Otherwise you'll see Mesa Indirect, mesa3d.org-- something along those lines.

@ almahtar: I was going to try that but I figured, I've only got 512mb total system RAM, and the card has 128 non-shared video memory. So.. I think I'll just stick it out until the better drivers get released. Not to mention, the computer dual boots with XP, so have it work fully for atleast one of em.

---

### Post by Ziox on 2006-09-16
use **glxinfo | grep direct** to see if direct rendering is on

---

### Post by almahtar on 2006-09-18
Yeah, I feel your pain there: that extra 128 MB makes a huge difference.  I think I'll try just sharing 32 and see how that works out: I don't need 128 MB of video ram if I'm not playing games, and I don't.

---

### Post by almahtar on 2006-09-18
*Update* I just installed the newest kernel update and the newest 8.28.8 drivers, and switched my shared mem down to 32 and it worked just fine.  So now I have 3D Accell and still have 472 MB of main memory.  Joy.

Hatchek, you may not want to wait until there's support for the oncard mem - it's been a known issue for over a year now and still no progress.  I don't think it's really a priority for ATI since these aren't really high end cards and most people don't run Linux on them anyway :-\

---

### Post by weematt on 2006-09-21
There are a few of us out here that are unable to disable sideport.  In my situation, my bios only provides me with the following options:

sideport only
sideport + shared main memory

I'm happy to share main memory if it gets DRI working...but here is my problem:

I've gotten the driver 8.28.8 working in 2D, and according to various logs, I have even got hardware DRI working, however when DRI is enabled, the screen is garbled.  Transparent areas of windows look corrupted, and when I try to test glxgears, it hangs hard.  I have seen one user report similar garbled ugly trash messed up windows in this situation, but I haven't heard of any solutions (except disableing hardware 3d acceleration* (not exactly a solution).

* by setting Option "no_dri" to "yes"

Any tips would be greatly appreciated! 

Thanks,

Matt

---

### Post by Ragnarol on 2006-09-22
I have exactly the same problem as you, weemat.

I was able to make it work with an old driver version (I think it was 8.23) but this version does not work with latest kernels :(

Do you know if its just our problem or the X200 don't work with the new drivers for noone?

Good luck!

---

### Post by mrjoe on 2006-09-22
> **weematt said:**
> 
I've gotten the driver 8.28.8 working in 2D, and according to various logs, I have even got hardware DRI working, however when DRI is enabled, the screen is garbled.  Transparent areas of windows look corrupted.

I have the same problem with my HP Pavilion dv8000. I'm using Gentoo amd64.  Have no solution for now. Here is [photo]("http://i113.photobucket.com/albums/n231/prepeta/IMG_3925.jpg") of my screen. I will try older drivers or install some 32bit linux disto to see if 64bit is the problem.

---

### Post by David Valentine on 2006-09-22
For what it's worth, I have the Xpress 200 embedded in my MSI RS480 mobo.  I get all the right info> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8 )
and> $ glxinfo | grep direct
direct rendering: YesHowever, glxgears churns out something like 40 fps at full screen, which is quite poor to the same machine under Breezy.  I've been a bit frustrated in figuring out why that is, although it seemed to speed up when I specified "noapictimer irqpoll" as a boot option in GRUB.

---

### Post by Ragnarol on 2006-09-23
> **mrjoe said:**
> I have the same problem with my HP Pavilion dv8000. I'm using Gentoo amd64.  Have no solution for now. Here is [photo]("http://i113.photobucket.com/albums/n231/prepeta/IMG_3925.jpg") of my screen. I will try older drivers or install some 32bit linux disto to see if 64bit is the problem.

I was able to made it work with 8.24 drivers, but it wasn't still perfect. Vegastrike hangs a lot while playing, however I don't know if the problem was the driver or the game.

The problem of 8.24 drivers is that it don't work with latest kernel version.

Please, let us know if you have success with x86 drivers. Thanks!

---

### Post by mrjoe on 2006-09-23
Tried x86 Ubuntu using fglrx-8.29.6-1_i386 driver. I can log in to the system but gnome hangs up after 4-5 secs.
Cannot post dmesg output or something else because whole system is unresponsive.
This time I get no "transparent" buggy windows like with amd64 kernel. But 3D still not usable :(.

Also older 8.27 driver is not working correctly. Haven't tried 8.24.

To contact ati's linux and request fix the problem visit [https://support.ati.com/](https://support.ati.com/). I post a support request ticket today. Hope they will respond someday.

---

### Post by trekkypj on 2006-09-23
Okay, just to pass on my own experiences...

I'm using a HP Pavilion dv5157eu with the Radeon X200M chip, with sideport+uma enabled and 128mb on board/128mb shared memory as the setting in the bios. 

(Edit: Using the i386 version of Dapper, NOT amd64)

Using the 8.24.8 drivers works for this model, no problems. Just tested ET and Neverwinter nights with it so it should be fine.

A pity the newer drivers don't work though. :(

Thanks to all who worked on getting this solution together. I was beginning to think I'd have to forget about 3d altogether!

---

### Post by steveyos666 on 2006-09-23
I've got a Compaq Presario V5101US, which also has the Radeon Xpress 200m.

I've never gotten this thing to work, no matter how many different drivers, or ways to install them I've tried. I've tried using guides and typing lots of code into the terminal, I've tried things that do it automatically, I've tried to get stuff right from ati.com, I've even asked on some forums.

So maybe the 200m's just not getting much love? This laptop can't run games, but it should be able to run the net and instant messengers and stuff. It all ran fine with Windows, but Ubuntu just crawls like it's dying no matter what I try.

So, to the people who have figured it out: Is there a 100% noob-friendly guide out there? For someone who doesn't know jack about Linux/Ubuntu. I'm so sick of Windows, but every time I reinstall Ubuntu to give it another go I just can never get it going fast, or get wireless working which also really sucks. And then everyone I talk to expects me to magically know all the lingo and such like I learned it in grade school. :/

---

### Post by Melcar on 2006-09-23
I have a 200M on my laptop and I have installed and uninstalled ATI drivers several times, all being successful.  
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

---

### Post by steveyos666 on 2006-09-24
f@FBI-laptop:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

:(

---

### Post by Ragnarol on 2006-09-24
> **trekkypj said:**
> Okay, just to pass on my own experiences...

I'm using a HP Pavilion dv5157eu with the Radeon X200M chip, with sideport+uma enabled and 128mb on board/128mb shared memory as the setting in the bios. 


We have exactly the same configuration!

Which kernel version are you using? Drivers 8.24 don't work for mine (2.6.15).

I had a good idea, it is trying to update the bios version. In HP website you can find a new version of our bios. Maybe updating it will allow to choose just UMA memory for the card. I couldn't test it as I don't have Windows installed and the patched didn't work with cedega.

Please, try if you can and let me know!

Thanks!

---

### Post by trekkypj on 2006-09-24
I'm using the latest Ubuntu kernel from synaptics... version 2.6.15.27 I think. Also, confirming that I used v8.24.8 of the ATI drivers.

I tested it with NWN and with Enemy Territitory. Works fine with high settings in both games. NWN crashes very occasionally but it does that in Windows too so I reckon that's a game config issue.

*> EDIT: I believe I've solved the NWN crash... apparently there's a memory leak when playing with ATI cards that requires a patch of the game, rather than the ATI driver :D .*

I did update the bios a while back but not sure if it's the latest revision.

If you're interested, I did a guide outlining the way I went about installing the drivers. It's not perfect but it worked for me. Most of it is just repeating the ati drivers wiki instructions...

[My dv5157eu ati install method]("http://www.minds.may.ie/~trekkypj/weblog/ubuntu-dapper-drake-ati-driver-solution-for-hp-pavilion-dv5157eu/")

---

### Post by Ragnarol on 2006-09-24
Thanks,

But sadly we are not using the same configuration. I am getting the following error when modprobing de module:

fglrx: Unknown symbol no_iommu

The error I told that I had when using newer kernels, looks like a problem that ati fixed in subsequents release.

I think it is just an error un amd64 kernels... so maybe it will be worthy to change to x86... I don't know if 3d accel worth it...

I know that I should bought an nvidia laptop!

Cheers,

---

### Post by trekkypj on 2006-09-24
Ah.

Well I am using the x86 version... it works fine. *shrug*

I think that if you look for the AMD64 version of the ATI drivers it'll work. THe names of the modules are slightly different in the commands but otherwise fine.

Having said that, I haven't done it myself. Read it on one of the wiki pages I think.

---

### Post by Jiilik on 2006-09-24
Solution:

For fglrx and this card (200M)

In xorg.conf, add the lines:
```
Section "Extensions"
    Option "Composite" "false"
EndSection
```
Then DRI will be enabled, and therefor FireGL for 3D support.

For fglrx versions up to the current one 8.28.8, Composite + DRI = BOOM!

So you have to pick one or the other, and since DRI being disable means 3D is done by Mesa - I'd suggest disabling Composite.

(I'm on amd64 with this video card)

---

### Post by steveyos666 on 2006-09-24
Can anyone put all of this into English?

I don't speak linux yet!

---

### Post by Ragnarol on 2006-09-25
> **steveyos666 said:**
> f@FBI-laptop:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

:(

Steveyos,

Your problem is that you already have the ATI section in your xorg configuration file. You can try to start with a new one (you have backups, haven´t you?) or force ati config to create an additional secction.

I don't remember what option is for that, probably --force or -f or something similar, check ati-config help for it, and let us know if you were able to fix it.

Jiilik, I will try your fix when I get to home, currently I am at work... I will keep my fingers crossed :)

Thanks,

---

### Post by steveyos666 on 2006-09-25
aticonfig?


```
f@FBI-laptop:~$ aticonfig
Usage: aticonfig [OPTION] ...
Parses an existing X-Server configuration file and modifies it to operate with
ATI products.

The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
           NTSC-M
           NTSC-JPN
           NTSC-N
           PAL-B
           PAL-COMB-N
           PAL-D
           PAL-G
           PAL-H
           PAL-I
           PAL-K
           PAL-K1
           PAL-L
           PAL-M
           PAL-N
           PAL-SECAM-D
           PAL-SECAM-K
           PAL-SECAM-K1
           PAL-SECAM-L
        Note: Not all graphics cards support every mode. Regional
              settings are applicable.
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV
 --tv-overscan={on|off}
       Enable or disable overscan mode for TVout
       Note, not all tv-formats support overscan. Try to
       toggle overscan off before changing tv-format if
       and error occurs.
 --tv-info
         Print out the current tv geometry, tv format, and if the
         tv is physically connected.
 --tv-geometry=WIDTHxHEIGHT{+|-}X{+|-}Y
              =WIDTHxHEIGHT
         Change the size and position of the TVout display.
         WIDTH and HEIGHT are in percentage units. Please note
         that the valid range for WIDTH and HEIGHT depends on
         the tv-format selected. However, as a rule of thumb
         WIDTH and HEIGHT are valid in the range [1,100]
         X and Y are pixels offsets from centre
         of the screen. X and Y are have variable ranges dependant
         on ASIC. Use tv-info to get valid X and Y ranges
         If tv-geometry is invoked with just width and height
         then X and Y are assumed to be 0
         See example 5 below for a sample usage.

FireGL Workstation Board Features:
  --app, --use-app-profile=STRING
        Change the application profile for a FireGL workstation board.
        STRING can be one of:
            default
            maya
            softimage-xsi
            softimage-3d
            houdini4.0
            houdini5.0
            houdini5.5
FSAA Options:
  --fsaa={on|off}
        Enable/disable full scene anti-aliasing.  Enable this option to enhance
        photo-realism in 3D rendering.  Disable it to get the most accurate 3D
        image.
  --fs, --fsaa-samples={off,0,2,4,6}
        Set the number of FSAA samples per pixel or 2, 4, 6.  off is the same
        as setting 0 samples.
  --fsg, --fsaa-gamma={on|off}
        Enable/disable FSAA gamma.
  --fmsp, --fsaa-ms-positions=x0,y0,x1,y1,x2,y2,x3,y3,x4,y4,x5,y5
        Change the FSAA Multi-Sample Positions for x0,y0 to x5,y5.  You must
        specify exactly 12 real number values separated by commas.

Screen-Related Options:
  --ovt, --overlay-type=STRING
        Change the overlay for the X server.  STRING can be one of:
            opengl
            Xv
            disable
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
        or stereo.
  --lcd, --lcd-mode=STRING
        Change the LCD mode.  STRING can be one of:
            center
            full
  --dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
                                Note: This option is NOT supported with Avivo
            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
            horizontal          2 screens - one framebuffer,
                                screen 1 right of screen 0
            horizontal,reverse  2 screens - one framebuffer,
                                screen 1 left of screen 0
            vertical            2 screens - one framebuffer,
                                screen 1 above of screen 0
            vertical,reverse    2 screens - one framebuffer,
                                screen 1 below of screen 0
        Note:  This option is not valid if '--initial=dual-head' is specified.
  --vs, --sync-vsync={on|off}
        Enable/disable sync buffer swaps with vsync.  Enable this option to
        prevent tearing during 3D rendering.
  --psc, --pseudo-color={on|off}
        Enable/disable pseudo-color visuals.  Enable this option to get 16-bit
        color support.
  --stereo={on|off}
        Enable/disable quad-buffer stereo support.  Enable this option only for
        using applications that support the use of hardware 3D shutter glasses.
  --ss, --stereo-sync={on|off}
        Enable/disable quad-buffer stereo sync.  Enable this option to get 3D
        glasses to synchronize with the infrared transmitter.
  --resolution=Screen#,W1xH1,W2xH2,W3xH3,...
        Set the modes for the specified screen.  You may specify several
        resolutions separated by commas.
        Screens start at 0.  You can use 1 for dual-head
  --hsync=Screen#,LOW-HIGH
        Change the horizontal sync range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --vrefresh=Screen#,LOW-HIGH
        Change the vertical refresh range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --hsync2=LOW-HIGH
        Change the horizontal sync range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --vrefresh2=LOW-HIGH
        Change the vertical refresh range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --mode2=W1xH1,W2XH2,W3xH3,...
        Change the modes for the second display.  You may specify several
        resolutions separated by commas.  Only valid for clone and big desktop
        settings.
  --screen-layout={left|right|above|below}
        Set the secondary screen position for dual head.
  --screen-overlap=NUM
        Set the screen overlap region in big desktop mode to be NUM pixels.
  --force-monitor=STRING[,STRING...]
        Describe all displays that are to be enabled and/or disabled regardless
        of physical connection.  STRING can be one or more of the following
        set, separated by commas:
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            tmds2i
            nocrt1
            nocrt2
            nolvds
            notv
            notmds1
            notmds2
            notmds2i

POWERplay Options:
  Following options will not change the config file.
  These options will be effective immediately. Other options on
  the same command line will be ignored.
  --lsp, --list-powerstates
        Print information about power states and exit.
  --set-powerstate=NUMBER
        Set a power state listed by --list-powerstates.

Advanced Options:
  --tls={on|off}
        Enable/disable fast thread local storage.  Disable this option when
        virtual machines or WineX fail to work properly.
  --sb, --signal-block={on|off}
        Enable/disable signal blocking.  Disable this option when debugging a
        multi-threaded OpenGL application.
  --locked-userpages={on|off}
        Enable/disable locked user pages. Disable this option if the system
        hangs when running fgl_glxgears.
        User page lock is no longer available on AGP system now.
  --gcpu, --generic-cpu={on|off}
        Enable/disable generic CPU.  Use this option if the CPU is being
        reported improperly.  For example: If you have an AMD cpu that is
        being reported as Intel.
  --max-gart-size=NUMBER
        Set user-defined max GART size for non-AGP systems.
        Possible integer values are from 64 to 512 (mb).

Dynamic Display Management Options:
  Following options will not change the config file. They are
  used for querying driver, controller and adaptor information.
  These options will be effective immediately. Other options on
  the same command line will be ignored.
  --enable-monitor=STRING,STRING
        Setting current monitor to be enabled. Only 2 displays
        can be enabled at the same time. Any displays
        that are not on the list will be disabled.
        STRING can be one of the following set, separated
        by commas:
            none
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            auto   -- use default policy to enable the displays.
  --query-monitor
        This will return connected and enabled monitor information
  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.

Pair mode options:
  Following options are used for query add and remove pair modes.
  These options will be effective immediately. Other options on
  the same command line will be ignored.
  --list-pairmode
        list all the current existing pair modes the driver can use.
  --add-pairmode=width0xheight0+width1xheight1
        Add one pair mode to the list. width0 and height0 are the
        size of primary display and width1 and height1 for the
        secondary  display.
  --remove-pairmode=index
        Remove one pair mode from the list. User can get index by
        list-pairmode.

External Events Daemon Options:
  Following options will not change the config file. They are
  used to send commands to the atieventsd external events daemon.
  --set-policy=STRING
        Sets the event policy for the daemon to be STRING.
        See the atieventsd(8) manpage for further details.

Miscellaneous Options:
  -v, --verbose
        Show what aticonfig is doing.
  -q, --quiet
        Disable all information output except for errors.
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  --nobackup
        Do not make an automatic backup of the configuration file.
  -i, --input=FILE
        Select a FILE to input as the configuration file. Set FILE to '-' to
        pipe from standard input.  Without this option, aticonfig will search
        /etc/X11 for the default configuration file.
  -o, --output=FILE
        Select a FILE to output the new configuration file to.  Set FILE to '-'
        to print to standard output.  Without this option, aticonfig will
        replace the input file with the newly generated file.
  -h, --help
        Display this help screen.
  -f, --force
        Only valid with 'initial' option.  Force aticonfig to generate default
        Monitor, Device, and Screen sections even if the original configuration
        file has invalid settings in these sections.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768
  4. Force primary CRT on and TV-out off.
                        aticonfig --force-monitor=crt1,notv
  5. Change tv geometry
                         aticonfig --tv-geometry=85x90+10-10
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre.

Please report bugs to http://support.ati.com

```


I need some translation here, I'm used to this all being a lot easier. All I can make out of this is [IMG]http://www.madtvstore.com/ProductImages/Hot-Dog-T-Shirt-2-B.jpg[/IMG]

All I want is for my computer to not slow down, browsing the **INTERNET**!



EDIT: Oh, also, I'm not getting any sound on flash-type-sites like homestarrunner.com and .swf files kill my computer dead.

---

### Post by Ragnarol on 2006-09-25
> **Jiilik said:**
> Solution:

For fglrx and this card (200M)

In xorg.conf, add the lines:
```
Section "Extensions"
    Option "Composite" "false"
EndSection
```
Then DRI will be enabled, and therefor FireGL for 3D support.

For fglrx versions up to the current one 8.28.8, Composite + DRI = BOOM!

So you have to pick one or the other, and since DRI being disable means 3D is done by Mesa - I'd suggest disabling Composite.

(I'm on amd64 with this video card)

Well, I have tried it without success.

Could you post you xorg.conf just to check that I didn't miss anything?

The behaviour of the system is exactly the same. It hangs and hangs when starting up, Ubuntu gnome splash screen shows without borders and it hangs before starting. Nothing is written to Xorg log.

Which version of kernel and xorg are you using Jiilik?

Thanks,

---

### Post by Ragnarol on 2006-09-25
Steveyos,

I mean that you should type the following:

sudo aticonfig --initial --force

Probly you are getting this error because you have already go through the howto. You don't need to apply this step every time you install a new version of the drivers.

What this step does is modify your XOrg (xorg is the windows system) configuration file to use the driver for the display. Once you do that the configuration file has changed and you don't need to do it again.

What is your problem exactly?

good luck,

---

### Post by steveyos666 on 2006-09-25
I typed that and got:

f@FBI-laptop:~$ sudo aticonfig --initial --force
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2


And well, I still got the problem. I don't know if that was supposed to solve it, but yeah.

You know how when you play a graphically-intense pc game, say Prey for example, and if your pc isn't powerful enough you'll have crappy frames per second? Well I get crappy frames per second on .swf/flash/browser-type-whatever games. You know, stuff that any computer can handle. They all ran fine with Windows installed, so it's not like this computer can't handle them.

I believe I've got Flash 7, which is the latest I can find for Ubuntu, even though 8 or 9's out for Windows. So maybe it's just because browser games are all upgraded or something? I'm not sure if everything is slow because of the ATI driver, or Flash, or something else. I'm pretty good with Windows, but I've never had to type in all these lines of codes and stuff to solve any problems.

To me it seems that when you switch to Linux, you get rid of .exe, but you get a whole bunch of new problems. My attention span isn't good enough for all these guides. I want Ubuntu to work so bad but my brain's broken. :(

But then again, I guess I'm not alone with the 200m. I believe my next laptop will have the Nvidia logo on it.

---

### Post by Ragnarol on 2006-09-25
Steveyos,

If your problem is with flash games I am almost sure that it hasn't anything to do with your ati card/drivers.

I can't figure out which problem could be... have you tried searching a bit but using flash as keyword, not ati?

Don't throw the towel. Usually fglrx drivers works quite well with the ones provided by ubuntu, that is if not a weird problem appears, as it is our case (not yours, i hope :)).

It could sound like a poor excuse, but the problem is not with linux, but with companies that don't support it, and do not assign resources for linux drivers, like ATI does.

Nvidia has a much better support in linux Drivers, the only reason why I have an ATI is because I couldn find a nice Nvidia laptop...

Good luck with your flash games!

Have you tried Enemy Territory? It is a free online game with 3d graphics. If works ok for you your problem is not, 99% sure, the ATI driver.

good luck again,

---

### Post by steveyos666 on 2006-09-26
Oh I'm definitely not quitting Ubuntu, I'm just waiting it out, letting stuff like Automatix and EasyUbuntu develop some more. I can't do the terminal stuff, I don't have the attention span for guides.

If you mean Wolfenstein's Enemy Territory, I doubt this laptop could run it. And if you do mean that, and it'd have to be installed with Wine, well I can't even get Wine installed. This laptop's junk anyway, I'm just saving up and I'll make sure my next laptop's got Nvidia, since it seems to be the favored card on this side of the fence.

But as far as this laptop goes, with the 200m, I'd need older drivers? If you can't just install stuff on top of stuff like on Windows, I'd reinstall Ubuntu if that'd help. I don't have anything on here anyway.

---

### Post by Melcar on 2006-09-26
ATI drivers work fine on the 200M, even the new ones (at least the 32bit version).  And yes, you have to uninstall older drivers before installing new ones; usually you just have to remove all the older .deb files.  This guide tells you how to uninstall or at least get rid of old .deb files (this is what I used when I upgraded from the 8.28.8 drivers to the 8.29.6 ones):
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by trekkypj on 2006-09-26
> **steveyos666 said:**
> Oh I'm definitely not quitting Ubuntu, I'm just waiting it out, letting stuff like Automatix and EasyUbuntu develop some more. I can't do the terminal stuff, I don't have the attention span for guides.

If you mean Wolfenstein's Enemy Territory, I doubt this laptop could run it. And if you do mean that, and it'd have to be installed with Wine, well I can't even get Wine installed. This laptop's junk anyway, I'm just saving up and I'll make sure my next laptop's got Nvidia, since it seems to be the favored card on this side of the fence.

But as far as this laptop goes, with the 200m, I'd need older drivers? If you can't just install stuff on top of stuff like on Windows, I'd reinstall Ubuntu if that'd help. I don't have anything on here anyway.

Enemy Territory works fine for me, really nippy actually.

And I'm using the old 8.24.8 drivers. What's your machine spec, besides the graphics?

I have a 1.8Ghz Turion64 with a gig of ram, but 128 of that is 'diverted' into shared memory for the ATI so fglrx won't crash/set the laptop on fire :D

If you have the option to do a reinstall, install the x86 version as I don't know how to get the drivers to work for amd64

---

### Post by Ragnarol on 2006-09-26
I give another try with latest drivers, 8.29.6, but still the same...

AAAAGGGGGHHHHH ](*,)

---

### Post by mrjoe on 2006-09-26
> **Ragnarol said:**
> I give another try with latest drivers, 8.29.6, but still the same...

AAAAGGGGGHHHHH ](*,)

I downloaded new driver (8.29.6) today.
Enabled DRI. 
Typed startx [-o< ....
Correct windows showed up .... But after few seconds X crashed #-o
Same error like x86 driver.

I also tried
```

Section "Extensions"
    Option "Composite" "false"
EndSection

```
but no success.

Jiilik can you send us your kernel and xorg configuration? I would wery thankful for that.

UPDATE:
No crash but buggy semitransparent norefreshing windows again :-/

---

### Post by Ragnarol on 2006-09-26
I am currently using sideport+uma, anyone with the same config?

I asked for bios updates because I think that maybe without using card memory it will work... that could explain that it dont work with just card memory and almost work with sideport+uma ;)

By induction, it should work with just main memory 8)

---

### Post by mrjoe on 2006-09-26
> **Ragnarol said:**
> I am currently using sideport+uma, anyone with the same config?

I asked for bios updates because I think that maybe without using card memory it will work... that could explain that it dont work with just card memory and almost work with sideport+uma ;)

By induction, it should work with just main memory 8)


Sideport+uma too. My notebook is HP dv8000.

---

### Post by steveyos666 on 2006-09-27
> **Melcar said:**
> ATI drivers work fine on the 200M, even the new ones (at least the 32bit version).  And yes, you have to uninstall older drivers before installing new ones; usually you just have to remove all the older .deb files.  This guide tells you how to uninstall or at least get rid of old .deb files (this is what I used when I upgraded from the 8.28.8 drivers to the 8.29.6 ones):
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

If they work fine, why does this thread exist? :-k 

I'll try that link anyway, I think I've tried everything else anyway so it's worth a shot.

EDIT: Eh, that link's already in this thread. I don't see the part you're talking about on there either. Could you tell me where it is on that page?

> **trekkypj said:**
> Enemy Territory works fine for me, really nippy actually.

And I'm using the old 8.24.8 drivers. What's your machine spec, besides the graphics?

I have a 1.8Ghz Turion64 with a gig of ram, but 128 of that is 'diverted' into shared memory for the ATI so fglrx won't crash/set the laptop on fire :D

If you have the option to do a reinstall, install the x86 version as I don't know how to get the drivers to work for amd64

Compaq Presario V5101US
Mobile AMD Sempron 3300+ 2.0GHz
512 MB RAM

^Which basically means 'crap' but with a more professional look.

---

### Post by trekkypj on 2006-09-27
Hmm, maybe you could get more memory... never any harm and it isn't crippling these days.

Try setting the shared video in the BIOS to 64mb... I think someone got it working on that setting.

ET is not that much of a hog, provided 3d is working correctly. You should get a decent framerate and good graphics at least.

If you just want 3d to work, like I do, install the 8.24.8 drivers because 9/10 times they work no hassle on any laptop with a x200m chip. The other ones I cannot get to work and there's loads of issues depending on the machine and the version of the drivers, far as I can make out.

---

### Post by steveyos666 on 2006-09-27
> **trekkypj said:**
> Hmm, maybe you could get more memory... never any harm and it isn't crippling these days.

Try setting the shared video in the BIOS to 64mb... I think someone got it working on that setting.

ET is not that much of a hog, provided 3d is working correctly. You should get a decent framerate and good graphics at least.

If you just want 3d to work, like I do, install the 8.24.8 drivers because 9/10 times they work no hassle on any laptop with a x200m chip. The other ones I cannot get to work and there's loads of issues depending on the machine and the version of the drivers, far as I can make out.

I'm not putting any money into this laptop, I'm just saving up for a better one. And yeah, I've played ET a few times before, on other computers. But I'm still having problems with the basics, so I'm not even close to ready to start with Wine and all that.

And as far as the drivers go, I guess I still need to uninstall them. I couldn't find what that other guy was talking about on that link, but I followed the first part again and it still says:

f@FBI-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

And I guess that shouldn't say mesa3d.


EDIT: I switched it to 64mb, maybe that'll help once I get the drivers installed.

---

### Post by MalReynolds on 2006-09-27
I have the same laptop (Compaq v5101us).
I installed Kubuntu and I was able to get video 8.28.8 working using:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

I'm a total newb at Linux and hate the command-line.
Using Automatix I got Wine, DVD, Adobe, and a bunch of other goodies working.  Oh, wireless too.  That took a while.

If you want to get rid of that laptop let me know. :)

Scott

---

### Post by steveyos666 on 2006-09-27
> **MalReynolds said:**
> I have the same laptop (Compaq v5101us).
I installed Kubuntu and I was able to get video 8.28.8 working using:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

I'm a total newb at Linux and hate the command-line.
Using Automatix I got Wine, DVD, Adobe, and a bunch of other goodies working.  Oh, wireless too.  That took a while.

If you want to get rid of that laptop let me know. :)

Scott

I just tried that link, no luck. I installed it on my desktop though, didn't know that was gonna happen.

f@FBI-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

f@FBI-laptop:~$ cd /home/f/Desktop
f@FBI-laptop:~/Desktop$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


Says the same thing in both directories anyway.

As far as getting rid of the laptop, if the warranty would let me, I could switch it for a brand new one. If you'd be willing to pay, let me know. I'm dying to switch over to Nvidia.

---

### Post by Ragnarol on 2006-09-29
I have updated my laptop bios, but without success. 

Now it is a bit more stable, but still crash after a few minutes.

I was hopping that the new bios allow me to use just UMA memory for the card, but this option is still not available for me.

Do you have any luck, guys?

---

### Post by steveyos666 on 2006-09-29
I still haven't even gotten the drivers installed :D

I'm just giving up until I get a new laptop with an Nvidia card.

---

### Post by Melcar on 2006-09-29
> **steveyos666 said:**
> If they work fine, why does this thread exist? :-k 

I'll try that link anyway, I think I've tried everything else anyway so it's worth a shot.

EDIT: Eh, that link's already in this thread. I don't see the part you're talking about on there either. Could you tell me where it is on that page?




Remove any old fglrx debs from /usr/src/: 

sudo rm /usr/src/fglrx-kernel*.deb

Of course, it also helps if you remember the location where you unpacked the original .deb files so you can remove those too.

---

### Post by steveyos666 on 2006-09-30
> **Melcar said:**
> Remove any old fglrx debs from /usr/src/: 

sudo rm /usr/src/fglrx-kernel*.deb

Of course, it also helps if you remember the location where you unpacked the original .deb files so you can remove those too.

Apparently, I didn't even install anything there.

f@FBI-laptop:~$ sudo rm /usr/src/fglrx-kernel*.deb
Password:
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory

It'd be nice if the guides told you where to install things, because if I have to download something that isn't through the terminal, it goes right to the desktop.

Well:

f@FBI-laptop:/usr/src$ ls
fglrx-kernel-source.tar.gz  linux-headers-2.6.15-27
linux                       linux-headers-2.6.15-27-386


I do got that. ](*,)

---

### Post by Rob_H on 2006-10-01
Bonus question for HP Pavilion dv8000 owners: Does anyone have an xorg.conf example that mirrors/clones the laptop LCD display on an external monitor? Ideally, I want the external display at 1280x1024 or 1024x768 so I can give presentations. But every time I try to configure this, the desktop area displayed on the monitor is too big and ends up scrolling when I move the mouse pointer, while the display on the LCD panel seems to be at its normal resolution. How do I "optimize" the display for the external monitor? Thanks.

---

### Post by Ragnarol on 2006-10-02
I have my laptop configured to use a cloned external TFT screen.

External screen is working at 1680x1050 while laptop screen is working at 1280x800, but Desktop is set to 1680x1050 so I need to scroll the screen using the mouse on desktop.

Using gnome resolution manager, if I set screen resolution to one that both screens support it works perfect.

Is this what you want? If it is, I will post my xorg.conf file when I arrive home (currently at work).

---

### Post by Ragnarol on 2006-10-02
Now my bonus question. how can I switch off the laptop screen while having the external one working?

If I close laptop screen both screen go black...

---

### Post by Rob_H on 2006-10-02
Yes, please post your xorg.conf file. I'd like to look. I am actually using Kubuntu, so I will have to see if there is a KDE equivalent that works. Are you intentially runnuning the desktop at 1680x1050? Have you tried lower resolutions?

> **Ragnarol said:**
> Now my bonus question. how can I switch off the laptop screen while having the external one working?

Adding the following line to the "Device" section of xorg.conf will do it. (Although I don't know what will happen if you close the lid.)

```
  Option  "ForceMonitors" "crt1,nolvds"
```

Similarly, you can enable just the laptop display like this:

```
  Option  "ForceMonitors" "nocrt1,lvds"
```

You can have aticonfig generate these lines using the "--force-monitor" argument instead of adding them manually if you want. Unfortunately, I haven't found a way to dynamically switch between active displays without restarting X. The Fn+F4 combination doesn't work. So what I've done is modified the GRUB menu to let me pick the xorg.conf at boot time via the XORGCONFIG environment variable.

---

### Post by sosokeys on 2006-10-02
TEST!

You can test your 3D by checking either glxgears (if it actually runs) or perhaps using Gnome/KDE's openGL (3D) screen savers. 

If you're using glxgears every so often it will print out a frame rate. If you are using the Mesa Indirect rendering (the default thing X11 uses) you'll get frame rates in the low to mid 100s. If you have true 3D working (with like the ATI drivers) you should see frame rates in the thousands. Or atleast, very close.

Running fglrxinfo will output what system your 3D is running on. If you have working ATIness, It would output something like: Vendor: ATI Technologies FireGL.. or something. Otherwise you'll see Mesa Indirect, mesa3d.org-- something along those lines.

@ almahtar: I was going to try that but I figured, I've only got 512mb total system RAM, and the card has 128 non-shared video memory. So.. I think I'll just stick it out until the better drivers get released. Not to mention, the computer dual boots with XP, so have it work fully for atleast one of em.

---

### Post by Ragnarol on 2006-10-02
> **Rob_H said:**
> Yes, please post your xorg.conf file. 

Here you have

---

### Post by Rob_H on 2006-10-02
Thank you! Although after writing that message, I tinkered with the config some more and finally got the effect I needed: 1024x768 on both the laptop panel and the external monitor. Perfect for presentations. If anyone's interested, here are the relevant parts of xorg.conf:

```

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

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Centermode" "off"
	Option	    "Mode2" "1024x768"
	Option	    "DesktopSetup" "clone"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
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
		Modes    "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



```

---

### Post by jhawk on 2006-10-04
switch to 8.24.8 faster x 3 and full console support. I would be on it except for xorg ver 7 and kernel

---

### Post by Ragnarol on 2006-10-09
Well, I have swithced back to x86 arch. I installed drivers version 8.24 and everything is fine now! 

This driver version works much better in x86 than in amd64.

I am having some problems with Cedega, games hanging and thinks like that... anyone else?

Also after switching to x86, but using my same xorg.conf when playing films in the external monitor (thanks Rob_H!! it worked) the resolution is not set to the screen resolution.

This worked before, but not now :(

---

### Post by rssaddict on 2006-10-15
Hi all, just wanted to report back from the front on this one:

I got 3D working on a presario r4125 with a Radeon Xpress 200m, with the latest drivers (8.29.6) and Ubuntu Edgy (kernel 2.6.17-10-386).

I followed the installation instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually") , using method 2.

This resulted in a crash and a black screen, no matter which driver version I tried.  I finally got it working by switching to all UMA memory in the BIOS.  Pity I have to sacrifice system RAM to get this thing working, and can't crank it up to 256, but hey, it works.

---

### Post by Juzz on 2006-10-16
Hiyas,

Is anyone else experiencing (or has experienced) some weird flickering of the screen while running nothing in particular?

On this notebook I get some flickering from time to time - it is very quick almost as if the picture on the screen was of rubbery paper and it got pulled.

My setup:
Ubuntu 6.06
Medion MD96400
AMD turion ML 1.6GHz
1GB of RAM (of which 128 mb has been set aside for gfx)
ATi 200M graphics from the chipset - running the 8.24.8 drivers from ATi
RT61 Wireless networking builtin
12.1" widescreen display

The flickering was also present last time I tried my luck with linux on this notebook, but I don't quite know what is causing it.

Regards
Juzz

---

### Post by Juzz on 2006-10-19
Has anyone got a working Config.wtf for World of Warcraft that you're using on your ATi 200m system?
With a plain start Config.wtf the game locks up just after loading.

---

### Post by Ragnarol on 2006-10-27
Anyone has been able to make this card work with xgl/compiz?

I have been trying but when I start using the xgl server systems hangs in a way similar to when I use a driver newer than 8.24: it works for a while but with some corrupted graphics, and after a minute or so system hard hangs :(

I would like to know your experiences...

Thanks!

---

### Post by Ragnarol on 2006-10-27
Edgy has arrived. I updated my system to Edgy and... bad news guys.

Fglrx 8.24 does not work with the default kernel, or at least it doens't worked for me :(

That means that I am again without DRI, with fingers crossed waiting for a new and working driver version.

Please, let me know if any of you is able to make the drivers work with the x200m in Edgy.

Compiz has to wait...

---

### Post by Rob_H on 2006-10-27
> **Ragnarol said:**
> Edgy has arrived. I updated my system to Edgy and... bad news guys.

Fglrx 8.24 does not work with the default kernel, or at least it doens't worked for me :(

That means that I am again without DRI, with fingers crossed waiting for a new and working driver version.

Same here. Kinda wish I'd waited to upgrade now.

---

### Post by nbound on 2006-10-28
tried install the restricted modules? (the one that ends in generic should be good for a plain install) :D

---

### Post by Ragnarol on 2006-10-28
The problem is that version 8.24 of the driver doesn't compile with the newest kernel, We should have to wait till the next driver :(

---

### Post by skatedawe on 2006-10-28
Im having the same problem as juzz, with the flickering problem.

maybe this helps: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Edgy_Manually) 

for all of us?

---

### Post by hatchek on 2006-10-28
I noticed this problem only seldomly, but sometimes I'll get this wierd effect where theres 3 simultaneous copies of my screen just out of phase with eachother, by about 1 inch. And they seem to roll or flicker. Kinda hard to describe. If I switch from X to another console and then back again (Ctrl+Alt+F#) it usually goes away. 

But no luck lately with the drivers.

---

### Post by mrjoe on 2006-11-01
Tried latest 8.30.3. No success. Only blank screen when using sideport only. Mixed colors when using sideport+uma (128+128 shared). At least I can reboot this time (ctrl+alt+backspace , ctrl+alt+delete).

------ Xorg.0.log ------ 
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.18-suspend2 x86_64
Current Operating System: Linux turion 2.6.18-suspend2 #12 Tue Oct 17 01:31:22 CEST 2006 x86_64
Build Date: 16 October 2006
.........
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib64/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(1): === [atiddxPreInit] === begin, [s]
(EE) fglrx(1): Quitting secondary screen -- no monitor specified.
(EE) fglrx(1): PreInit failed
(II) fglrx(1): === [atiddxPreInit] === end

Backtrace:
0: X(xf86SigHandler+0x71) [0x48bea1]
1: /lib/libc.so.6 [0x2b8f07ee05d0]
2: /usr/lib64/xorg/modules/drivers/fglrx_drv.so(atiddxDriverEntPriv+0xf) [0x2b8f08ef984f]
3: /usr/lib64/xorg/modules/drivers/fglrx_drv.so(atiddxFreeScreen+0x2b) [0x2b8f08efeb8b]
4: X(xf86DeleteScreen+0x5b) [0x49f2ab]
5: X(InitOutput+0xa15) [0x45f7c5]
6: X(main+0x26f) [0x430e5f]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b8f07ece134]
8: X(FontFileCompleteXLFD+0xa1) [0x430339]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by Rob_H on 2006-11-01
As I suggested in another thread, if you're as unhappy as I am with the "fglrx" driver, make some noise at ATI. Report the bug through their web site. They may ignore you with a canned response, as they did with me, but if more people complain about the same issue, maybe someone will pay attention.

---

### Post by mrjoe on 2006-11-02
Good idea. If everybody send them bug report maybe they will correct this 200M bug. I send them bug report once a month. I think I have submitted them bug report 3 or 4 times but with no response. But I'm sure that I will never buy notebook or PC with their video card again. Who want's to exchange his notebook with me ;)

---

### Post by Ragnarol on 2006-11-07
Anyone else have tried the latest drivers 8.30?

I haven't yet, I am a bit busy this days, I will try to test them this weekend. But it would be nice to know if you guys (especially those that have success just with 8.24 like me) have found any improvement in this version.

Thanks,

---

### Post by mrjoe on 2006-11-07
I tried them. Still buggy

---

### Post by Ragnarol on 2006-11-29
No luck with 8.31 neither. :(

---

### Post by angel12 on 2006-12-11
first time posting to this forum, but i have been trying to get my x200 working with ubuntu for the past 8 months, off and on. Im now trying to use it on Edgy, and i have tried the latest drivers, 8.31.5-1, and i get the same results i have been every time i have tried to use the propriety drivers. a blank screen when x starts. i dont have the option to turn off the onboard memory completely, just uma+sideport.

---

### Post by Rahiim3 on 2006-12-11
Just installed Edgy; 
1. how do I check which version of the display driver for ati 200M?
2. Can't find the 8.24 driver
Toshiba laptop celeron M/ ATI radeon x200m
thanks

---

### Post by Ragnarol on 2006-12-12
I'm afraid that 8.24 drivers doesn't work with Edgy. I think the problem is Xorg version.

---

### Post by bofphile on 2006-12-13
Good news,

With the new ATI drivers (8.32), I can now use only Sideport memory (128Mb).
The performance are much better than before:
```
5179 frames in 5.0 seconds = 1035.641 FPS
5287 frames in 5.0 seconds = 1057.340 FPS
5279 frames in 5.0 seconds = 1055.549 FPS
5236 frames in 5.0 seconds = 1047.040 FPS

```
I can't believe they fixed this problem!!!!

---

### Post by angel12 on 2006-12-13
so the brand new drivers work with the video ram? no more sharing? what about xgl/compiz?

---

### Post by Ragnarol on 2006-12-13
Also working for me!!!!

Only sideport and DRI enabled!

Looks like it is still a bit buggy, if I ctrl+alt+backspace and  try to start the session again Gnome dont work, but the system doesn't hang.

I will try XGL tomorrow.

The others have had any luck?

---

### Post by Kilg0re on 2006-12-13
wow, i've been waiting for this.
I'll try it out tonight

---

### Post by marcele on 2006-12-14
Well here are my results ( I have a hp dv8210ca with this horrid video card):

Previous Driver (8.31.5):
1. Bug with Bigdesktop (if second monitor has resolution larger than the first.. then mouse pointer gets misaligned on the main monitor)
2. Bug with Xinerama (if you move the mouse to the second monitor it turns into a blob of the first monitor)
3. With Composite disabled black screen on boot (UMA video memory)
4. With Composite disabled hard lock on login (UMA / Sideport memory)

New driver (8.32.5)
1. Bug with Bigdesktop (if second monitor has resolution larger than the first.. then mouse pointer gets misaligned on the main monitor)
2. Bug with Xinerama (if you move the mouse to the second monitor it turns into a blob of the first monitor)
3. With Composite disabled **DRIVER WORKS** (UMA video memory)
4. With Composite disabled **DRIVER WORKS** (UMA / Sideport memory)

---

### Post by angel12 on 2006-12-14
so xgl/ compiz? and do you have the option to just run it off of sideport?

---

### Post by mrjoe on 2006-12-14
> **Ragnarol said:**
> Also working for me!!!!

Only sideport and DRI enabled!

Looks like it is still a bit buggy, if I ctrl+alt+backspace and  try to start the session again Gnome dont work, but the system doesn't hang.

I will try XGL tomorrow.

The others have had any luck?

Finally :D. Works with sideport+uma and also with sideport only.

---

### Post by lnxusr on 2006-12-14
I can confirm these drivers (8.32.5) are working great with XGL/Beryl, Runs smooth and is so far stable on my HP Pavilion DV5212us w an ATI Xpress 200M with sideport mem. Looks like the AMD/ATI acquisition may be paying off. Now if only they'd add AIGLX support!

For anyone who wants to get these drivers working, the following scripts will download/install/build and configure them for you:

Dapper:
[http://lnxusr.phpnet.us/ati-8.32.5-builder.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder.sh)
Edgy:
[http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh)
(both scripts have been tested and are confirmed working on their respective distro versions)
Once downloaded, run chmod +x <script filename> then sudo ./<script filename>
If you have any trouble, let it be known.

You may have to put the following lines in your xorg.conf file to enable 3D acceleration on Edgy:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```
I hope this becomes a trend at ATI, releasing good drivers that is. Hope this helps my fellow ATI victims :D

---

### Post by Ragnarol on 2006-12-14
Beryl also working for me.

This is the first time I see Beryl in action... :)___

---

### Post by lnxusr on 2006-12-14
> **Ragnarol said:**
> Beryl also working for me.

This is the first time I see Beryl in action... :)___

Wait'll they release drivers supportive of AIGLX, Really a massive performance increase over XGL, and it also  runs games seamlessly, even on my nvidia 5200. My games seem to run fast on XGL, but with really weird texture problems, playable, but they look really strange, oh well it works, and now I can show off Linux + XGL/Beryl on-the-go :D

---

### Post by angel12 on 2006-12-15
jease, it only took them a couple of years to get it right no? 

now if only they would open their drivers up...

---

### Post by lnxusr on 2006-12-15
> **angel12 said:**
> jease, it only took them a couple of years to get it right no? 

now if only they would open their drivers up...

A big step forward for ATI I'm sure :D From what I've read, AMD is strongly considering opening up the drivers. Guess us Linux people are lucky AMD took over, Maybe they'll open the Windows drivers too and make my tech support life that much easier.

---

### Post by hatchek on 2006-12-15
@lnxusr: Nice.

However, after running the Dapper script, I still have errors with hardware acceleration. Here is the relevant part of /var/log/Xorg.log.0 :

```

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb6ed9000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb6ed9000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x20000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 7291
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "(null)" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(**) fglrx(0): Video overlay enabled on CRTC1

```

Kernel Source isn't the right version?

---

### Post by Toolbelt on 2006-12-16
I have been following this thread with much interest.  I have a dv8000 laptop with an ml37 processor and X200M video.  I upgraded to Edgy and am on a 2.6.17-10-386 kernel.  I have been trying to get the 8.32.-5 driver to load and have been unsuccessful to this point.  I followed method 2 (multiple tries) and for some reason it fails (no noteworthy errors).  Right now I am trying via the script that was posted just recently in the forum, I suspect that will fail too......I need "definitive help"

---

### Post by Toolbelt on 2006-12-16
No joy on the script either......the Ubuntu Edgy installation guide suggest that not having gcc 4.0 could be an issue....gcc 4.1 is what is loaded, I removed it before I ran the script and the script reloaded it.

---

### Post by danboy on 2006-12-16
ToolBelt..

I just successfully installed the 8.32.5 drivers on my dv8000, the script didn't work for me, but if you install all the debs it povided, run..
sudo m-a prepare,update
sudo m-a build,install fglrx

and add the following to you xorg.conf..
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

and

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

you should be cool after restart.

i was even able to disable UMA for the first time..

/Danboy

---

### Post by Toolbelt on 2006-12-16
More work ....and success!

First, I realized that fglrx wasnt loading, so I added it to the /etc/modules

then, I went into the /etx/X11/xorg.conf file and added this section:

Section "Module"
	Load  "dri"  #.....in addition to other loads already in this section
EndSection

Section "DRI"
	Mode         0666
EndSection



Dont ask me what mode 0666 means, maybe someone here can give me the meaning?

---

### Post by scrivener on 2006-12-16
The Edgy script didn't work for me.  I needed to change this line:
**dpkg -i xorg-driver-fglrx_8.32.5-1_i386.deb fglrx-kernel-source_8.32.5-1_i386.deb fglrx-control_8.32.5-1_i386.deb**

To this:
**dpkg -i xorg-driver-fglrx_8.32.5-1_amd64.deb fglrx-kernel-source_8.32.5-1_amd64.deb fglrx-control_8.32.5-1_amd64.deb**

When I rebooted I didn't have 3D.  I checked my Xorg log at /var/log/Xorg.log.0 and had similar errors to what hatchek reported except mine showed 28.8.  To fix this I went into Synaptic and marked the package **linux-restricted-modules-2.6.17-10-generic** for complete removal.  

Then I navigated to /usr/src and reinstalled **fglrx-kernel-2.6.17-10-generic_8.32.5-1+2.6.17.1-10.34_amd64.deb** with gdebi (right click > Open with GDebi...).  Then I rebooted and I was all set.  fglrxinfo showed that I was using the ATI driver 32.5.  glxinfo showed that I had direct rendering enabled.  fgl_glxgears is showing 200+ fps, but the sides of the box are white. 

I'm working with this on Edgy (amd64) on an HP Pavilion zv6015us laptop with ATI Radeon Xpress 200M graphics.

EDIT:  The 3D doesn't seem stable with UMA enabled.  My system froze when I was playing with the screensaver settings.  (I could only move the mouse and had to use the power button to reboot.)  After disabling UMA and only using Sideport everything is working as expected.  I'm getting better FPS without UMA and no more white sides on the fgl_glxgears box.

---

### Post by Kilg0re on 2006-12-16
Everything is working fine for me the way I have it setup.
Beryl is really amazing, I can't wait to see what people will come up with next.

The only thing is I have not been able to log in to a XGL session with UMA / Sideport memory.
UMA only works fine.

---

### Post by Rob_H on 2006-12-19
OMG PONIES!

Finally, 3D acceleration WORKS with the 8.32.5 driver! I have the Radeon Xpress 200M on an HP Pavilion dv8000. 3D acceleration/DRI has not worked since version 8.24.8, which I was forced to abandon after upgrading to Edgy. But now it is working again. Here's what I did:

(1) Followed the Edgy Method 2 instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.32.5_drivers_in_Ubuntu_Edgy_Manually").
(2) Ran **aticonfig --initial --force**. For some reason, direct rendering would not work with my existing xorg.conf even after upgrading the driver.

Next challenge, get dual-head working.

EDIT: By the way, I just have Sideport RAM enabled in the BIOS now. Previously, I had to enable Sideport+UMA or else I'd get a black screen and lock-up.

---

### Post by d-E-a-D on 2006-12-19
Just follow [http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m) 

And you can get Radeon 200M, Xgl and beryl full working on edgy

Cumps

---

### Post by Saviq on 2006-12-25
Hey, what about the dual-head setup? Did You get it working?

---

### Post by Rob_H on 2006-12-25
> **Saviq said:**
> Hey, what about the dual-head setup? Did You get it working?

Yes, no more garbled mouse pointer on the second screen either.

---

### Post by agbloomfield76 on 2006-12-27
Relative Ubuntu newbie -- trying to get Beryl to work on my HP dv8240us, ATI Radeon Xpress 200M.

Downloaded, compiled, and installed ATI's flgrx latest driver.  Seems to run fine; glxgears runs smoothly, but never tells me FPS.  Following instructions from this thread (and others), created menu options for glx session.

Boots into it, but never allows me to use Beryl.  If I run beryl-manager, it kicks out with an error "11".  Running glxgears in the glx session is much slower, and it complains of a missing x86Free module.

I'm thoroughly confused.  Is it an AMD64 problem?  I know there's an i386 patch for the ATI driver; is there a workaround for the x64?  I'd love to have this working!

---

### Post by scrivener on 2006-12-27
I have an AMD64 HP laptop too and I get the same "11" error message.  

To check if the drivers are working try running  fgl_glxgears.  I get about 240 fps.

---

### Post by Rob_H on 2006-12-27
> **agbloomfield76 said:**
> Relative Ubuntu newbie -- trying to get Beryl to work on my HP dv8240us, ATI Radeon Xpress 200M.

I have the same exact model laptop, and it is working for me with the newest ATI drivers under Kubuntu Edgy.

Since you mentioned the AMD 64, I assume you are running the 64-bit version of Ubuntu. I'd strongly recommend just running the 32-bit version. Whatever modest performance gain you get by running 64-bit will be more than offset by driver and other software problems, especially on a laptop. You might be seeing an example.

---

### Post by hatchek on 2006-12-29
Still not 100% working here.

After following instructions [http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m) there, (just the top half) I've still have no hardware acceleration, and a curious error in the log file: (highlighted with #'s, about halfway down)

```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) Loading extension ATIFGLRXDRI
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)

#alot of repeating crap removed here

drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb72fe000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.32.5
(II) fglrx(0):     Date: Dec 12 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.17-10-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x20000000 FBMappedSize: 0x00715000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,1261)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - a
ssumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 357
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
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
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): Interrupt handler installed at IRQ 209.
(II) fglrx(0): Exposed events to the /proc interface
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:1:5:0

############
#This is the Error#
############

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727) 
(EE) AIGLX: reverting to software rendering

(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy

```

---

### Post by Rob_H on 2006-12-29
> **hatchek said:**
> Still not 100% working here.


It looks like you're trying to use AIGLX. I don't think it's compatible with the proprietary ATI drivers. Use XGL instead.

---

### Post by hatchek on 2006-12-29
I wasn't going for Beryl, I just needed instructions for setting up the fglrx driver... Anyway,
I've got rid of the AIGLX error by adding a few lines to Xorg.conf:
```
 
Section "ServerFlags"
   Option "AIGLX" "Off"
EndSection

```

But For some reason its still reverting to Mesa, though Xorg.log.0 says its been initiated.

(II) fglrx(0): [DRI] Installation complete

but then it goes to loading GLcore..
(II) Loading local sub module "GLcore"
...
...
(II) GLX: Initialized MESA-PROXY GL provider for screen 0

While digging through the Xorg log, I have not come across any other errors.

---

### Post by Rob_H on 2006-12-29
Hatchek,

Have you tried using a "clean" xorg.conf? Make a backup of your copy and then run:

```
sudo aticonfig --initial --force --overlay-type=Xv
```

Then reboot.

---

### Post by Ragnarol on 2007-01-12
Any improvements with version 8.33?

---

### Post by hatchek on 2007-01-21
I've finally figured out what was going on here.

Apparently, I left out the Section "DRI" Mode 0666 thing in my xorg.conf file.

So after I added that, and removed the code to turn AIGLX off, It uhhh.. worked!

I rebooted, looked at the ATI Control thing in my task menu, and it said OpenGL provider: ATI.

So ... hooray! Finally 3D acceleration with dv8000 notebook using ATI Radeon Xpress 200M.

Here is xorg.conf 
```


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
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
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "drm"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

#Section "ServerFlags"
#	Option	    "AIGLX" "Off"
#EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
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
	BusID "PCI:1:5:0"
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
	Option	    "Composite" "Disable"
EndSection

Section "DRI"
	Mode 0666
EndSection



``` :KS

---

### Post by scrivener on 2007-01-22
Beryl/XGL works on my AMD64 laptop with the latest version of Beryl (0.1.99) and the 8.32.5 ATI driver.  In case anyone was wondering. :)

---

