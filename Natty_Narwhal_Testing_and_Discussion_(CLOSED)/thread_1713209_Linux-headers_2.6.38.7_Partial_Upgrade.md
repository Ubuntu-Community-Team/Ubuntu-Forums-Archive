---
title: "Linux-headers 2.6.38.7 Partial Upgrade"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by snlzkn on 2011-03-23
I have been using Natty since the first alpha. Today I saw some updates and updated using aptitude dist-upgrade. It said it will remove one of the ubuntu-one packages and I said it is fine. After the installation when it tries to configure the following packages I get error. Here is the error:
```

The following partially installed packages will be configured:
  initramfs-tools linux-image-2.6.38-7-generic 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

Setting up initramfs-tools (0.98.8ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.38-7-generic (2.6.38-7.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-7-generic
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-7-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.38-7-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-7-generic
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-7-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-7-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.98.8ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.38-7-generic (2.6.38-7.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-7-generic
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-7-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.38-7-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-7-generic
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-7-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.38-7-generic
 initramfs-tools

```

Did any body else who applied this update got this error?
lspci | grep VGA gives this and I have open source ati drivers with compiz enabled unity.

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

---

### Post by uRock on 2011-03-23
Bump for move to separate thread.

---

### Post by PWill on 2011-03-23
I got this error, too. update-initramfs says something about libpango not being found. I'm going to try installing the development headers for libpango. I'm afraid to restart if my kernel images haven't been updated.

---

### Post by paul_in_london on 2011-03-23
+1 on one of my Natty installs initially, but you should find it's ok if you update/upgrade again now.

---

### Post by snlzkn on 2011-03-23
Yes the problem is solved but I got this message during installation:
```
gtk-update-icon-cache-3.0: The generated cache was invalid.

```
I think that will not be an issue probably another update will fix it really soon. Whenever I check there is an update, so much to fix! My unity keeps crashing, I am looking forward to updates of compiz and unity :D

---

### Post by BrainwreckedTech on 2011-03-23
Confirmed as fixed.  I even went to file a bug report on it after re-doing the update/upgrade cycle.  Should have known something was in the works when I saw compiz being held back.

---

### Post by sauthess on 2011-03-24
Hi,

Same problem on fresh install (alpha 3 64 bits version):

update-initramfs: Generating /boot/initrd.img-2.6.38-5-generic
cp: cannot stat `/usr/lib/x86_64-linux-gnu/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-5-generic
dpkg*: erreur de traitement de initramfs-tools (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1
Traitement des actions différées («*triggers*») pour «*python-support*»...
Des erreurs ont été rencontrées pendant l'exécution*:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

Manually solved with :
cd /usr/lib/x86_64-linux-gnu/
ln -s /usr/lib/pango

and relaunched upgrade after these two commands.

If you could solve this issue on 64 bit version I (and all other users ;) ) ill thank you a lot.

Thanks,

BR

---

### Post by comrobo on 2011-03-25
i copied pango folder from "/usr/lib/i386-linux-gnu" to "/usr/lib/" and no more errors.

---

### Post by AxeZn on 2011-04-26
> **comrobo said:**
> i copied pango folder from "/usr/lib/i386-linux-gnu" to "/usr/lib/" and no more errors.
Epic. Thanks.

---

