---
title: "Your progress report for Nvidia GLX 180.22 on 32 or 64 bit Intrepid"
date: 2009-01-18
forum: Multimedia Software
---

### Post by sofasurfer on 2009-01-18
Many people, especially myself, are not able to install the Nvidia GLX 180.22 (or maybe some others also) graphics driver. 

I am wondering if there is any differance in success stories between 32 bit and 64 bit in regards to installing these drivers.

I know that with Hardy, I always used 32 bit because I found that there were reports of difficulties with some applications when installing on 64 bit Hardy. I, personnally could not run Skype until I switched from 64 bit to 32 bit Hardy. So I quess this is a legitimate inquiry.

---

### Post by silentknyght on 2009-01-19
Intrepid 8.10 64bit, geforce 9500gt

I had a significant amount of problems upgrading from the 180.06 beta drivers to the 180.22 release.  I was able to install the 180.06 beta drivers without using any uninstall/purge of the existing/previous drivers.  However, the same straightforward approach caused either a low-graphics mode and a complete refusal to run.

I ended up using a purge nvidia* command (can't find the reference for it atm) to remove practically everything.  The 180.22 drivers installed, but with 2-3 warnings about a failure to create/modify a file or some such, but ultimately X restarted and I was able to access the X nvidia control panel to confirm the 180.22 drivers were running.  I haven't run any serious graphical apps to confirm that I still didn't bork things, but it appears to be running okay so far.

~SK

---

