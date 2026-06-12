---
title: "Client rejected from local host"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by anonymouscoward on 2006-06-10
I have a terrible problem with my X server.

I upgraded to Ubuntu 6.06 from 5.10. 6.06 installed the latest Nvidia driver but that didn't work for me. I followed the instructions from this forum and installed the legacy Nvidia driver. That worked, as expected. (My card is Nvidia GeForce2 MX/MX 400.)

However, even this legacy Nvidia driver has not cured one terrible problem. My gdm keeps restarting over and over. When I inspected the X log right after one restart, the last 2 lines were something like:

AUDIT: (DATE TIME) (PORT NUMBER?) X: client 2 rejected from local host
AUDIT: (DATE TIME) (PORT NUMBER?) X: client 2 rejected from local host

I logged in again, angered at this stupid problem occuring again and again. And then, another restart, but this time this message appeared at the command line at Ctrl-Alt-F7:

glibc detected *** double free or corruption *** (!prev) (HEX ADDRESS?)

Someone please help me with this. I can hardly work when the damned desktop keeps restarting for no damned reason.

Thank you.

---

### Post by anonymouscoward on 2006-06-10
gdm restarted again and the X log ends with things like:

AUDIT: Sun Jun 11 09:15:27 2006: 13962 X: client 1 rejected from local host
AUDIT: Sun Jun 11 09:15:27 2006: 13962 X: client 3 rejected from local host
AUDIT: Sun Jun 11 09:15:27 2006: 13962 X: client 1 rejected from local host
AUDIT: Sun Jun 11 09:15:27 2006: 13962 X: client 4 rejected from local host
AUDIT: Sun Jun 11 09:15:27 2006: 13962 X: client 3 rejected from local host

Now, I also checked auth.log. Nothing suspicious there, I think.

I checked kern.log and this is what I find around the time gdm restarts:

Jun 11 09:15:24 localhost kernel: [4300059.563000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jun 11 09:15:24 localhost kernel: [4300059.564000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jun 11 09:15:24 localhost kernel: [4300059.565000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jun 11 09:15:25 localhost kernel: [4300060.152000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jun 11 09:15:25 localhost kernel: [4300060.153000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jun 11 09:15:25 localhost kernel: [4300060.153000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

Why is the kernel apparently detecting my Nvidia card again and again every now and then? Could this be the source of the bug?

---

### Post by anonymouscoward on 2006-06-10
Wait! Right before that in kern.log, I see:

Jun 11 09:15:22 localhost gconfd (username-12747): Received signal 15, shutting down cleanly
Jun 11 09:15:22 localhost gconfd (username-12747): Exiting
Jun 11 09:15:23 localhost gdm[12671]: Error reinitilizing server

And then, after the AGP detection notices, there are notices for gconfd starting for `username` and root (presumably all over again).

---

### Post by ivangetov on 2006-10-09
hi i have the same problem upgrading 6.06 to 6.10-beta. do tou find a solution of this problem? i'm using voodoo banshee

---

### Post by redsek on 2006-10-24
Hi,

I had the same problem recently with some  system upgrades. gdm would spontaneously restart every 20 mins or so.

The Xorg log file report indicated the problem.

(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
AUDIT: Mon Oct 23 20:11:37 2006: 26491 X: client 2 rejected from local host
AUDIT: Mon Oct 23 20:11:37 2006: 26491 X: client 4 rejected from local host

The problem was that the symbolic link /usr/lib/xorg/modules/extensions/libglx.so  was broken. The glx module had somehow been removed during the upgrade (I guess). (The glx module was built by the NVIDIA driver installer NVIDIA-Linux-x86-1.0-8774-pkg1.run for me). 

Running glxinfo would trigger the problem and cause the gdm restart.

I resolved this by reinstalling the NVIDIA driver. No more error messages, no more restarts.

---

### Post by xsism on 2007-01-14
> **redsek said:**
> Hi,

I had the same problem recently with some  system upgrades. gdm would spontaneously restart every 20 mins or so.

The Xorg log file report indicated the problem.

(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
AUDIT: Mon Oct 23 20:11:37 2006: 26491 X: client 2 rejected from local host
AUDIT: Mon Oct 23 20:11:37 2006: 26491 X: client 4 rejected from local host

The problem was that the symbolic link /usr/lib/xorg/modules/extensions/libglx.so  was broken. The glx module had somehow been removed during the upgrade (I guess). (The glx module was built by the NVIDIA driver installer NVIDIA-Linux-x86-1.0-8774-pkg1.run for me). 

Running glxinfo would trigger the problem and cause the gdm restart.

I resolved this by reinstalling the NVIDIA driver. No more error messages, no more restarts.

This happened when the new xorg and xorg-dev updates came a couple days ago. I fixed it by going into synaptic and reinstalling nvidia-glx and rebooting. Everything seems great again and no more system halts.

that helped, but I also had to reinstall the Nvidia binary driver. I still had the .run file so that was easy at least!
:)

---

### Post by Kaso_Da_Zmok on 2008-01-15
Thanks, reinstaling the NVIDIA driver did help.. i am on Arch linux.
:popcorn:

---

### Post by tom1200 on 2008-01-28
Thanks, reinstalling the NVIDIA drivers helped also on Mandriva.

---

### Post by dannystaple on 2008-01-30
Thanks all - solved my problem in no time. On a related note, does anybody know which nvidia driver version the restricted-modules package for Gutsy is currently using? I had video issues with drivers earlier than 169.07.

---

