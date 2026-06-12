---
title: "How to force nfs shares to mount in fstab BEFORE gdm loads"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by kevinfishburne on 2011-05-31
I just upgraded my kernel in Ubuntu 10.10 to 2.6.38.7-candela, and subsequently the desktop is loaded before my nfs share mounts in my fstab:

[FONT="Courier New"]# Data partition
lycaeum:/media/Data		/media/Data					nfs					defaults
[/FONT]
It mounts while gdm is in the middle of loading, as my wallpaper is displayed but launcher images and panel backgrounds aren't loaded until I log out and back in.

Is there a way to force the system to stop booting until the nfs share is mounted? It seems all boot tasks are performed in parallel without regard to dependency in this case.

---

