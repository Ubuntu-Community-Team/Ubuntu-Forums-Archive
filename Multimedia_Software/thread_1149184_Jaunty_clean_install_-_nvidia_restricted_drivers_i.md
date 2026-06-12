---
title: "Jaunty clean install - nvidia restricted drivers impossible to get working"
date: 2009-05-05
forum: Multimedia Software
---

### Post by procogent on 2009-05-05
I'm astounded I can't find a solution for this:

[LIST=1]
[*]Performed clean install of Ubuntu 9.04 Jaunty x64 (kernel 2.6.28-11-generic) using alternate install disc.
[*]Installed nvidia-glx-180 (plus dependencies) via Synaptic.
[*]Ran "sudo nvidia-xconfig".
[*]Reboot
[*]ERROR!:  Ubuntu is running in low-graphics mode... Failed to load NVIDIA kernel module... Screen(s) found, but none have a usable configuration.
[/LIST]

This is entirely reproducible.  Is it my hardware or what?  What else needs to be done to get it working?  I've tried:

[LIST]
[*]Using avenard repositories and loading his driver
[*]Completely uninstalling all nVidia packages and reinstalling
[*]Booting into console, stopping GDM, and installing/reinstalling via apt-get
[*]Using restricted driver manager to activate driver
[*]Running "sudo dpkg-reconfigure xserver-xorg"
[*]Downloading the latest driver from nVidia and using their installer
[*]Doing every combination of the above in just about every order
[/LIST]

My hardware:

[LIST]
[*]Gigabyte MA790GP-DS4H System Board
[*]Gigabyte Geforce 9800GT Video Card
[/LIST]

There has to be something I'm missing.  This config worked fine in Intrepid.  I'm ready to pay money to get someone to tell me what's going on here.

---

### Post by caver1 on 2009-05-05
I had the same problem at first. Go back int Synaptic and 
remove everything Nvidia. Then reload only the Nvidia 180.
don't run sudo nvidia-xconfig.
Reboot. everything should be fine.
You might have to set your resolution etc. But I found that everytime
I ran sudo nvidia-xconfig I always ended up with nothing.
One other thought did you do a clean install or upgrade through 
Synaptic.
I found that with a clean install I had no problems with graphics but with the upgrade route that's all I had.
caver1

---

### Post by MichaelNW on 2009-09-10
In my case, September 2009, running the nvidia-xconfig did create a functional /etc/X11/xorg.conf

Environment:
Asus M3N79-VM MB with integrated nVidia GeForce 8200 video controller.

Installed:
nvidia-kernel-common
nvidia-glx-180
nvidia-settings
nvidia-180-modaliases 
nvidia-180-libvdpau

---

