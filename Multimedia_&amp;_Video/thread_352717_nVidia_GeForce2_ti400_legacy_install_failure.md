---
title: "nVidia GeForce2 ti400 legacy install failure"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by o4tuna on 2007-02-03
Ubuntu 6.10
Athlon 3000+
nVidia GeForce2 ti400 (0x0151)

Tried these instructions:
If you have an amd duron/athlon you should probably install this kernel package :
Code:

$sudo aptitude install linux-k7


To install the legacy (proprietary) nvidia driver :
Code:

$sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r` $sudo nvidia-xconfig

Don't forget to do a reboot.


Looked good, but on reboot, I'm still stuck at 800X600
So I ran through the procedure a second time, so I could capture the results...
With these results:

#sudo aptitude install linux-k7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

#sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

#sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

reboot again, still stuck at 800X600

Looked up how to test for driver installed correctly, found:
glxinfo | grep direct

It errors out, so I guess it's not installed?

Looked in /etc/X11/xorg.conf, shows my monitor & card by name...

---

