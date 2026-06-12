---
title: "Intrepid Video Fixes (nVidia 96 series focus)"
date: 2008-12-11
forum: Multimedia Software
---

### Post by dawynn on 2008-12-11
With the switch from Hardy to Intrepid, there were major changes in xorg.  These changes initially were not supported in the legacy drivers, even at release time.  But nVidia has released a 96 seroes driver that will work with the new xorg functionality.  The 96 series of nVidia drivers matured into usability with 96.43.09.  These are now available in the intrepid-updates area.

Please keep any responses to this thread limited to actual fixes.  Please identify the general problem you are fixing, and the actual fix implemented.
 
**Finding the right drivers:**

In Synaptic, go to the Settings menu and pull up "Repositories".  This will bring up an extra window.  Choose the "updates" tab.  Make sure that "Recomended updates" is check-marked, and choose close.  Hit the "Reload" button to refresh your computer's list of available packages.  "Search" (not "Quick Search") for "jockey".  Make sure that jockey-common and either jockey-gtk or jockey-kde are installed to the latest version.

Exit out of Synaptic and bring up your "Hardware Drivers".  This will search your system and recommend all of the nVidia drivers that will work with your video card.  This may not mean that these will work with your system.  For example, I have an Athlon Classic with an nVidia GeForce FX 5700 LE card.  My card can use more recent drivers, but my computer can't handle the SSE instructions used by the driver.  So, I'm stuck with the 96 series also.

Choose the most appropriate driver for your system and follow the prompts.  

If you have been a linux and *buntu user for some time, and have had to make changes into xorg.conf for your computer and your video card in the past, I would encourage you to read

```
man nvidia-xconfig
```

This is the standard tool for making xorg.conf changes related to your nVidia video card.  For any simple changes you may have found necessary for your card in the past, you should find some setting used by this tool to adjust your nVidia card to your needs.

I would suggest restarting your system once the driver has been set up to your liking.  At this point, basic functionality should be working, although there may be other deeper issues yet.  Please scan the rest of this document for other fixes.

Many of the remaining fixes came from various posts in bug 251107
([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107))
It is L-O-O-O-N-N-N-G.  You have been warned.

**Fix for wine fonts:**

From a terminal, type 

```
cd ~/.wine
gedit settings.txt
```

This will bring up a text edit session.  Copy and paste these lines into the editor.

```
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"
```

Save and exit out of gedit.  This should bring you back to your terminal session, still in the ~/.wine directory.  So, in the terminal session, type

```
regedit settings.txt
```

If you have a laptop and are experiencing a Blank Screen when you install the Nvidia drivers. Try the following:

Add the following lines to the "Device" section:

```
Option "UseDisplayDevice" "DFP"
Option "AddARGBGLXVisuals" "true"
```

it should look something like this:

```
Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "UseDisplayDevice" "DFP"
Option "AddARGBGLXVisuals" "true"
EndSection
```

First additional line forces the Drivers to display on the laptop screen instead of a CRT.
Second line fixes the "white screen" issue people are seeing with these drivers.

Then reboot. it should work now.

**Compiz compatability**

Many have also noted the "AddARGBGLXVisuals" fix helps compiz work.  This can be enabled by...

```
sudo nvidia-xconfig --add-argb-glx-visuals
```

**More laptop font fixes:**

Especially for laptops, some have noted that going to 
System -> Preference -> Appearance -> Fonts -> Details
and choosing "Subpixel (LCDs)" has helped with issues in Open Office and Compiz.

**OpenOffice menu issues**

One user said he talked to the folks at Compiz-Fusion, who suggested adding:

Option "RenderAccel" "0" to the Device section of xorg.conf

will solve this problem.  A number of users indicated that did the trick for them.

Another user reported fixing his OOo menu issue by going to
System->Appearance->Visual Effects 
and changing the setting to "None".

Others have noted that enabling composite in xorg.conf has worked.  You can do this via command line by typing:

```
sudo nvidia-xconfig --composite
```

---

### Post by dawynn on 2008-12-16
Not sure if my experience echoes the experience of others...

In the end, the final solution to fix the rest of my nvidia problems was a matter of going through my /etc/X11/xorg.conf file and simplifying it.  After using the automated tools, I had two screen configurations, two devices, and two monitor settings.  But I only have one card and one monitor.

I made sure to keep the name of each item as its referenced throughout xorg.conf, but otherwise, I took out the extra settings and just simplified my configuration file down to just a single one of each item.

A reboot after slimming my file and everything worked.  Glxgears finally shows spinning gears for me.  I'm back in business.

---

