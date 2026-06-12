---
title: "Upgrade killed NVIDIA driver, unable to re-enable."
date: 2008-05-30
forum: Multimedia Software
---

### Post by pseudo-random on 2008-05-30
About 2 days ago I installed some updates which have broke my X server.
I've had this before in the past and set about re-installing the Nvidia driver both manually and with EnvyNG only to have it fail again.
I've currently removed all nvidia and envy related packages from synaptic and binned my xorg.conf which ironically gives me the best resolution yet (1680x1050) compared with the default low res 800x600 I was getting earlier.
However, any attempt to install the nvidia driver breaks the X server and gives me the fail-safe mode.
Also, In System > Administration > Hardware Drivers my Nvidia 8600GT is no longer visible! I've re-installed jockey to try to fix that and still no joy.
I'm guessing this is a kernel upgrade issue?
Anytime I would try the Nvidia restricted driver I'd get this error in my Xorg.0.log:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
I've tried different versions of glx (-legacy, -new etc) to no avail.
I've also tried older kernels from within grub.
Attached is an example xorg.conf generated during another unsuccessful attempt at driver install.

I've followed dozens of tuts but have yet to find one that works for me since most finish up with "..tick 'enable' in hardware drivers, then reboot and enjoy!" That would be great if I had anything in there...
[IMG]http://wintolin.co.uk/images/nvidia-wtf.jpg[/IMG]
:confused:

---

### Post by pseudo-random on 2008-05-31
Backed up then Re-installed. Now back to normal.
Decided it was quicker than the xorg trial and error methods which were taking too long.
:)

---

### Post by Plasma_NZ on 2008-05-31
Ok - each time there's a kernel update my drivers die aswell.. so i just reinstall them as such...

Im running NVIDIA's drivers from there website and un-installed the drivers for my 2 8500GT's that came with ubuntu.. had no-end of problems...


Download drivers from NVIDIA.. uninstall ubuntu NVIDIA drivers..

press ctrl + alt + f1 - will boot you to prompt

sudo /etc/init.d/gdm stop
goto where u downloaded the nvidia drivers too..
sudo sh NVIDIA-DRIVER-NAME and follow directions....

once thats all done, type startx to restart GUI - from in there once X has started.. u can run
sudo nvidia-settings - and configure to your liking..

also if u get the error u mentioned above - in the GUI type sudo nvidia-xconfig - then reload gdm and run sudo nvidia-settings 

Hope this helps..

---

### Post by crosssover on 2008-05-31
> **pseudo-random said:**
> About 2 days ago I installed some updates which have broke my X server.
I've had this before in the past and set about re-installing the Nvidia driver both manually and with EnvyNG only to have it fail again.
I've currently removed all nvidia and envy related packages from synaptic and binned my xorg.conf which ironically gives me the best resolution yet (1680x1050) compared with the default low res 800x600 I was getting earlier.
However, any attempt to install the nvidia driver breaks the X server and gives me the fail-safe mode.
Also, In System > Administration > Hardware Drivers my Nvidia 8600GT is no longer visible! I've re-installed jockey to try to fix that and still no joy.
I'm guessing this is a kernel upgrade issue?
Anytime I would try the Nvidia restricted driver I'd get this error in my Xorg.0.log:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
I've tried different versions of glx (-legacy, -new etc) to no avail.
I've also tried older kernels from within grub.
Attached is an example xorg.conf generated during another unsuccessful attempt at driver install.

I've followed dozens of tuts but have yet to find one that works for me since most finish up with "..tick 'enable' in hardware drivers, then reboot and enjoy!" That would be great if I had anything in there...
[IMG]http://wintolin.co.uk/images/nvidia-wtf.jpg[/IMG]
:confused:

i've had the same problem, I tried everything and couldn't fix it
think i'll get back to 7.10 a compile a new kernel.

Hardy is by far the worst ubuntu release !!!

---

### Post by Plasma_NZ on 2008-05-31
> **crosssover said:**
> i've had the same problem, I tried everything and couldn't fix it
think i'll get back to 7.10 a compile a new kernel.

Hardy is by far the worst ubuntu release !!!

Have u tried the method i mentioned.?

---

### Post by doobrain on 2008-05-31
Yep, happened to me too.

Had to uninstall and reinstall twice in the last couple of days (using the latest driver from NVIDIA's site).

---

