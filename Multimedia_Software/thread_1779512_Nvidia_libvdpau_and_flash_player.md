---
title: "Nvidia libvdpau and flash player"
date: 2011-06-10
forum: Multimedia Software
---

### Post by Noiano on 2011-06-10
Hello everyone,
Some time ago I installed libvdpau1 vdpau-va-driver along with nvidia-current package from repo and I created the usual mms.cfg under /etc/adobe to make flash use my GPU (nvidia 8600 M GT). Everything was working fine: flash was gpu accelerated.
Later on I uninstalled the libvdpau1 vdpau-va-driver in order to disable gpu acceleration on flash because I had some problems.

Now I changed my mind again and I would like to enable it again. Strangely I had no success with latest flash player 10.3. Feels like there's something missing under /usr/lib

```


noiano@DELL-noiano:/usr/lib$ ll vdpau
lrwxrwxrwx   1 root root    38 2011-06-06 20:27 libvdpau_nvidia.so.1 -> /etc/alternatives/libvdpau_nvidia.so.1
lrwxrwxrwx   1 root root    23 2011-06-10 20:53 libvdpau_trace.so.1 -> libvdpau_trace.so.1.0.0
-rw-r--r--   1 root root 54584 2010-12-13 20:13 libvdpau_trace.so.1.0.0

```

Are there some symblinks that need to be created manually? I tried to reinstall nvidia-current and libvdpau1 vdpau-va-driver but nothing.

I hope someone can shed some light on the mistery ;)

PS: ubuntu 11.04  :D

---

### Post by beew on 2011-06-10
If you install flash with FireFox's flash-aid addon it will automatically configure flash to use VDPAU if available.

---

### Post by Noiano on 2011-06-11
> **beew said:**
> If you install flash with FireFox's flash-aid addon it will automatically configure flash to use VDPAU if available.

that plugin only creates the mms.cfg file and puts in the usual options ... I already did that ;)

---

### Post by Noiano on 2011-06-11
I tried to reinstall nvidia-current using apt-get install --reinstall ... Here's what I got...

```

Unpacking replacement nvidia-current ...
Processing triggers for man-db ...
Setting up nvidia-current (270.41.06-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-current/ld.so.conf because link group gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-270.41.06 DKMS files...
Building only for 2.6.38-8-generic-pae
Building for architecture i686
Building initial module for 2.6.38-8-generic-pae
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic-pae
Processing triggers for python-support ...
noiano@DELL-noiano:~$ cat /usr/lib/nvidia-current/ld.so.conf 
/usr/lib/nvidia-current


```

Seems like something goes wrong when some symblinks have to be created...

---

### Post by Noiano on 2011-06-12
up

---

