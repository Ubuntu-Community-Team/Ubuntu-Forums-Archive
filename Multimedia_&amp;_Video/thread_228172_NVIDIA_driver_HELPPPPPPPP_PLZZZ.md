---
title: "NVIDIA driver HELPPPPPPPP PLZZZ"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by Goldilocks on 2006-08-02
Hello everyone
I am a newcomer to linux. Installed Ubuntu Dapper (default kernel) a week ago. Everything was nice except the nvidia driver issue.
i have an NVIDIA geforce 6600 gt agp graphics card along with a VIA MB
with integrated graphics. The graphics card works fine with the default driver that comes with ubuntu. But i wanted to test the nvidia propriety drivers n this is where everything goes wrong. I have followed tseliot's guide for driver installation n used both methods but same thing happens in both cases.
As soon as i install the drivers and run

sudo nvidia-xconfig

upon x server restart the monitor goes blank. The green light changes to orange as though its not gettin any signal but the hard disk's led keeps blinking showing some activity . The screen returns as i change "nvidia" to "nv" in xorg.conf in the recovery mode. There seems 2 b some conflict b/w the nvidia drivers n the inbuilt graphics. 

my present xorg.conf is 



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
	Load	"i2c"
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
       #Option          "NvAGP"       "1"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107E"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"PHILIPS 107E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


The output of 

lsmod | grep agp

is 


agpgart                34888  1 nvidia


i have blacklisted agpgart n via_agp. Changed "nv" to "nvidia" and
"NvAGP" to 0/1/2/3 but still the problem remains the same.

Any suggestion will be highly appreciated.

---

### Post by E-werd on 2006-08-02
Do you still have your original xorg.conf that Ubuntu installation made backed up?  If so, try backing up your current configuration and using the original configuration, but changing "nv" to "nvidia" in the "Device" section.

If you don't have your original configuration, try running:

sudo dpkg-reconfigure -phigh xserver-xorg



Now, assuming you've run the following command:

sudo aptitude install nvidia-glx

You should be able to just change "nv" to "nvidia" in the "Device" section of xorg.conf and work fine.  That is all I did to get mine working.

Here are my specs, FYI:

Athlon XP 2200+ 266Mhz FSB
80gb WD HDD
nVIDIA GeForce 6600 256mb DDR
Gigabyte GA-7VKML motherboard
512 MB PC2700 Memory


Best of luck to you. :D

---

### Post by Goldilocks on 2006-08-02
Yeah well i have already tried that n a lot of other things too.But its not making it work.BTW thanx for the suggestion. I hope they keep coming becoz i really want to make my graphics card work.

---

### Post by inkapyrite on 2006-08-03
>upon x server restart the monitor goes blank.

it might be because your lcd can't handle the refresh rate on your graphics card. That blank screen happened to me when i installed my nvidia drivers. Here's how i fixed it:
 
 [http://www.ubuntuforums.org/showthread.php?t=221313&page=2](http://www.ubuntuforums.org/showthread.php?t=221313&page=2)

Just a reminder:

check what horizSync and vertRefresh rates your philips monitor can handle first. Two ways of doing it: 
1. look at your monitor manual for the refresh rates for the resolution that you want 
2. (more reliable imho) when using 'nv' drivers, directly check what the refresh rates are being used (how? buttons on monitor that lets you adjust contrast/brightness etc will probably have an option that displays the information on the current refresh rate) 

copy these values to the horizSync and vertRefresh entries. 

and remember to set the Option "UseEdidFreqs" to "False".



Fingers crossed. It just might solve your problem!;)

---

### Post by Lord Illidan on 2006-08-03
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#Load	"dri" You don't need this!
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvida"
	BusID		"PCI:1:0:0"
       #Option          "NvAGP"       "1"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107E"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"PHILIPS 107E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
Try this xorg.conf

---

### Post by tseliot on 2006-08-03
Try point 4 of the problems section of my guide

---

### Post by Goldilocks on 2006-08-03
I have tried inkapyrite's n lord illidan's suggestions but they dont work for me. Yes i also tried the point 4 of problem section yesterday but that didnt work either. The problem is the same. Blank screen as soon as x tries to load with nvidia drivers n one thing more i can not hear any welcoming sounds which r usually played during login with default drivers. No progress so far. I still think my via integrated graphics have got something to do with it but they dont make any conflicts with the default driver.

Now i have restored my original xorg.conf n removed any blacklistings. ANYONE NOW HELP ME FROM HERE ON.

---

### Post by tseliot on 2006-08-03
> **Goldilocks said:**
> I have tried inkapyrite's n lord illidan's suggestions but they dont work for me. Yes i also tried the point 4 of problem section yesterday but that didnt work either. The problem is the same. Blank screen as soon as x tries to load with nvidia drivers n one thing more i can not hear any welcoming sounds which r usually played during login with default drivers. No progress so far. I still think my via integrated graphics have got something to do with it but they dont make any conflicts with the default driver.

Now i have restored my original xorg.conf n removed any blacklistings. ANYONE NOW HELP ME FROM HERE ON.

Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

I know that you don't have an Intel card. For this reason you should type:
```
lsmod
```

and see if you have a module which ends with "_agp". You should use that instead of "intel_agp" in step 3 of that guide

---

### Post by Goldilocks on 2006-08-03
Thanx tseliot but i have tried that too. i have blacklisted via_agp n done the rest but still the same problem. i know my graphics card n monitor are fine becoz they work perfectly in windows. All i have been doing for the last two days is trying 2 make the nvidia drivers work but they dont. Any other suggestion???

---

### Post by tseliot on 2006-08-03
try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Goldilocks on 2006-08-03
I think i owe u all a thanx. U all r gr8 ppl. I finally got my graphics card working. After doing everything i could find in these forums, i thought it was never goin 2 work with the propriety drivers. In the despair i made one last hard try. I flashed my inno 3d 6600gt bios with a PNY 6600gt bios. It worked like magic. Everything worked without any tweaking. The reason i have found 2 be a fault in inno's bios. On my windows despite being an agp 8X card, my card was always listed as PCI-e 16X. I never knew the reason though. Taking a look at Xorg.0.log i found that it was the same thing where nvidia drivers would struck.

(II) NVIDIA(0): Bus detected as PCI Express
(II) NVIDIA(0): Detected PCI Express Link width: 16X

and i knew there was only one hard cure 2 it n i flashed it. Think it will help other ppl 2 who r havin same blank screen on startup n no suggestion seems 2 work. Thanx everyone u r gr8.:grin:

---

