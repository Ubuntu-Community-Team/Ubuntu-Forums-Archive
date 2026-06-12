---
title: "Dell Precision M65, DVI does not work with Edgy"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by Kurgan_it on 2006-10-28
Maybe I should have posted in the installation forum, but this is a video issue, so I posted here. Hope I got to the right forum.

I have tried installing Edgy on a Dell Precision M65 using an external monitor connected to a docking station via DVI connector, but it seems that video drivers do not work properly when booting from the (live) CD. If I use standard boot, video stays blank with just some random pixels lit on the top row. If I use "safe mode" for video, I get an error that says that CPU#0 suffered a soft lock just before the point where video should go into graphic mode.

Booting with the internal monitor (laptop undocked) works flawlessly in standard (non-safe) mode. The two monitors have the same resolution (1680x1050).

I'm not interested in dual monitor, just in using the external monitor connected to the docking station OR (not AND) the internal monitor when disconnected. 

Is this a known issue? I have searched the forums and found lots of issues with DVI and dual monitors, but nothing about my setup.

Thanks a lot.

---

### Post by Kurgan_it on 2006-11-09
I have found that lockup depends on ACPI and not video drivers. I still haven't found what exactly locks up.

---

### Post by Kurgan_it on 2007-01-08
I have finally solved my problem, that is related to Intel wireless NIC. The bug showe up only when docked, this behaviour was misleading and made me think about something about docking, while it was wireless-related. 

I'm writing this post to leave a trace on the forum to help people that have the same problems.

You should download a patched driver for youw intel wireless NIC. Read about it in this bug:

[http://ubuntuforums.org/showthread.php?t=322180](http://ubuntuforums.org/showthread.php?t=322180)

---

