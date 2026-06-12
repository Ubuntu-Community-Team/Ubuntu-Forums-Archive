---
title: "nvidia driver problem"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by delta99 on 2006-09-23
hello, I need help because I can't seem to get it working.

I followed [This Guide]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") but it don't work.

When I type "sudo nvidia-glx-config enable" into terminal, I get this error:
> 
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
delta@delta-desktop:~$


I have edited my xorg file and changed driver to "nvidia"... Still won't work. My linux-restricted-modules are the same version as my kernel.


This is whats installed: (Synaptic)

Package: linux-restricted-modules-2.6.15-26-386
Installed Version: 2.6.15.11-4

Package: nvidia-glx
Installed: 1.0.8762+2.6.15.11-5

Package: nvidia-kernel-common
Installed Version: 20051028+1

Package: smartdimmer
Installed Version: 0.1-2

Package: xserver-xorg-driver-nv
Installed Version: 1:1.0.1.5-0ubuntu4

Any advice please. Not sure what my next move is, thank you.;) 

(my videocard is BFG 7800GT (sli, but just 1 card)

---

### Post by tseliot on 2006-09-23
that command is broken.

You should use:
```
sudo nvidia-xconfig
```

And restart the Xserver.

If the driver doesn't work, try point 4 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by delta99 on 2006-09-23
thanks, yes that command worked or at least no errors. I don't see the nvidia logo but nvidia-settings works fine.

cheers
ps: no tv-out, but I guess look into that

---

