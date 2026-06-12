---
title: "Help... compiz won't start"
date: 2009-03-30
forum: Multimedia Software
---

### Post by her15t on 2009-03-30
I've just install xserver-xorg-video-intel, but now my compiz won't start.
and here output from terminal

heri@herist:~$ compiz 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller]) 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work. 
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0 
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

what must I do to make my compiz work again, I've try to remove xserver-xorg-video-intel 
and reinstall xserver-xorg-video-i810 but got wrong screen resolution and still not work.

Thank

---

### Post by Sam Lars on 2009-03-31
Could you try the output of compiz-check too?

---

### Post by her15t on 2009-03-31
Here output of compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

it seem everything OK..:confused:

---

### Post by isparkes on 2009-04-01
Having exactly the same issue for a couple of days. The only things that have changed on the set up are that I have installed the usual updates and have started using an external monitor with a different resolution.

---

