---
title: "Display issues with SONY Bravia after update"
date: 2011-12-24
forum: Multimedia Software
---

### Post by bublehead688 on 2011-12-24
I just installed an update to my Lucid HTPC and now my Sony Bravia TV shows up great just after reboot and then makes the entire screen black from the bottom up to about half of the top menu bar shortly after login. I checked several threads and did what they suggested with no joy. Most of them had me check the TV settings with no joy and one(listed below) had me ensure the display settings were at normal. Which they were.
[http://ubuntuforums.org/showthread.php?t=1564650](http://ubuntuforums.org/showthread.php?t=1564650)

I am running my HTPC on a ZOTAC ION with atom processor Lucid 10.04.3 LTS and onboard NVIDIA card for display.
[INDENT]03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
	Subsystem: ZOTAC International (MCO) Ltd. Device a113
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at fafe0000 [disabled][size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb,nouveau[/INDENT]
I also made a copy of the Xorg.0.log file which is attached if that will help. Thanks very much for anyone who has this issue or can figure out what is going on. If I can't get an answer on this I guess I will have to try and roll back the updates that were done today.

---

### Post by bublehead688 on 2011-12-25
Replying to my own post here. I have been able to fix my issue with the display on the Bravia. I basically uninstalled the NVIDIA drivers and blacklisted the nouevau driver and then reinstalled the newest drivers from the NVIDIA site.

I was able to make this change by logging into the computer under the safemode. By doing this I was able to make all of the file adjustments by command line. This [thread]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") was immensely helpful.

If you have the same issue please feel free to contact me if this doesn't work.

---

