---
title: "ATI HD 3870 no GLX (8.10)"
date: 2009-01-14
forum: Multimedia Software
---

### Post by hiethan592 on 2009-01-14
So after upgrading to 8.10 to fix a separate hardware incompatibility, I no longer have the ability to run anything 3d.  I am running 8.10 2.6.27-9-generic on an AMD 64bit.  It worked perfectly before upgrading.  Clicking activate in the restricted drivers manager does nothing.  Just a download box and then nothing, doesn't even ask me to restart.

glxinfo:
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

xorg.conf:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "Extensions"
        Option      "Composite" "disable"
EndSection
```

Any help would be greatly appreciated.  I need 3d to work on my semester project.

---

### Post by hiethan592 on 2009-01-14
Just tried the proprietary drivers (8.12) on the ATI website with no luck either.  Anyone?  Is there something I am missing?  Is there a way to make sure I am getting everything uninstalled that I need to?

---

### Post by Lawkout on 2009-01-14
> **hiethan592 said:**
> Just tried the proprietary drivers (8.12) on the ATI website with no luck either.  Anyone?  Is there something I am missing?  Is there a way to make sure I am getting everything uninstalled that I need to?

This link worked for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by hiethan592 on 2009-01-15
I followed that guide but after rebooting all I have is a black screen with a few random colored pixels at the top of the screen.  And switching to a tty causes my monitor to say 'no input' and I cannot get back to the black screen with random pixels.

Any other ideas?

---

