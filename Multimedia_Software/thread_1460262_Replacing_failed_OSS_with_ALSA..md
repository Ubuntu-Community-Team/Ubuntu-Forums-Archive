---
title: "Replacing failed OSS with ALSA."
date: 2010-04-22
forum: Multimedia Software
---

### Post by cloroxmartini on 2010-04-22
So I tried to install OSS to see if it would allow my mircophone to work properly in the WinXP guest I was running in VirtualBox. I couldn't get it to install properly so now I'm left without any sound on my system. I was wondering how I could get rid of what ever files from OSS that are left and reinstall ALSA.

I'm running Ubuntu 9.10.

---

### Post by Yellow Pasque on 2010-04-22
If you made a .deb like the OSS guide suggested, removing OSS4 is easy. Stop all audio apps/mixers and:
```
sudo soundoff
sudo dpkg -P oss-linux
```

```
sudo dpkg-reconfigure linux-sound base
```
Select ALSA.

```
sudo apt-get install alsa-base alsa-utils pulseaudio gstreamer0.10-pulseaudio libsdl1.2debian-pulseaudio libcanberra-pulse
```

If you made any customizations to audio config files, revert them. If you have any instances of libflashsupport.so on your system, remove them.

---

