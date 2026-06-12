---
title: "trying to get out of low graphics mode"
date: 2008-08-18
forum: Multimedia Software
---

### Post by philosophyguy on 2008-08-18
Hi all! I'm relatively new to ubuntu, and so far I've managed to solve any issues I've had without having to post here, but this one has been frustrating me to no end.

I recently installed the ubuntustudio-video and ubuntustudio-audio packages (I'm currently running Hardy 8.04). So when I rebooted after the initial installation, ubuntu started in low graphics mode saying that it did not recognize my graphics card. There was no NVIDIA splash screen. The NVIDIA drivers were no longer working and every time I tried to reinstall them, it didn't work (i.e. I'd still startup in low graphics mode at 800 x 600).

After reading through many forum posts, I discovered that there are issues with the -rt kernel and the NVIDIA drivers. So I
[LIST]
[*]uninstalled nvidia-settings and nvidia-glx-new and downloaded the latest legacy driver from NVIDIA 
[*]installed linux-headers-rt
[*]went into recovery mode and installed the NVIDIA driver manually
[/LIST]

When I rebooted, it was no longer in low graphics mode, but instead went to a default resolution of 640 x 480. I tried to change the resolution through nvidia-settings, but this was the highest available option. All the 3D acceleration stuff worked though (cube spinning, advanced desktop effects, etc.). But needless to say, I can't work at a resolution that low. I attempted using dpkg-reconfig xserver-xorg to no avail. 

I've since gone back to the glx drivers which don't really work with the rt kernel, and I'm back in low graphics mode (800 x 600).

All I want is some way of getting 1024 x 768 resolution.

Help?

---

