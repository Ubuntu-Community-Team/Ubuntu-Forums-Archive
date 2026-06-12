---
title: "nvidia driver issues after upgrade"
date: 2008-04-25
forum: Mythbuntu
---

### Post by straxus on 2008-04-25
I just upgraded to hardy, and now X refuses to start with the restricted nvidia driver.  It's failing over to the vesa driver.  If I try to select the nvidia driver and click 'test', I get "Configuration Test Failed".  I have a GeForce 6200 and I'm using the s-video out to my TV.

Edit:

From the xorg error log:
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***

lsmod shows "nvidia", though.

---

### Post by superm1 on 2008-04-25
> **straxus said:**
> I just upgraded to hardy, and now X refuses to start with the restricted nvidia driver.  It's failing over to the vesa driver.  If I try to select the nvidia driver and click 'test', I get "Configuration Test Failed".  I have a GeForce 6200 and I'm using the s-video out to my TV.

Edit:

From the xorg error log:
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***

lsmod shows "nvidia", though.
Did you install a newer version at some point?   check dmesg and see what it claims.  Look in /lib/modules/2.6.24-16-generic for multiple nvidia.ko's

---

### Post by straxus on 2008-04-25
I've only tried using 169.12 from the repo so far.

[   82.939792] NVRM: API mismatch: the client has the version 169.12, but
[   82.939795] NVRM: this kernel module has the version 71.86.04.  Please
[   82.939797] NVRM: make sure that this kernel module and all NVIDIA driver
[   82.939798] NVRM: components have the same version

And I don't see any nvidia.ko's in there.

---

### Post by oboedad55 on 2008-04-25
> **straxus said:**
> I've only tried using 169.12 from the repo so far.

[   82.939792] NVRM: API mismatch: the client has the version 169.12, but
[   82.939795] NVRM: this kernel module has the version 71.86.04.  Please
[   82.939797] NVRM: make sure that this kernel module and all NVIDIA driver
[   82.939798] NVRM: components have the same version

And I don't see any nvidia.ko's in there.

Can you do a clean install and just copy your /home over? I always do a  clean install. Maybe things are better now but in the past any time I did an upgrade there were some weird problems. It could save you time in the long run.

Cheers,

---

### Post by straxus on 2008-04-25
Found them:
/lib/modules/2.6.24-16-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.24-16-generic/volatile/nvidia.ko
/lib/modules/2.6.24-16-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.24-16-generic/volatile/nvidia_new.ko

---

### Post by straxus on 2008-04-25
> **oboedad55 said:**
> Can you do a clean install and just copy your /home over? I always do a  clean install. Maybe things are better now but in the past any time I did an upgrade there were some weird problems. It could save you time in the long run.

Cheers,

I could, but I'd prefer to fix the problem and learn about it in the process.  Also, I'm very close to having it fixed now.

---

### Post by straxus on 2008-04-25
The last piece of the puzzle before I crash for the night:

I can modprobe nvidia_legacy, and it loads.
But neither nvidia nor nvidia_new show up in an lsmod after modprobeing them.

---

### Post by laga on 2008-04-25
Do you have /etc/modprobe.d/lrm-video and /sbin/lrm-video on your box? Do you have /lib/linux-restricted-modules/.nvidia_legacy_installed or /lib/linux-restricted-modules/.nvidia_new_installed?


> 
I can modprobe nvidia_legacy, and it loads.

Does that mean X loads or that the kernel module loads?

---

### Post by straxus on 2008-04-25
The module.

Since that's the case, I assume that if I were to install the nvidia-glx-legacy package, X would load fine.  But since that's about as useful to me as the open source nv driver, I'm using the latter until I can get nvidia-glx-new working.

---

### Post by straxus on 2008-04-25
This is interesting.  On my laptop (where everything is working fine after the upgrade) these are the only nvidia ko's that exist:

/lib/modules/2.6.24-16-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia/nvidiafb.ko


The other three present on my Mythbuntu machine are not on this one.  That's a pretty good lead. Maybe I can make something happen now.

---

### Post by straxus on 2008-04-25
I went back into the Mythbuntu box, and discovered that the three ko's that existed earlier (nvidia_legacy, nvidia, nvidia_new) were gone.  Likely as a result of my purging the restricted packages and reinstalling them in an attempt to sort this mess out.  I don't know how they got there in the first place, but they didn't belong there.

Still, at boot the legacy nvidia module is loaded somehow.  If I unload it:

```
sudo modprobe -r nvidia
```

And then load the correct modules:

```
sudo modprobe nvidia-agp
sudo modprobe nvidiafb
```

Everything is happy.  So now, I just need to determine where that legacy module is located, and why it's getting loaded at boot.  Any ideas?

---

### Post by straxus on 2008-04-25
> **laga said:**
> Do you have /etc/modprobe.d/lrm-video and /sbin/lrm-video on your box? Do you have /lib/linux-restricted-modules/.nvidia_legacy_installed or /lib/linux-restricted-modules/.nvidia_new_installed?

Oh dear.  I missed this part of your post completely.  I hope you didn't think I was being rude.  I just don't start waking up really good for a few hours.

/etc/modprobe.d/lrm-video, /sbin/lrm-video, and /lib/linux-restricted-modules/.nvidia_new_installed all exist.

---

### Post by straxus on 2008-04-25
I still have no idea why it's behaving this way (and would really like to understand what happened), but I found a workaround.  If anyone knows of a better way to handle this, please let me know.

I added this line to /etc/default/linux-restricted-modules-common
```
DISABLED_MODULES="nvidia nvidia_legacy"
```

And also appended the following to /etc/modules
```
nvidia-agp
nvidiafb
```

Now the nvidia driver and X are happy.

---

### Post by Etlaesium on 2008-05-14
I did the following per this thread...
```

sudo /etc/init.d/gdm stop
sudo modprobe -r nvidia
sudo modprobe nvidia-agp
sudo modprobe nvidiafb
sudo apt-get install nvidia-glx
sudo /etc/init.d/gdm start

```

And also appended the following to /etc/modules
```

nvidia-agp
nvidiafb

```

Now, my nVidia Corporation NV20 [GeForce3] (rev a3) card and Gateway2000 EV-700 monitor work in conjunction to give higher resolutions than the horribly default 800x600.

:)

---

