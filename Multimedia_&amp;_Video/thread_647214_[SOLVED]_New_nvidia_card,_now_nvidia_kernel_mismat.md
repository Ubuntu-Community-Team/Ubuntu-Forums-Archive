---
title: "[SOLVED] New nvidia card, now nvidia kernel mismatch (help!)"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by candtalan on 2007-12-22
I have just changed my video card from a Radeon 7000 type to a NVIDIA gforce FX5200. Booting went ok and when the desktop appeared the Restricted drivers manager popped up - very impressive - and I accepted and the driver downloaded and installed, no errors. A restart was required, so I rebooted.

Now the boot process is ending with a command line and a startx command produces error messages - 
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9631, but this X module has the version1.0-9639. Please make sure that the kernel module and all NVIDIA driver components have the same version.

This is an existing install (of kubuntu),which has recently been taken from 7.04 to 7.10 by upgrading.
Help would be much appreciated

edit SOLVED:
I now have it working, although I have not been able to determine exactly  how.  I installed a new kubuntu in another partition in this machine, then added ubuntu-desktop, then accepted the restricted drivers install from gnome. This worked with no problems.

Revisiting the problem kubuntu system, I edited xorg.conf so that the driver was not "nvidia" but changed to simply "nv". this gave me back a display after restart, and then I used gnome (after ubuntu-desktop had been added) to accept the restricted driver. It worked ok this time.

I note that the original system had been installed with the previous video card and also that I was using kubuntu, so I tried dealing with the restricted drivers from gnome, which worked. However I am not at all sure that kde had anything to do with the problem.
hth

---

