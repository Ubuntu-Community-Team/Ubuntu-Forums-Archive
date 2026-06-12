---
title: "Missing video mode for Bush LCD TV in Karmic (Worked in Jaunty)"
date: 2010-02-14
forum: Multimedia Software
---

### Post by thepurpleblob on 2010-02-14
I have Mythbuntu on a macmini (1,1) into an old-ish Bush LCD32TV009HD. It's an Intel video chipset. With Jaunty all its video modes were automatically recognised including its native 1366x768. With Karmic it no longer works - the default resolution has become a terrible looking 1280x768. 

Progress so far...
* Googled and everybody says "add the resolution to xorg.conf". Karmic, no longer has an xorg.conf and although I understand that I can use one if I want I don't have the experience (or particularly want to acquire it) to hand-craft one. I can't find a way that works to make one automatically.
* This page - [https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution) - looked very hopeful. In particular the very last part - "It worked in Jaunty but not in Karmic". This says "You can test this by rebooting Karmic with the kernel parameter modeset=0". 
* Ok - how do I do that? Grub has been replaced by Grub2 and I can find no reference anywhere to adding kernel parameters. It used to be easy in Grub but now it isn't (or it isn't obvious).

I'm sure all these changes are an improvement, it just doesn't feel like it right now. Can anybody suggest how I can (quickly/easily) get my video mode back? 

Any help appreciated!

---

