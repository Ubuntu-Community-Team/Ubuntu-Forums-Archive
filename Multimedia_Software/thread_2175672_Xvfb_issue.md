---
title: "Xvfb issue"
date: 2013-09-20
forum: Multimedia Software
---

### Post by treaves on 2013-09-20
I have an 13.04 server that I ssh into to run software I've written.  This machine has the NVIDIA-CUDA package, as two CUDA's are installed, and my software uses them.  There are no GUI logins on this machine (no monitor attached).  I am running Xvfb on display :3.

I've written a piece of software that uses librsvg for processing SVG images.  It core dumps, with this:
Xlib:  extension "RANDR" missing on display ":3.0".

I've spent about eight hours researching this.  All I've really learned is that it's a common issue, and there ate no clear answers as to how to resolve it. The people that have claimed to overcome the issue tend to blame the XINERAMA extension, and disabled it in the xorg.conf file.  But Xvfb does not use this file.  The second group (they seem to only offer advice, as no one has stated they have this working) say to start Xvfb without the XINERAMA extension.  This seems reasonable.

I see that Xvfb hase two options that may be helpful : '-xinerama' to not use XINERAMA, and '-extension XXX' to not use that extension.  The problem is, Xvfb completely ignores both of these options.  I've tried every premutation I can think of, and I always get this when starting Xvfb "Initializing built-in extension XINERAMA".  

Has anyone actually resolved this issue with Xvfb?  Does anyone know why Xvfb ignores the command line options?  Does anyone know where is the correct bug tracker to log a defect for Xvfb?

Any help would be greatly appreciated.

---

