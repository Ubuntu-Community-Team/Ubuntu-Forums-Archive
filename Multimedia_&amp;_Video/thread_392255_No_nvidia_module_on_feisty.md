---
title: "No nvidia module on feisty"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by sickrandir on 2007-03-24
Hi, 
I use the latest feisty upgraded from a previous installation of edgy and my grafic card is a nvidia geforce 440 mx (supported by the 9631 driver)
Since I made the upgrade, every time I boot the xserver doesn't start giving me the following error:
> 
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Could not open '/lib/modules/2.6.20-12-generic/volatile/nvidia.ko': No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.


If I try to do: ```
sudo modprobe nvidia
``` it tells me that the module is missing.

Doing: ```
sudo aptitude reinstall linux-restricted-modules-`uname -r` nvidia-glx 
``` works and makes the xserver start but it's a temporary solution because every time I boot the problem comes out again the same!

Anyone has an idea for a permanent fix?

P.S: maybe could be useful to know that on edgy I installed the nvidia driver with envy but now since the script is not available for feisty I removed it.

Thanks for the attention

sickrandir

---

### Post by Digitallysick on 2007-03-25
i did sudo nano /etc/X11/xorg.conf

i found where it says "nvidia" and checked it to "nv" saved my xorg and started x, at least it gets your desktop back up, im searching for a fix as well

---

### Post by fenian on 2007-03-25
I used the guide [here]("https://help.ubuntu.com/community/MythTV/Install/Live/Feisty+/Hardware/Video_Nvidia?highlight=%28nvidia%29") to get mine working.I think because of the upgrade you need to reinstall the driver and linux-restricted-modules.

---

### Post by sickrandir on 2007-03-27
Thanx fenian!! It worked!
I suspect it was a dependecy problem so the fix should only be:
```
# sudo /etc/init.d/linux-restricted-modules-common start
# sudo depmod -a
```

Thanx again

sickrandir

---

