---
title: "Any TwinView wizards out there?  Some questions..."
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by mageus on 2006-12-17
First of all, to anyone trying to figure out TwinView, I strongly recommend NVidia's own reference here:
[http://download.nvidia.com/solaris/1.0-8762/README/appendix-g.html](http://download.nvidia.com/solaris/1.0-8762/README/appendix-g.html).


Trying to set up TwinView, my specs are at the bottom.  Sorry for the long post.

I've got a working setup with a Dell 20" widescreen connected via DVI & a 50" plasma monitor connected via a VGA-DVI adapter plug.

I use 1680x1050 in portrait view for daily use (with the plasma off), but would like to switch to 1366x768 cloned view to watch movies and the such.

The stock configuration (1680x1050 LCD only) works fine.  For TwinView, I can get both displays to show 1280x768.


- How can I force 1366x768?  It works in WXP on this machine, even cloned.  I've tried adjusting the metamode option and the Display->Modes option without help.


- Do I need to specify TwinViewOrientation if I've given offsets in the metamodes option?

If I understand correctly (after hours and hours of digging around), TwinView basically presents the window manager with a 'screen' that has a resolution of the bounding box of all displays.  It has no idea about the displays connected.  TwinView then makes each display show a portion of that 'screen' based on the resolutions and offsets specified in the 'metamodes' option.  Thus the need for panning parameters if a display resolution is smaller than the screen.
Is this correct?


- Are metamodes absolute restrictions on screen size?

I can go into the NV settings app and resize everything larger than the original metamode that gnome booted into.  So does that mean that the purpose of the metamode is just to specify the initial resolutions of everything on startup of the window manager?
If this is the case, why do we even need metamodes in the first place?  Why can't the NVidia driver just remember the last configuration and apply it at the time of Xwindows startup?


- Is there a way to clean up communication between TwinView and the window manager?

I understand that changing resolutions to a larger size will screw up your desktop because the window manager doesn't recognize the full change, so your menu bars will 'float' on the desktop (at the same x,y position they were in the first resolution).


- Can I setup 2 configurations and boot Xwindows into each one when I want to?

The way the xorg.conf options are set up, it will always try to boot into the first metamode and I have to manually change resolutions to the other mode when needed.  Using the NULL parameter in the metamodes doesn't help since I think X detects the plasma even when it's off (in standby).  Well, actually, I'm not quite sure about that because it seems to exhibit variable behaviour.
In any case, is there a way to set up a flag to boot into one mode or the other?  The kludge is to swap out two different xorg.conf files each time you want to change modes, but that is inelegant.


- It seems like the 'UseDisplayDevice' and 'ConnectedMonitor' options aren't really needed.

Most of the postings here have talked about these settings.  The NVidia reference page itself says these are optional and usually not needed.  I'm guessing these are only needed if you've got an older TV that doesn't support EDID.


- Do I need to use 'UseEDIDFreqs'?

It seems that X detects the frequencies even without this option.


- Do I need the Composite -> Disable option?  Some config put it there, and I have no idea why.



Attached is my xorg.conf

TIA



BioStar TForce 6100 (NForce 410)
eVGA GeForce 7600GT
1GB RAM

Dell 2005FPW
Vizio P50HDM

Ubuntu 6.10 386, kernel 2.6.17-10-generic
Nvidia 1.0-9631

---

### Post by mageus on 2007-01-02
Many lookers, no takers.

Anyone?

---

