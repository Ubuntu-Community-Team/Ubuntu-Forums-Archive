---
title: "(hardy) Stuck at 800x600 after installing the rt kernel"
date: 2008-05-19
forum: Multimedia Software
---

### Post by oskar2000 on 2008-05-19
nvidia 7600 GT

In a desperate search for fixing my audio issues, I thought maybe the Ubuntu-studio package will provide some help, since my soundcard is one of the few that is being recommended for audio editing on linux.

After the reboot, it booted into the command line. I couldn't get it fixed with the rt kernel (which didn't help my audio issues) - I reverted to the 2.6.24-16-generic kernel. a dpgk reconfigure xserver-xorg brought me back to the desktop, but with a resolution of 640x480. After uninstalling the nvidia-glx-new driver and another xserver reconfigure it boots into 800x600,. (changing the xorg.conf line from nvidia to nv didn't do it for some reason.)
I've also tried the nvidia-glx (not 'new') with the same results. Now I'm out of ideas. 
Usually when that happened I could manually add the resolution in the xorg.conf, but it looks different in Hardy.

---

### Post by oskar2000 on 2008-05-20
I tried to install the nvidia driver again using envy - no luck... this time the bullet proof x-server kicks in and gives me an option to run in low graphics mode.

Anyway - at this point I would be happy if I could switch to the nv driver - if I switch to nv in xorg.conf the x-server still won't start. 

Any ideas?

---

