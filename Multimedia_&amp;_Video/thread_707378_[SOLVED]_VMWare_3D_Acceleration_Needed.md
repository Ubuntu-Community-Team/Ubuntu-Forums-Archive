---
title: "[SOLVED] VMWare 3D Acceleration Needed"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by scrop on 2008-02-25
I've been following the instructions in the manual for enabling acceleration. I've added this to the vmx file of a non-running vm.

mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"

when I start the vm, vmware immediately flips that mks.enable3d setting back to FALSE.
I can't find any error in the logs or information about this. Can someone please help?

Latest Gutsy in use
Latest NVIDIA driver in use (desktop is accelerated, no trouble here)
GeForce 8600 GT

Guest OS is WinXP w/ VMWare Tools installed. From watching the log file, it looks like VMWare toggles this setting to false on me before the Guest OS ever starts.

---

### Post by scrop on 2008-02-28
The VMWare forums have been having some issues for a few days. Users can't login w/o being taken to the registration screen in an endless loop. I even called them and they had the same issue on their end.

Anyway, after experimentation, I found that VMWare will silently disable 3d support if you don't specify this parameter correctly.

svga.vramSize = "67108864"

If this works out to be anything other than the exact size of the memory your graphics card has then w/o warning or errors being logged you just get reverted to no 3d.

How about a round of applause for that user experience?

---

### Post by oakgrove on 2008-02-29
*How about a round of applause for that user experience?*

That's comedy gold right there, folks.

---

