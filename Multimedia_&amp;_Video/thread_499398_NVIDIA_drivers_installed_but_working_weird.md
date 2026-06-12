---
title: "NVIDIA drivers installed but working weird"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by DavidCar on 2007-07-12
Hi!

I installed nvidia restricted drivers, but I'm having a rather strange problem. I have to install the drivers EACH time I restart my computer. The first time I installed the drivers everything worked out and I even tried beryl (AT LAST!!!:P), but then, after I restarted my PC the X server wasn't working with the driver and i got this message in the log.

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0): that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0): that the NVIDIA device files have been created properly.
(EE) NVIDIA(0): Please consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aborting ***

Thnx in advance and sorry for my bad english.

---

### Post by oscarsfriend on 2007-07-12
I just had the exact same problem.  Starting with a fresh kubuntu install, I followed method 2 from here: [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2)

startx worked fine.  I rebooted, then found X wouldn't start!  Figured out that after typing "modprobe -r nvidia" then X works with startx, until I reboot.  Then spent several hours fiddling about and getting nowhere fast.

Finnally I cracked it!  apt-get shows no nvidia drivers already installed (when I tried to remove them just in case, as per link above, said they were not installed).  But they were installed!  'modprobe -l | grep "nvidia"' shows 4 different nvidia drivers -- the date on one the files is today's date (when I installed nvidia's binary), the others are older.

The solution: edit /etc/default/linux-restricted-modules-common and modify the last line to read: DISABLED_MODULES="nv nvidiafb nvidia_new nvidia_legacy"

Now works perfectly!

---

### Post by DavidCar on 2007-07-12
FIXED!!!!

Thanx oscarsfriend!!!! It was exactly like u said!!! just that in my case I had 5 drivers (one called nvidia-agp plus the ones u said). Anyway, thanx for your help!!!

---

