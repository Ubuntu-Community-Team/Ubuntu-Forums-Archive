---
title: "X won't start after recent kernel and nvidia legacy driver updates"
date: 2005-11-22
forum: Multimedia &amp; Video
---

### Post by ummikko on 2005-11-22
Everything worked fine before the update. Now I get this error:

FATAL:Error inserting nvidia
(/lib/modules/2.6.12-10-386/volatile/nvidia.ko):no such device
(EE) NVIDIA(0):Failed to load the NVIDIA kernel module
(EE) NVIDIA(0):***Aborting***
(EE) Screen(s) found, but none have a usable configuration

Things work if I change "nvidia" to "nv" in xorg.conf. However it worked fine with "nvidia" before. I am clueless :confused: -help appreciated. I have a Geforce2 GTS/Pro card. Here is my xorg.conf file:



------------------------------------
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"S/M 755DF"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"S/M 755DF"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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

---

### Post by jadugarr on 2005-11-22
I just experienced the exact same problem after kernel upgrade to 2.6.12-10-k7.  Moved back to last kernel until I know how to fix it.

---

### Post by tadwenger on 2005-11-22
Same problem here. Sure was glad to see the old kernel in grub. Message says x is not configured properly and boots into terminal.

---

### Post by sbassett on 2005-11-22
Ditto, 
  Any uber-ubuntu hackers that need info, please feel free to ask.

---

### Post by bonifacio on 2005-11-22
I have the same problem as the original poster.  My card is GeForce FX Go5200.  As a workaround I'm using the previous kernel 2.6.12-9-386.

---

### Post by pvoce on 2005-11-22
Normally, I have found that the easiest solution is to run the nvidia-installer again.

---

### Post by bonifacio on 2005-11-22
For some reason the update didn't pull the linux-restricted-modules-2.6.12-10-386-nvidia-legacy package.  So I did and my problem is solved.

---

### Post by Dagonus on 2005-11-23
Same problem as original author. Same solution worked.

---

### Post by zero0w on 2005-11-23
[QUOTE=bonifacio]For some reason the update didn't pull the linux-restricted-modules-2.6.12-10-386-nvidia-legacy package.  So I did and my problem is solved.[/QUOTE]

Exactly, I think the Ubuntu linux-restricted-modules builder seems to have ignored some people use **nvidia-glx-legacy** package (1.0-7174 driver) instead of the nvidia-glx package (1.0-7667 driver).

---

### Post by jadugarr on 2005-11-23
[QUOTE=zero0w]Exactly, I think the Ubuntu linux-restricted-modules builder seems to have ignored some people use **nvidia-glx-legacy** package (1.0-7174 driver) instead of the nvidia-glx package (1.0-7667 driver).[/QUOTE]

I experienced the problem using the 1.0-7667 drivers.

---

### Post by zero0w on 2005-11-23
[QUOTE=jadugarr]I experienced the problem using the 1.0-7667 drivers.[/QUOTE]

Then it should be a different problem from the one mentioned at the beginning of the thread, because he uses a GeForce 2 GTS display card which requires nvidia-glx-legacy package here.

---

### Post by jadugarr on 2005-11-23
[QUOTE=zero0w]Then it should be a different problem from the one mentioned at the beginning of the thread, because he uses a GeForce 2 GTS display card which requires nvidia-glx-legacy package here.[/QUOTE]

I got the same error after the kernel upgrade as he did, using a Geforce 3ti200.  Reinstalling the drivers will probably fix the error, but I haven't had time to mess with that yet.

---

### Post by daller on 2005-11-23
The "nvidia-glx-legacy" package is only for cards older than GeForce, isn't it?

---

### Post by jadugarr on 2005-11-23
[QUOTE=daller]The "nvidia-glx-legacy" package is only for cards older than GeForce, isn't it?[/QUOTE]

Actually I think it is all card older than a tnt2.  No wonder its called legacy ;).

---

### Post by daller on 2005-11-23
[QUOTE=jadugarr]Actually I think it is all card older than a tnt2.  No wonder its called legacy ;).[/QUOTE]

Yes, and why does people in this thread use it for a GeForce2 ???

---

### Post by zero0w on 2005-11-23
[QUOTE=jadugarr]I got the same error after the kernel upgrade as he did, using a Geforce 3ti200.  Reinstalling the drivers will probably fix the error, but I haven't had time to mess with that yet.[/QUOTE]

As I said, your problem was caused by something different.

---

### Post by jadugarr on 2005-11-23
[QUOTE=zero0w]As I said, your problem was caused by something different.[/QUOTE]
Oh I didn't read the full title to the post.  I just upgraded the kernel and got the same problem.  I think you have to manually reinstall the nvidia drivers after a kernel upgrade ... if you're using the nvidia drivers.

---

### Post by zero0w on 2005-11-23
[QUOTE=daller]Yes, and why does people in this thread use it for a GeForce2 ???[/QUOTE]

Search for "legacy GPUs" in this README and you'll find out:
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt)

```
Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.


    NVIDIA chip name                   Device PCI ID
    -------------------------------    -------------------------------
    RIVA TNT                           0x0020
    RIVA TNT2/TNT2 Pro                 0x0028
    RIVA TNT2 Ultra                    0x0029
    Vanta/Vanta LT                     0x002C
    RIVA TNT2 Model 64/Model 64 Pro    0x002D
    Aladdin TNT2                       0x00A0
    GeForce 256                        0x0100
    GeForce DDR                        0x0101
    Quadro                             0x0103
    GeForce2 GTS/GeForce2 Pro          0x0150
    GeForce2 Ti                        0x0151
    GeForce2 Ultra                     0x0152
    Quadro2 Pro                        0x0153
```

---

### Post by zero0w on 2005-11-23
[QUOTE=jadugarr]Oh I didn't read the full title to the post.  I just upgraded the kernel and got the same problem.  I think you have to manually reinstall the nvidia drivers after a kernel upgrade ... if your using the nvidia drivers.[/QUOTE]

His (and my) problem was caused by the Ubuntu Updater which informed of new updates earlier today.

---

### Post by jadugarr on 2005-11-23
[QUOTE=zero0w]Search for "legacy GPUs" in this README and you'll find out:
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt)
[/QUOTE]

Sorry, you are correct.  I have been awake for a while working on a programming project for class so I'm a little slow right now :).

---

### Post by daller on 2005-11-23
[QUOTE=zero0w]Search for "legacy GPUs" in this README and you'll find out:
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt)

```
Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.


    NVIDIA chip name                   Device PCI ID
    -------------------------------    -------------------------------
    RIVA TNT                           0x0020
    RIVA TNT2/TNT2 Pro                 0x0028
    RIVA TNT2 Ultra                    0x0029
    Vanta/Vanta LT                     0x002C
    RIVA TNT2 Model 64/Model 64 Pro    0x002D
    Aladdin TNT2                       0x00A0
    GeForce 256                        0x0100
    GeForce DDR                        0x0101
    Quadro                             0x0103
    GeForce2 GTS/GeForce2 Pro          0x0150
    GeForce2 Ti                        0x0151
    GeForce2 Ultra                     0x0152
    Quadro2 Pro                        0x0153
```[/QUOTE]

...Sorry, I was wrong! - Some dude told me that it was < (less than) GeForce

...What's the reason for this splitup? (nvidia-glx and nvidia-glx-legacy)

---

### Post by zero0w on 2005-11-23
No idea.

As a matter of fact the nVidia Windows driver was also split between legacy and modern display cards at version 71.xx. 

I guess it was good for nVidia to reduce the burden of maintenance over a wide array of GPUs.

---

### Post by ummikko on 2005-11-23
[QUOTE=bonifacio]For some reason the update didn't pull the linux-restricted-modules-2.6.12-10-386-nvidia-legacy package.  So I did and my problem is solved.[/QUOTE]

This works for me too. Thank you!

:D

---

### Post by jnie on 2005-11-23
[QUOTE=jadugarr]I think you have to manually reinstall the nvidia drivers after a kernel upgrade ... if you're using the nvidia drivers.[/QUOTE]

Correct! as stated in the Forum Group :  [Official Security Announcements ]("http://www.ubuntuforums.org/showthread.php?t=93511")

> ATTENTION: Due to an unavoidable ABI change this kernel has been given
a new version number, which requires you to recompile and reinstall
all third party kernel modules you might have installed. If you use
linux-restricted-modules, you have to update that package as well to
get modules which work with the new kernel version. Unless you
manually uninstalled the standard kernel metapackages (linux-386,
linux-powerpc, linux-amd64-generic), a standard system upgrade will
automatically perform this as well.

---

### Post by Teroedni on 2005-11-23
Are we talking about update from hoary to brezzy here?

---

### Post by jadugarr on 2005-11-23
[QUOTE=Teroedni]Are we talking about update from hoary to brezzy here?[/QUOTE]
No, a kernel upgrade in Breezy (I'm not sure if the hoary kernel was upgraded as well).

---

### Post by tseliot on 2005-11-23
EDIT: wrong post. Sorry, I'm getting too old...

---

### Post by Teroedni on 2005-11-23
Okay. I guess everyone have unninstalled nvidia glx and reinstalled again?
This is a common problem when the kernel is update or something else drastic is changed

I had to do alot of nvidia glx reinstall when i was using brezzy devel:P

So if there no more problem could the poster mark this thread as [solved]

Thank You:)

---

### Post by Pausanias on 2005-11-24
I am not using, nor have I ever had to use the legacy nvidia drivers. I am using the regular nvidia-glx package. And the latest security update broke my X server startup just as described above.

Using the nv driver is not an option as it doesn't work with my six-month old Quadro FX Go1400.... only the nvidia driver works.

Uninstalling and reinstalling nvidia-glx did nothing to fix the problem.

Booting back into the old kernel fixes the problem, but of course it's undesireable.

So, maybe it's "solved" for you legacy folks, but for the non-legacy people it's still a problem. Someone here was implying that it's a different problem, so I will start a new thread.

---

