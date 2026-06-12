---
title: "Intermittent vnc/svn disconnects"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by hydrofarm on 2011-10-18
We're running 11.10 on a Dell PowerEdge 1850 and after two fresh installs we are still having the same problem.

Though ping responses both from and to the server (from another pc) don't ever time out, we're getting disconnected intermittently from vnc as well as svn.  Reconnecting can take 5-10 attempts, sometimes more.  

At first we thought it was only happening with vnc but after setting up svn we get the same symptoms when trying to connect to our repositories.

Running dmesg | grep -i error returns:

[   22.716556] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.083974] Contact your BIOS vendor to see if the E752x error registers can be safely un-hidden
[   32.457712] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   35.087891] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[17028.608464] CIFS VFS: Send error in read = -512
[254889.029471] CIFS VFS: Send error in SessSetup = -13
[255028.554735] CIFS VFS: Send error in SessSetup = -13

---

