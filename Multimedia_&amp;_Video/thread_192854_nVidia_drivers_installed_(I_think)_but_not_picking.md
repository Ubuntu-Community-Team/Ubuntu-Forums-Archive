---
title: "nVidia drivers installed (I think) but not picking up Graphics Card"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by Blademaestor on 2006-06-09
Hi,

Wonder if anyone can help, only just started using ubuntu and have installed the nvidia drivers using synaptic but device manager comes up with:

(Device tab)
Vendor: nVidia Corporation
Device: Unknown (0x00f5)
Status: Status
Bus type: PCI
Device Type: Unknown
Capabilities: Unknown

(PCI tab)
Vendor: nVidia Corporation
Product: Unknown (0x00f5)
OEM Vendor: XFX Pine Group Inc.
OEM Product: Unknown (0x2201)

The video card I have is a AGP XFX Geforce 7800GS extreme edition.
Any idea's why its not picking up the card and how to remedy this?
Thanks

---

### Post by Brynster on 2006-06-09
when yopu first boot do you seen the Nvidia logo splash screen?

If not then the driver will not be installed correctly. I personally struggled with this until i tried Automatix which installed it effortlessly. I heartily recomend it for the Nvidia driver.

Props to Arnie boy, MistlyEvil and all for such a first class product.

---

### Post by taurus on 2006-06-09
Don't forget to either restart X, <Ctrl><Atl>Backspace, or reboot...

---

### Post by tseliot on 2006-06-09
[QUOTE=Blademaestor]Hi,

Wonder if anyone can help, only just started using ubuntu and have installed the nvidia drivers using synaptic but device manager comes up with:

(Device tab)
Vendor: nVidia Corporation
Device: Unknown (0x00f5)
Status: Status
Bus type: PCI
Device Type: Unknown
Capabilities: Unknown

(PCI tab)
Vendor: nVidia Corporation
Product: Unknown (0x00f5)
OEM Vendor: XFX Pine Group Inc.
OEM Product: Unknown (0x2201)

The video card I have is a AGP XFX Geforce 7800GS extreme edition.
Any idea's why its not picking up the card and how to remedy this?
Thanks[/QUOTE]
That's nothing to worry about.

Please post the output of the following commands:
```
dmesg | grep NVIDIA
```

```
glxinfo | grep direct
```

---

### Post by Blademaestor on 2006-06-09
These are the responses I get:

dmesg | grep NVIDIA

[4294683.015000] nvidia: module license 'NVIDIA' taints kernel.
[4294683.392000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006

glxinfo | grep direct

direct rendering: Yes

Just did a reinstall as something messed up (sorry for the technical terminology) and everything froze up, and then ubuntu wouldnt load afterwards,once again i let ubuntu update everything first then installed the nvidia drivers using "method 1" from the guide at the top of this topic this time, I get the splash screen but it still doesnt appear to recognise the card through device manager.

Thanks for the help so far

---

### Post by tseliot on 2006-06-09
[QUOTE=Blademaestor]These are the responses I get:

dmesg | grep NVIDIA

[4294683.015000] nvidia: module license 'NVIDIA' taints kernel.
[4294683.392000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006

glxinfo | grep direct

direct rendering: Yes

Just did a reinstall as something messed up (sorry for the technical terminology) and everything froze up, and then ubuntu wouldnt load afterwards,once again i let ubuntu update everything first then installed the nvidia drivers using "method 1" from the guide at the top of this topic this time, I get the splash screen but it still doesnt appear to recognise the card through device manager.

Thanks for the help so far[/QUOTE]
The driver works. As I've said before, the fact that device manager doesn't seem to detect your card properly doesn't mean anything (this is not Windows).

Trust me, I have a bit of experience in this field ;) 

Enjoy your driver and don't worry about device manager :) 

Regards

Alberto

---

### Post by Blademaestor on 2006-06-09
Thanks for the help Alberto and all and I will :D

---

### Post by nicjasno on 2006-06-10
I get the same taints kernel message.

But glxinfo doesn't work at all. Also, when doing this:

> 
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config-enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop


the sudo nvidia-glx-config-enable command didn't work. Now whatever i do, x won't start.

---

### Post by fmo on 2006-06-10
Open your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

you should have a section that looks like this one

```
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"        
        Driver         "nv"
        BusID           "PCI:1:0:0"
EndSection

```

replace the 
```
Driver     "nv"
```
by
```
Driver     "nvidia"
```

if it doesn't work reverse the change using the command line (if it doesn't work you should loose X)
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by nicjasno on 2006-06-10
I have my driver already set to nvidia, not nv. And X doesn't work. Doesn't work with nv setting either.

When doing

```

sudo apt-get install nvidia-settings

```

I get this:

```

dpkg- can't mmap package info file '/var/lib/dpkg/available no such device
E: sub-process /usr/bin/dpkg returned an error (2)

```

My xorg file is as follows:

```

Section "Files"
      	FontPath	"/usr/share/X11/fonts/misc"
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
	#Load	"dri"
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
        Identifier    "Logitech"
        Driver        "evdev"
        Option        "CorePointer"
        Option        "Dev Name"        "Logitech USB Receiver"
        Option        "Dev Phys"        "usb-*/input0"
        Option        "Device"        "/dev/input/event1"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
        Option "Renderaccel" "On"
        Option "IgnoreDisplaydevices" "DFP,TV"
        Option "NoRenderextension" "On"
        Option "Accel" "On"
        Option "AllowGlxWithComposite" "off"
EndSection

Section "Monitor"
        Identifier     "CTX LCD monitor"
	Option	       "DPMS"
	HorizSync      31.5 - 64.3
	VertRefresh    50-70
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor     "CTX LCD monitor"
    DefaultDepth 24
	
Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen          "Screen 1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Logitech"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection


```

---

### Post by fmo on 2006-06-10
I modified your xorg.conf, tried with this one and don't forget to make a backup of yours before please.

```

Section "Files"
      	FontPath	"/usr/share/X11/fonts/misc"
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
        Identifier    "Logitech"
        Driver        "evdev"
        Option        "CorePointer"
        Option        "Dev Name"        "Logitech USB Receiver"
        Option        "Dev Phys"        "usb-*/input0"
        Option        "Device"        "/dev/input/event1"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
        #Option "Renderaccel" "On"
        #Option "IgnoreDisplaydevices" "DFP,TV"
        #Option "NoRenderextension" "On"
        #Option "Accel" "On"
        #Option "AllowGlxWithComposite" "off"
EndSection

Section "Monitor"
        Identifier     "CTX LCD monitor"
	Option	       "DPMS"
	#HorizSync      31.5 - 64.3
	#VertRefresh    50-70
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor     "CTX LCD monitor"
    DefaultDepth 24
	
Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen          "Screen 1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Logitech"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection
```

---

### Post by nicjasno on 2006-06-10
Ok, at least i get an error message now:

```

(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia


(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

```

Here's the output of 

```

dmesg | grep nvidia

```

```

Module license 'NVIDIA' taints kernel

```

and

```

glxinfo | grep direct

```

```

glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared 
object file: No such file or directory

```

---

### Post by fmo on 2006-06-10
ok, by the looks of it you are missing the module of the driver.

Did you install the "linux-restricted-xxx" modules that go with your kernel?

---

### Post by nicjasno on 2006-06-10
Double post.

---

### Post by nicjasno on 2006-06-10
Hm... i think not.

My kernel is linux 2.6.15.23-386, how do i install them?

```

sudo apt-get install linux-restricted-2.6.15.23-386

```
 
?

Hm.... i somehow managed to make a double post... can a mod please delete the previous post, since i can't find a delete button?

---

### Post by nicjasno on 2006-06-11
Ok, i made sure that i have linux-restricte sources enabled. So i did

```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -a)

```

It told me the latest version is already installed. So i tried again:

```

sudo apt-get install nvidia-glx

```

works fine.

But when doing 

```

sudo apt-get install nvidia-settings

```

i still get the following error:

```

dpkg- can't mmap package info file '/var/lib/dpkg/available no such device
E: sub-process /usr/bin/dpkg returned an error (2)

```

I then downloaded the nvidia drivers manually and tried to manually install. But when the install was finished and i rebooted it still said that the "nvidia"module is nowhere to be found.... grrrrrrr!!!!!!!

I even tried [This](http://www.albertomilone.eu/europeo/nvidia_scripts1.html). The script ran fine, but when doing a startx, again, no glx and no nvidia module and no X :(

---

### Post by nicjasno on 2006-06-11
It looks like i don't have neither available nor available.old files in /var/lib/dpkg/ . How can that be? No wonder this doesn't work. Would it help if i use someone eslses available and available.old files? If so, can someone mail me his files please?

---

### Post by tseliot on 2006-06-11
Don't try to install nvidia-settings with the latest driver.

```
sudo nano -w /etc/X11/xorg.conf
```

Try adding the following line to the Section Device of your xorg.conf:

```
Option "NvAgp" "0"
```

Then save the file and exit (CTRL+X)

then reboot:
```
sudo reboot
```

---

### Post by fmo on 2006-06-12
[QUOTE=nicjasno]
I then downloaded the nvidia drivers manually and tried to manually install. But when the install was finished and i rebooted it still said that the "nvidia"module is nowhere to be found.... grrrrrrr!!!!!!!
[/QUOTE]

I know this problem, there is a process that actually remove the module at each boot once you have installed the drivers from repository.

To make it go away, you need to do a COMPLETE REMOVAL of the drivers packages from the repository and then reinstall the driver downloaded.

After that you should be ok.

---

### Post by nicjasno on 2006-06-12
I formated the / partition, reinstalled and let automatix do the rest. Works perfectly now. Thanks for the help.

---

### Post by HankB on 2006-06-12
[QUOTE=nicjasno]Ok, i made sure that i have linux-restricte sources enabled. So i did

```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -a)

```
[/QUOTE]

That should be 
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -**[COLOR="Red"]r[/COLOR]**)

```

I think.

---

### Post by tseliot on 2006-06-13
[QUOTE=HankB]That should be 
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -**[COLOR="Red"]r[/COLOR]**)

```

I think.[/QUOTE]
Yes, you're right

---

