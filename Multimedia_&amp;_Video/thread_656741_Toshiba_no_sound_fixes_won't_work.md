---
title: "Toshiba no sound fixes won't work"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by Crusty Juggler on 2008-01-02
When I use [this]("http://ubuntuforums.org/showthread.php?t=473425&highlight=toshiba+a200+sound") sound fix and try to install the alsa driver (1.0.15), I get the following errors:
```

ryan@Toshiba-home:/usr/src/alsa/alsa-driver-1.0.15$ sudo make
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/acore'
copying file alsa-kernel/core/timer.c
/usr/src/alsa/alsa-driver-1.0.15/utils/patch-alsa: 24: patch: not found
make[2]: *** [timer.c] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15'
make: *** [include/sndversions.h] Error 2

```

Any ideas/suggestions?

---

### Post by Crusty Juggler on 2008-01-02
Also- if I follow [this]("https://help.ubuntu.com/community/SoundTroubleshooting") fix, I get the following:
```
ryan@Toshiba-home:/usr/src/alsa/alsa-driver-1.0.15$ sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
The following extra packages will be installed:
  debconf-utils debhelper dpkg-dev g++ g++-4.1 gettext html2text
  intltool-debian libstdc++6-4.1-dev patch po-debconf
Suggested packages:
  dh-make debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc cvs
  gettext-doc libstdc++6-4.1-doc diff-doc
Recommended packages:
  kernel-package fakeroot kernel-headers kernel-source kernel-source-2.4.27
  linux-source libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  alsa-source build-essential debconf-utils debhelper dpkg-dev g++ g++-4.1
  gettext html2text intltool-debian libstdc++6-4.1-dev module-assistant patch
  po-debconf
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9287kB of archives.
After unpacking 26.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by Crusty Juggler on 2008-01-03
Anyone?

---

### Post by _peter_ on 2008-01-17
> **Crusty Juggler said:**
> When I use [this]("http://ubuntuforums.org/showthread.php?t=473425&highlight=toshiba+a200+sound") sound fix and try to install the alsa driver (1.0.15), I get the following errors:
```


/usr/src/alsa/alsa-driver-1.0.15/utils/patch-alsa: 24: patch: not found
make[2]: *** [timer.c] Error 1

```

Any ideas/suggestions?

apt-get install patch

---

### Post by gwpritch on 2008-01-18
> **Crusty Juggler said:**
> Also- if I follow [this]("https://help.ubuntu.com/community/SoundTroubleshooting") fix, I get the following:
```
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Edit /etc/apt/sources.list and comment out references to the cdrom then:

```
sudo apt-get update
```

---

### Post by sweBers on 2008-03-01
> **_peter_ said:**
> apt-get install patch

You're a lifesaver.  I was getting the same when trying to make for my creative card.

---

