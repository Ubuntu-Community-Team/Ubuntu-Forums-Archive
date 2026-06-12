---
title: "Nvidia driver problems"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by trakie on 2007-06-02
So I'm running feisty and have a geforce something card.  my installation history for drivers goes as follows:

nvidia from website (9742 or something i think)
then there was an update and these stopped working so i went back to nv driver in xorg
got annoyed because no 3d support so i downloaded and installed the newest nvidia drivers from their website, version 9755.

ok so thats what im using right now and it works, until i restart.  when ubuntu boots it fails to start the xserver, then i run sudo init 1, and install the newest nvidia driver again, and then sudo init 3, and here i am typing away with a working nvidia driver.

i thought there still might be an issue with the nvidia-glx drivers so i did a apt-remove nvidia-glx, and i still have the same problem.

any thoughts?

---

### Post by edubbler on 2007-06-02
try running

NVIDIA-Linux-x86-1.0-9755-pkg1.run --x-module-path=`X -showDefaultModulePath 2>&1 | cut -d, -f1` --x-library-path=`X -showDefaultLibPath 2>&1`

---

### Post by FuturePilot on 2007-06-02
If you're running Feisty it would be easier to install the driver with the Restricted Driver Manager. If you want the latest driver 9755, install the package nvidia-glx-new.
```
sudo apt-get install nvidia-glx-new
```

---

### Post by chicoicho on 2007-06-02
> **trakie said:**
> So I'm running feisty and have a geforce something card.  my installation history for drivers goes as follows:

nvidia from website (9742 or something i think)
then there was an update and these stopped working so i went back to nv driver in xorg
got annoyed because no 3d support so i downloaded and installed the newest nvidia drivers from their website, version 9755.

ok so thats what im using right now and it works, until i restart.  when ubuntu boots it fails to start the xserver, then i run sudo init 1, and install the newest nvidia driver again, and then sudo init 3, and here i am typing away with a working nvidia driver.

i thought there still might be an issue with the nvidia-glx drivers so i did a apt-remove nvidia-glx, and i still have the same problem.

any thoughts?

Next time use Automatix2 for nvidia driver.

---

### Post by Nythain on 2007-06-02
or not mess with automatix or the .run file from nvidia's site and just sudo apt-get install nvidia-glx-new, it will install the restricted modules package if not already, then gksudo nvidia-settings, make changes, save changes, and restart x with controll alt backspace

---

