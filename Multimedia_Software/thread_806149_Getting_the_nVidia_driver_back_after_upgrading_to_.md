---
title: "Getting the nVidia driver back after upgrading to 8.04"
date: 2008-05-24
forum: Multimedia Software
---

### Post by W3ird_N3rd on 2008-05-24
So you made the upgrade from Ubuntu 7.10 to 8.04, but now where's my nVidia?

I ran into the problem of not being able to enable the driver again. In System > Administration > Hardware Drivers, they were not available. 3D was working fine before the upgrade.

So here's the solution in my case: go to System > Administration > Synaptic Package Manager. Hit "search" and seach for packages with "restricted-modules" in their name. Most likely in this case, you will find a package like:
```
linux-restricted-modules-2.6.22-14-generic
```
to be installed. 2.6.22-14 is the kernel you were using on Ubuntu 7.10, so this is not working anymore. To fix it, look for this package:
```
linux-restricted-modules
```

Right-click the linux-restricted-modules and click "Mark for Installation", accept the additional required changes. Click Apply and wait a bit for it to be completed and close synaptic. At this point I restarted the computer, I'm not sure if that would be absolutely necessary but it won't harm. Click System > Quit... > Restart to do it.

When the computer started again, click System > Administration > Hardware Drivers. You should now be able to enable the nvidia driver the normal way. Enable the checkbox for "Enabled" and close the window, and restart the computer. If all went well, you should be able to start gazing at glxgears once again!

[edit]
Guide fixed so you don't run into trouble when you update your system.

---

### Post by K.Mandla on 2008-05-29
Moved to Multimedia and Video.

---

