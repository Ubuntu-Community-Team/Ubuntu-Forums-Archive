---
title: "fresh install, no dvd playback!"
date: 2010-12-06
forum: Multimedia Software
---

### Post by arnicainthemembrane on 2010-12-06
Hi, I have tried Totem, MPlayer, VLC, and Gnome Media player. Downloaded plugins automatically, tried 

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

and got

Virtual packages like 'libflashsupport' can't be removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package non-free-codecs
E: Package 'sun-java6-fonts' has no installation candidate
E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate

.... any ideas???

---

### Post by andrew.46 on 2010-12-07
Hi arnica,

> **arnicainthemembrane said:**
> .... any ideas???

Perhaps something simple:
```

sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh

```

Andrew

---

### Post by BlueSpecial on 2010-12-07
Go to Software Center and install "Ubuntu Restricted Extras". I had the same problem after installation and this solved it.

---

### Post by arnicainthemembrane on 2010-12-07
thanks for the advice... i find that vlc works now but not the others. no biggie, i like the vlc player...

---

