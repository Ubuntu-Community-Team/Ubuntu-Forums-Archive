---
title: "Cant get 1024 x 768 to work"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by Mr.NiceGuy on 2007-06-30
I cant get 1024 x 768 to work in Ubuntu. I installed ubuntu recently and when i got to System>Prefrences>Screen Resolution    i cant pick 1024 x 768 all i can pick is 800 x 600 and i dont know what to do. Please Help me.

my /etc/X11/xorg.conf looks like this

```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:2:4:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"VG150b"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"VG150b"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by david_2001 on 2007-06-30
If you have a ViewSonic VG150b LCD display then try adding the correct (according to the [COLOR="DarkOrange"][datasheet[/COLOR]]("http://www.viewsonic.com/pdf/us_eng/products/vg150.pdf")) horizontal and vertical frequencies for your monitor to xorg.conf:
```
Section "Monitor"
	Identifier	"VG150b"
	Option		"DPMS"
[B]	HorizSync	30-62
	VertRefresh	50-75[/B]
EndSection
```

---

### Post by Mr.NiceGuy on 2007-07-01
i put that in and saved it and still i am 800 x 600 :( I really have no clue why this is not working but i really want my better resolution back.:p

---

### Post by bioShark on 2007-07-01
Hi

I have exactly the same problem, 800x600 only.

I have also added the modeling line in xorg.conf:
Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync

...but it still doesn't work!

Please help us on this, cause I'm starting to have problems with my eyes!

---

### Post by david_2001 on 2007-07-01
> **Mr.NiceGuy said:**
> i put that in and saved it and still i am 800 x 600 :( I really have no clue why this is not working but i really want my better resolution back.:p
Did you restart the X server after saving the changes?  Logging out/in won't work, so either use Ctrl-Alt-Backspace to kill the current X session or reboot (my preference).

---

### Post by bioShark on 2007-07-01
I myself have restarted the X server with ctrl + alt + backspace a dozen of times. I have also rebooted a few times...but still, nothing

---

### Post by Mr.NiceGuy on 2007-07-01
same here, is there another thought on how to fix this problem

---

### Post by david_2001 on 2007-07-01
> **Mr.NiceGuy said:**
> same here
This is baffling.  Let's try a few more changes:
```

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
# Added the following additional module
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:2:4:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"VG150b"
	Option		"DPMS"
	HorizSync	30-62
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"VG150b"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
# Deleted 1280x1024 because it definitely isn't supported by this monitor.  Also deleted the "unusual"
# resolutions.
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Mr.NiceGuy on 2007-07-02
i copied and pasted exactly what was there and still i get 800 x 600. im srry for all the trouble but its just not working :(

---

### Post by bioShark on 2007-07-02
Mine isn't working aswell, I am guessing there might be something wrong with the driver Nvidia has installed!

---

### Post by sputnick on 2007-07-02
when i first installed ubuntu, it didn't have my resolution, which is a little unique, so i googled around and found an easy fix, there is a text file you have to edit and add your resolution, it was very very very easy, and very quick, and it worked like a charm. sorry i can't remember where i found the info nor the filename of the text file...  but if you keep lookin, you'll find it. good luck.

---

### Post by sputnick on 2007-07-02
a little grepping revealed that the file i had to edit is 

/etc/X11/xorg.conf

hmmm.. come to think of it your resolutions are already in there. guess that is not your problem.

---

### Post by david_2001 on 2007-07-02
> **Mr.NiceGuy said:**
> i copied and pasted exactly what was there and still i get 800 x 600. im srry for all the trouble but its just not working :(
Do you have nvidia-settings installed?  If so, run it from a console, select "X Server Display Configuration" and see whether it offers 1024x768 as a possible resolution.  If it does then select and click on "Save to X Configuration File".  Otherwise, please reboot and then post your entire /var/log/Xorg.0.log file.

---

### Post by bioShark on 2007-07-02
Hi

having a Geforc4 MX 440 video card, and having installed the Nvidia drivers, I am guessing, I have to change it with the nvidia legacy drivers. That's what i have found out googleing a little. I will do this tonight, cause right now I am at work!
c.u

---

### Post by david_2001 on 2007-07-02
> **rollandsov said:**
> Mine isn't working aswell, I am guessing there might be something wrong with the driver Nvidia has installed!
Inaccurate monitor detection in certain instances is a known problem.  Unforuntately, the fix is to do what we've done already.  The next step will be to try turning off some of the automatic monitor detection and make another little fix that I just noticed:

```
Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:2:4:0"
# Commented the following line out as it is not used by the nvidia driver
#	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
**	Option		"UseEDIDFreqs"	"False"**
**	Option		"ModeValidation"	"NoEdidModes"**
EndSection
```

---

### Post by david_2001 on 2007-07-02
> **rollandsov said:**
> Hi

having a Geforc4 MX 440 video card, and having installed the Nvidia drivers, I am guessing, I have to change it with the nvidia legacy drivers. That's what i have found out googleing a little. I will do this tonight, cause right now I am at work!
c.u
According to information on the nvidia website, even the very latest 100.14.11 driver supports the MX440.

---

### Post by bioShark on 2007-07-02
Hi 

I will try what you have sugested about the monitor detection first before going to legacy:

so...I should comment out this line:

#	Option		"AddARGBVisuals"	"True"

and I should add this 2 lines:
	Option		"UseEDIDFreqs"	"False"
	Option		"ModeValidation"	"NoEdidModes"

P.S. I have noticed that the nvidia driver doesn't recognize my monitor, cause in the status of the driver is : @@@ at 800x600; Display device @@@.

Strange.... I have a Dell P780.

---

### Post by alv22 on 2007-07-02
Hi. I have a laptop and had the exact same problem until I changed the default color depth to 16.

That is:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"VG150b"
	Defaultdepth	24
```

to

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"VG150b"
	Defaultdepth	16
```


Now, this is a suboptimal workaround, but at least it's nicer to fix it in the correct res.

Tell me if it works!

---

### Post by david_2001 on 2007-07-02
> **rollandsov said:**
> Hi 

I will try what you have sugested about the monitor detection first before going to legacy:

so...I should comment out this line:

#	Option		"AddARGBVisuals"	"True"

and I should add this 2 lines:
	Option		"UseEDIDFreqs"	"False"
	Option		"ModeValidation"	"NoEdidModes"

P.S. I have noticed that the nvidia driver doesn't recognize my monitor, cause in the status of the driver is : @@@ at 800x600; Display device @@@.

Strange.... I have a Dell P780.
First, I made an oops.  The 1.0.96xx driver supports the MX440, not the very latest version.  If you are using the Ubuntu nvidia driver then you shouldn't have any problem (I only recently replaced my MX440 card and it worked just fine with the Ubuntu nvidia drivers - not legacy).  Answers to your questions above are:
[LIST=1]
[*]Yes.
[*]Yes.  The alternative is to go the whole hog and use Option "UseEDID" "False"
[/LIST]
There's more information on the nvidia options for xorg.conf in the [COLOR="SandyBrown"][readme]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9639/README/README.txt")[/COLOR].  Do you have the correct horizontal and vertical frequencies for your monitor?  Information I can find is:
```
HorizSync	30-85
VertRefresh	48-120
```

---

### Post by bioShark on 2007-07-02
Hi

At some point in my many changes of the xorg.conf I had set the horiz and vertical frequencies in the monitor section, I have also tried a modeling line...generated by a tool on a website (don't remember which one)...and both changes didn't seem to make a difference. 
I will make the changes you have suggested in about 2 hours. Hope for the best!

---

### Post by david_2001 on 2007-07-02
> **rollandsov said:**
> Hi

At some point in my many changes of the xorg.conf I had set the horiz and vertical frequencies in the monitor section, I have also tried a modeling line...generated by a tool on a website (don't remember which one)...and both changes didn't seem to make a difference. 
I will make the changes you have suggested in about 2 hours. Hope for the best!
Good luck!

EDIT: Try using xvidtune to generate a modeline if you really need one - you can see it working.

---

### Post by Mr.NiceGuy on 2007-07-02
> **david_2001 said:**
> Do you have nvidia-settings installed?  If so, run it from a console, select "X Server Display Configuration" and see whether it offers 1024x768 as a possible resolution.  If it does then select and click on "Save to X Configuration File".  Otherwise, please reboot and then post your entire /var/log/Xorg.0.log file.

the thing is since it is 800 x 600 it wont let me see the part that you are asking so i will post my entire /var/log/Xorg.0.:(

---

### Post by bioShark on 2007-07-02
It seems that it doesn't work with the replacements you have suggested, so I try now to install the legacy drivers!

---

### Post by Mr.NiceGuy on 2007-07-02
**FIXED** this is what this section looked like...
```
Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:2:4:0"
        Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"UseEDIDFreqs"	"False"
	Option		"ModeValidation"	"NoEdidModes"
EndSection
```

make it look like this and all your worries will be gone.

```
Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:2:4:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"UseEDID"	"False"
	Option		"ModeValidation"	"NoEdidModes"
EndSection
```

after doing this it still didnt work for me, then i deleted my whole home folder even the hidden ones that appear when you push ctrl + h
do this and it shall work. Worked for me;)

---

### Post by david_2001 on 2007-07-02
> **Mr.NiceGuy said:**
> after doing this it still didnt work for me, then i deleted my whole home folder even the hidden ones that appear when you push ctrl + h
do this and it shall work. Worked for me;)
Glad to hear that something worked, though deleting the entire contents of your home folder is a little radical - I'd want to know which exact file needed to be removed ;-).

---

### Post by bioShark on 2007-07-02
Hi

IT'S WORKING!!!!!!!!!!!!!

Solution:

Manual download to the Nvidia 9639 driver, directly from [www.nvidia.com](www.nvidia.com) . It is the latest one (may 2007). After installing the build-essential :

    $sudo apt-get install build-essential

 from the repository,

   $sudo sh NVIDIA-Linux-x86-1.0-9639-pkg1.run

Then it makes an install of about 2 minutes, and the next time you start the X you have all the resolutions available. 

c.u.

---

### Post by david_2001 on 2007-07-02
> **rollandsov said:**
> Hi

IT'S WORKING!!!!!!!!!!!!!

Solution:

Manual download to the Nvidia 9639 driver, directly from [www.nvidia.com](www.nvidia.com) . It is the latest one (may 2007). After installing the build-essential :

    $sudo apt-get install build-essential

 from the repository,

   $sudo sh NVIDIA-Linux-x86-1.0-9639-pkg1.run

Then it makes an install of about 2 minutes, and the next time you start the X you have all the resolutions available. 

c.u.
Well done - it's persistence that counts ;-).  Don't forget that you'll need to repeat the driver install every time the Ubuntu kernel package gets updated.

---

### Post by bioShark on 2007-07-02
Hi

Good to know :P

Thanks for all your help!

---

