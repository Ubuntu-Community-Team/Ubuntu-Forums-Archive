---
title: "Problem with the visuals effects and GLX"
date: 2009-08-07
forum: Multimedia Software
---

### Post by agranger36 on 2009-08-07
Hi everybody,

From two weeks now, I've got a huge problem :
Before troubles appeared, compiz was working perfectly, 3D cube, special windows, all the common 3D graphical effects that compiz usually provides was working.

When suddenly, one day, I went to System > Preferences > appearance > visual effects, I saw that none of them was activated. I didn't understand why, because 3D effects given by compiz were OK, then I enabled "extra" option !

And then, as a matter of fact, I was said : "Visual effects couldn't be activated"

So, there is my xorg.conf :


Section "Device"
        Identifier        "Intel GMA X4500"
        Driver          "intel"
        VendorName      "Intel"        
EndSection

Section "Monitor"
        Identifier        "Configured Monitor"
EndSection

Section "Screen"
        Identifier        "Default Screen"
        Monitor                "Configured Monitor"
        Device                "Configured Video Device"
        Option         "AddARGBGLXVisuals" "True"
        Option         "AllowGLXWithComposite" "True"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection



The outcome of glxinfo :


name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault



The outcome of lspci | grep VGA :



VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)



I would be pleased if someone could help me !


Info :
I am a new member's site and i am a french man. I am bad in english and i don't saw place the code balises. Think you

---

### Post by agranger36 on 2009-08-08
Nobody ?:(

---

### Post by overdrank on 2009-08-08
> **agranger36 said:**
> Nobody ?:(

Hi and welcome, if you are using Jaunty 9.04 you may look at the link in my signature about Jaunty and intel graphics.

---

### Post by agranger36 on 2009-08-09
Hi:)

Thank you for your message :KS. I test the technic and the UXA acceleration is actived but not GLX. And I don't play to my 3D games. Please help me.

Sorry for my bad english.:lolflag:

---

### Post by Johanano on 2009-08-09
Have you tried opening a terminal and running "compiz --replace". If that seems to work then it's an issue in the Appearance-settings.

---

### Post by agranger36 on 2009-08-09
See the outcome of compiz --replace :

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: xterm 
no xterm found, exiting

The problem is really GLX:(
Again : help me

---

### Post by agranger36 on 2009-08-11
Always nothing:(

Edit :

I'm used the compiz-check script and see the outcome :

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


It's crazy !

---

### Post by agranger36 on 2009-08-12
Any suggestions ?

---

### Post by agranger36 on 2009-08-12
Help me, please :(

---

### Post by agranger36 on 2009-08-14
Nobody for help me ?

---

### Post by agranger36 on 2009-08-16
Is the 6st up :(

---

### Post by agranger36 on 2009-08-21
Update : GLX run !!

But the visuals effets don't run.
The outcome of compiz --replace :

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by tantric rex on 2009-09-24
how did you get GLX to run?

i recently replaced my motherboard with one that has an intel x4500 onboard (g41) and have the exact same problem as you report in your previous posts: no glx, compiz-check shows no rendering, glxinfo, and many others tell me i have no opengl support.  i am using intel driver 2.4 (couldnt play any video with 2.6) and synaptic reports intel driver and mesa are installed.  ive tried reinstalling everything but still no compiz, cairo-dock, or xbmc opengl...they all report i dont have the support.

when i edited my xorg.conf to match yours my system boots into low graphics mode saying: fatal error - no screens are found.

argh!  im trying to avoid a full ubuntu reinstall...could you please let me know what steps you took to get glx working?

---

### Post by tantric rex on 2009-09-25
update: 

looks like switching from an nvidia agp card to a new mobo with intel (g41) x4500 somehow corrupted my graphics driver + opengl relationship.  so after 1 week and many hours of dead ends, finally gave up and reinstalled ubuntu 9.04 and, as expected, works mostly fine (aside from some cairo-dock (glx-dock) and cairo-dock + compiz issues).

---

