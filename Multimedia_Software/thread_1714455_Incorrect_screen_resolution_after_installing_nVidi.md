---
title: "Incorrect screen resolution after installing nVidia drivers."
date: 2011-03-25
forum: Multimedia Software
---

### Post by Mad Dawg on 2011-03-25
I know there are a lot of threads out there for same or similar issues, but nothing I found was working for me until, by sheer chance, I found this very simple solution on the Fedora forums. Too elegant not to share.

Environment:

Ubuntu 10.10
nVidia GeForce 5500
Samsung SyncMaster 225BW
Using DVI cable (in case it matters)

Issue:

After installing the proprietary nVidia drivers, the screen resolution was no longer the correct native resolution of the display. In my case specifically, the nVidia X Server Settings utility was detecting the maximum supported screen resolution was 1280x1024 while my display's native resolution is 1680x1050.

Solution:

Open a Terminal window.

Make a backup copy of the original xorg.conf file. This is just good form any time you are making config file customizations.

```
sudo cp -p /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Open 'xorg.conf' in a text editor.

```
gksudo gedit /etc/X11/xorg.conf
```

Add the following line to the "Device" section.

```
Option "ModeValidation" "NoMaxPClkCheck"
```

Here is my current, working 'xorg.conf' file for reference.

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"ModeValidation" "NoMaxPClkCheck"
EndSection
```

Save modified 'xorg.conf' and either restart X or reboot.

When everything comes back up you should be at your monitor's native resolution. Open the nVidia X Server Settings utility and you should see a bunch of previously missing resolution settings, including the correct native resolution for your display.

---

### Post by realzippy on 2011-03-25
*Using DVI cable (in case it matters)*

matters,'cause this is the problem

[COLOR="Red"]Option "ModeValidation" "NoMaxPClkCheck[/COLOR]"

should be the last shot;
note that you are running a nvidia FX 5xxx video device which were known to have a buggy TMDS encoder chip having problems with DVI...

---

