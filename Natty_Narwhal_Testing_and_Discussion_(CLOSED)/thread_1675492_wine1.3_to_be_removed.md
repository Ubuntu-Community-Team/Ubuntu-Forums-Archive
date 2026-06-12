---
title: "wine1.3 to be removed"
date: 2011-01-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-01-25
Watch that fine print if you have wine1.3 installed. Hopefully this will be resolved soon

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[B]The following packages will be REMOVED:
  wine1.3 wine1.3-gecko[/B]
The following NEW packages will be installed:
  indicator-applet-appmenu indicator-applet-complete libdrm-nouveau1a
  libpoppler-glib6 wine1.2 wine1.2-gecko
The following packages will be upgraded:
  apport apport-gtk apport-kde binfmt-support binutils bzr dmsetup evince
  evince-common gcalctool gdm gir1.2-panelapplet-3.0 gnome-panel
  gnome-panel-bonobo gnome-panel-data gnome-power-manager hpijs hpijs-ppds
  hplip hplip-cups hplip-data libdevmapper1.02.1 libdrm-dev libdrm-intel1
  libdrm-radeon1 libdrm2 libevdocument3 libevview3 libglib2.0-0 libglib2.0-bin
  libglib2.0-data libglib2.0-dev libgpg-error0 libhpmud0 libkms1
  libpanel-applet-3-0 libpanel-applet2-0 libpci3 libpcre3 libproxy0
  libsane-hpaio libsmbclient libsoprano4 libtalloc2 libtdb1 libwbclient0
  linux-firmware pciutils policykit-desktop-privileges python-apport
  python-libproxy python-problem-report samba-common samba-common-bin
  smbclient soprano-daemon ttf-symbol-replacement-wine1.3 tzdata tzdata-java
  ubuntu-sso-client update-notifier update-notifier-common winbind
  x11proto-randr-dev xserver-xorg-input-wacom xserver-xorg-video-intel
  xserver-xorg-video-siliconmotion
67 upgraded, 6 newly installed, 2 to remove and 0 not upgraded.
Need to get 90.0 MB of archives.
After this operation, 10.9 MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by ibuclaw on 2011-01-25
> **buzzmandt said:**
> Watch that fine print if you have wine1.3 installed. Hopefully this will be resolved soon


I can't see wine1.3 in the official repository, only wine1.2...

---

### Post by rajeev1204 on 2011-01-26
This is a problem with the wine PPA i believe because iam using 10.10 Maverick and i got this today.

---

### Post by twigusa on 2011-01-26
I had this too with Maverick PPA and had to install / upgrade wine independently:

apt-get install wine1.3

This resolved the problem.

Cheers,
Twig.

---

### Post by dino99 on 2011-01-26
all was fine on my end, use maverick-ppa too on i386

---

