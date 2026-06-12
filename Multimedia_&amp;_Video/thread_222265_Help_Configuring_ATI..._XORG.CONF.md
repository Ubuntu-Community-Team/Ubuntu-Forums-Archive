---
title: "Help Configuring ATI... XORG.CONF"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by Efrain Valles on 2006-07-24
this might sound Cliche but... I need Help Configuring my ATI CARD

I own a Ati Radeon Mobility M6 LY... and I was trying to solve some random crash problem when I decided to give [this]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Confirm_that_it_works") a try...

but my X fails to load... 

this is the XORG.CONF I use so that my X doesn-t crash...

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
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
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
		Modes		"1024x768" "800x600" "640x480"
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

Once I go through with the Steps in the Wiki (Includes CHanging the driver to fglrx) ... and Reboot my X fails to load...

please Help...

=eff=

---

### Post by Ziox on 2006-07-24
what is your goal? Enable 3D Acceleration?

---

### Post by Efrain Valles on 2006-07-25
> **Ziox said:**
> what is your goal? Enable 3D Acceleration?

I think just using the ATI driver would be fine... I haven't met a single person that has made this card do som 3d accel...

I am using the VESA driver right now and it's really struggling to get the card to work... so ...

---

### Post by 2hansen on 2006-07-31
I've got the same card as you, and to my knowledge these cards are not supported by the fglrx-driver.

---

### Post by Ziox on 2006-07-31
@ 2hansen

he's not trying to enable direct rendering / 3D acceleration, which means he doesn't need the fglrx driver...

@ efrain

have you tried the ATI driver? meaning to change "vesa" to "ati" or "radeon"?

what is the result of it?

---

### Post by 2hansen on 2006-07-31
The original post said: 

> I own a Ati Radeon Mobility M6 LY... and I was trying to solve some random crash problem when I decided to give this (a link to fglrx guide) a try...

but my X fails to load.

And by following the guide you end up with the fglrx-driver, which does not support the card --> and X fails to load...

---

### Post by Efrain Valles on 2006-07-31
> **Ziox said:**
> @ 2hansen

he's not trying to enable direct rendering / 3D acceleration, which means he doesn't need the fglrx driver...

@ efrain

have you tried the ATI driver? meaning to change "vesa" to "ati" or "radeon"?

what is the result of it?

It Crashes ,,, very Often... 
I am using the vesa driver but it is a bit Jerky ... no animated fade outs when I lock my screen ... takes a while to popo some windows... it is really not helping

the Ati driver FREEZES the screen randomly... I have read ton of posts talking about memory leaks and wireless cards causing them, other people say it is the video cards... I have given up on this card rendering any #D.. I want it from crashing... 

are you using drapper and this card ... did you have this problem... ???

---

### Post by Ziox on 2006-07-31
> **Efrain Valles said:**
> It Crashes ,,, very Often... 
I am using the vesa driver but it is a bit Jerky ... no animated fade outs when I lock my screen ... takes a while to popo some windows... it is really not helping

the Ati driver FREEZES the screen randomly... I have read ton of posts talking about memory leaks and wireless cards causing them, other people say it is the video cards... I have given up on this card rendering any #D.. I want it from crashing... 

are you using drapper and this card ... did you have this problem... ???

If you are talking to me, yes I'm running dapper.  But I don't have the exact card, I have a really old ATI Technologies Inc Radeon IGP 330M/340M/350M.

EDIT: if you don't mind not having 3d rendering, then i believe you can comment out the lines: "Load "dri" and also the last section of Xorg.conf...the "DRI" section...then you can try the ATI driver...

hope this helps

---

### Post by 2hansen on 2006-08-01
I have an Ati Radeon Mobility M6 LY in my Sony Laptop, which uses the "radeon" or "ati" driver without problems - unless I use the dual head possibility - if so it freezes randomly. I have reported it [here]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/47775").

And yes, I am on Dapper too...

---

### Post by Ziox on 2006-08-01
> **2hansen said:**
> I have an Ati Radeon Mobility M6 LY in my Sony Laptop, which uses the "radeon" or "ati" driver without problems - unless I use the dual head possibility - if so it freezes randomly. I have reported it [here]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/47775").

And yes, I am on Dapper too...

If you want to try dual head without the use of MergedFB, you can try my HowTo located in my signature. 

@Efrain sorry to hijack your thread (even if it is just one post)

---

### Post by Didjit on 2006-08-06
Did you get this worked out? I have the same card with the same lock up problems using driver "ati".

Didijt

---

### Post by Efrain Valles on 2006-08-06
nope ... I'm still on the vesa driver...

:-k what's this talk on Dual Heads? I am not a native Speaker... and my pc jargon is very limited (partly because I switched to linux a a year ago):-k 

like I said I don't want 3d Accel so ... the vesa is doing the job for the time being...

:(
GOTTA HATE ATI...

---

### Post by Ziox on 2006-08-06
> **Efrain Valles said:**
> nope ... I'm still on the vesa driver...

:-k what's this talk on Dual Heads? I am not a native Speaker... and my pc jargon is very limited (partly because I switched to linux a a year ago):-k 

like I said I don't want 3d Accel so ... the vesa is doing the job for the time being...

:(
GOTTA HATE ATI...

Dual heads is where there are two monitors connect to the same computer.  The functions of dual monitor is the ability to drag windows from one monitor to the other monitor, or the monitors can be "clones" of each other. 

"GOTTA HATE ATI" -well said, my man. :)

---

### Post by Didjit on 2006-08-06
> **Efrain Valles said:**
> nope ... I'm still on the vesa driver...

  what's this talk on Dual Heads? I am not a native Speaker... 

Seems like the ability to run two monitors, nothing that will solve our problem.....

Didjit

---

### Post by Ziox on 2006-08-06
for those that can't start X, check the file /var/log/Xorg.0.log file.  The log file includes errors that X has created every single it is initiated. You should most that file...

---

### Post by 2hansen on 2006-08-07
> If you want to try dual head without the use of MergedFB, you can try my HowTo located in my signature.

I am already using a similar configuration with Xinerama. However, my "freezing-problems" occurs no matter if I use Xinerama or just uses two independently X-Screens. But thanks anyway.

B:)

---

### Post by 2hansen on 2006-08-07
> **Efrain Valles said:**
> nope ... I'm still on the vesa driver...

Ok, but as mentioned previously - in my case the native Dapper driver ("ati" or "radeon") works just fine with my ATI Radeon Mobility M6 LY - except if I use it in a dual head setup. So the driver is working! So something else seems to be troubling you.

If you posted the xorg.conf that troubles you we could have a look at that? I believe that the one quoted above is the working one (with the vesa-driver)?

B:)

---

### Post by Efrain Valles on 2006-08-07
No problem.. listen my pc has been working great with ubuntu regardless the video card thing... it is still performing well...
so i put this to rest...  

A question..  a well supported video card for a desktop computer... I want a new desktop and I have to set it up, any help will be apreciated...

---

### Post by Ziox on 2006-08-07
> **Efrain Valles said:**
> No problem.. listen my pc has been working great with ubuntu regardless the video card thing... it is still performing well...
so i put this to rest...  

A question..  a well supported video card for a desktop computer... I want a new desktop and I have to set it up, any help will be apreciated...

get a nvidia card, not another ati card...that's all i have to say...

---

