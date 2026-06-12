---
title: "Ubuntu Studio low res!"
date: 2008-11-23
forum: Multimedia Software
---

### Post by Joe of loath on 2008-11-23
hello!

I have a ubuntu studio box on a 26inch LCD TV. (connected via VGA). when I installed the max resolution was 800x600. I installed the Nvidia driver via envy and now my max resolution is 640x480! fix-X doesn't work, I can't edit Xorg.conf (see below) and I can't reconfigure Xorg through the terminal (it bombs out with an error after the keyboard settings!).

can anyone help me? I'm out of ideas!:confused::mad:

---

### Post by Joe of loath on 2008-11-23
here's my Xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

---

### Post by lukjad on 2008-11-23
Could you give us information on your Video card please?

---

### Post by Joe of loath on 2008-11-23
yes, its a Geforce MX440.

---

### Post by ipburbank on 2008-11-23
go to System -> Administration -> nvidia x server settings and look at the x server display configuration tab. From there you can change the resolution from what ever it is to auto, or if it is already on auto change it to what you want it to be.

~let us know how it goes, and if it is fixed remember to go to thread tools and mark thread as solved :popcorn: ~istvan Creator of All Free VFX

---

### Post by lukjad on 2008-11-23
> I have a ubuntu studio box on a 26inch LCD TV.

Is this Ubuntu Studio 8.04?

---

### Post by Joe of loath on 2008-11-23
in the Nvidia control panel the max res is 640x480. I also can't click 'apply' because it's off the bottom of the screen.

> **lukjad007 said:**
> Is this Ubuntu Studio 8.04?

yes. I installed onto Xubuntu (couldn't find the ubuntu cd), but it just downloaded gnome. 8.1 had the same problems.

---

### Post by ipburbank on 2008-11-23
What you want to click is save to x-configureation file

---

### Post by Joe of loath on 2008-11-23
> **ipburbank said:**
> What you want to click is save to x-configureation file

thats the button! I can't see it, it's off the bottom of the screen lol.

---

### Post by ipburbank on 2008-11-23
if you can see the menu bar, right click and select move, then see if you can bring it on screen.

---

### Post by Joe of loath on 2008-11-23
> **ipburbank said:**
> if you can see the menu bar, right click and select move, then see if you can bring it on screen.

can't do that, I tried already.

the highest resolution on the nvidia list is 640x480. I need at least 1024x768 (possibly 1366x768 too, as I'd like the native resolution of the screen.)

anyone know how to fix it?

---

### Post by ipburbank on 2008-11-23
If you can't do it the gui way you can do it in the text editor. use google to edit your xorg, and in that there will be a section about your monitor, just type in your preferred resolutions there.

---

### Post by Joe of loath on 2008-11-25
> **ipburbank said:**
> If you can't do it the gui way you can do it in the text editor. use google to edit your xorg, and in that there will be a section about your monitor, just type in your preferred resolutions there.

tried that already, it messed up big time.

---

### Post by ipburbank on 2008-11-25
what happended? can you post some screenshots and your xorg please?

---

### Post by Joe of loath on 2009-01-03
ok, back again. I managed to find the xorg.conf of someone using the same card and a similar TV to mine, and merged the relevant sections. I'm now getting the error: no screens found.

seems a little silly. I think its something to do with the signal the TV sends back to the card not being detected. here's my Xorg.conf:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
       Identifier      "Generic Video Card"
       Driver          "nvidia"
       Option "UseEdidDpi" "FALSE"
       Option "ModeValidation" "NoWidthAlignmentCheck"
EndSection

Section "Monitor"
       Identifier      "Generic Monitor"
       DisplaySize     345 195
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "Generic Video Card"
       Monitor         "Generic Monitor"
       DefaultDepth     24

   SubSection "Display"
       Depth           8
       Modes           "1366x768" "1024x768" "800x600" "640x480"
   EndSubsection
   
   SubSection "Display"
       Depth           16
       Modes           "1366x768" "1024x768" "800x600" "640x480"
   EndSubSection

   SubSection "Display"
       Depth           24
       Modes           "1366x768" "1024x768" "800x600" "640x480"
   EndSubSection
EndSection
```

it doesn't even like the basic nvidia xorg.conf (same error). it only seems to work if I reconfigure X (but then only with 800x600), but it only gets through the keyboard stage before bombing out (something about a customized configuration, even though its the basic file :evil:)

can anyone help?
Thanks
Joe

---

### Post by Joe of loath on 2009-01-06
anyone?

---

### Post by Joe of loath on 2009-01-16
Can someone please help? I just reinstalled as my SSH server was hacked, and want to TRY getting the resolution working.

---

### Post by Joe of loath on 2009-02-03
](*,)

---

