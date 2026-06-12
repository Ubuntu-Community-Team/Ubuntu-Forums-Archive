---
title: "Nvidia problems on Ubuntu 10.04"
date: 2010-05-07
forum: Multimedia Software
---

### Post by kabeza on 2010-05-07
Hi
I've upgraded this morning to 10.04 (from 9.10)
All went fine, except that I've got a bad resolution (4:3 ratio, rest black) after restarting PC and starting ubuntu/gdm again

I went through this

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

But got not a lot of luck. I could not install drivers (downloaded driver again) due a problem related to nvidia.ko module => latest kernel stuff

The other problem I'm having is that I can't see each window's windowbar, I mean, the bar that contains:
- window title
- maximize, minimize, close buttons
- etc.

PS: I've been running compiz in 9.10, should this affect to windowbarless windows -knowing that nvidia driver wasn't installed correctly-?

I have a Samsung 943 monitor 19" ws, nvidia GEForce 8400 Gs on an Intel C2D with 2gb ram

Thanks a lot in advance for any tip you can give me ):P

---

### Post by davoudi on 2010-06-01
[http://ubuntuforums.org/showthread.php?t=1470822](http://ubuntuforums.org/showthread.php?t=1470822)

---

### Post by kabeza on 2010-06-02
thanks davoudi
I could solve that problem by trying lots of reinstallation procedures for the NVidia driver, until I succeeded, but the "problem" I had later was this:

[http://ubuntuforums.org/showthread.php?t=1466638](http://ubuntuforums.org/showthread.php?t=1466638)

Thanks a lot anyway...

---

### Post by farbird on 2010-06-02
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install nvidia-current
sudo apt-get install libvdpau*

that shd give u a nvidia driver that will not be affected by kernel updates.

---

