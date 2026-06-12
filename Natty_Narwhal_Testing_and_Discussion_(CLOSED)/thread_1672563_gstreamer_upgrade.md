---
title: "gstreamer upgrade"
date: 2011-01-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-01-21
```
~$ sudo aptitude dist-upgrade 
[sudo] password for zika: 
The following packages will be upgraded: 
  gir1.2-gstreamer-0.10 gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x libgstreamer-plugins-base0.10-0 libgstreamer0.10-0{b} 
7 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,179 kB of archives. After unpacking 77.8 kB will be used.
The following packages have unmet dependencies:
  libgstreamer0.10-0: Conflicts: gstreamer0.10-plugins-bad (< 0.10.20.2) but 0.10.20-1ubuntu3 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     gstreamer0.10-plugins-bad   
2)     rhythmbox-radio-browser     



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gstreamer0.10-plugins-bad rhythmbox-radio-browser
The following packages will be upgraded:
  gir1.2-gstreamer-0.10 gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
7 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 2,179 kB of archives.
After this operation, 5,108 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by dino99 on 2011-01-21
seems you dont use main server as these updates have been done a few days ago on my system

---

### Post by meborc on 2011-01-21
from changelog:
```
gstreamer0.10 (0.10.31.3-1) experimental; urgency=low

  * debian/control.in:
    + [B]Conflict with gstreamer0.10-plugins-bad0.10 (<< 0.10.20.2) because
      of the moved selector and valve plugins[/B]. There's no file conflict.
  * New upstream pre-release:
    + debian/libgstreamer.symbols:
      - Update new symbols to the latest pre-release version.
```

I went ahead and removed the "bad" plugin, it was holding back too many updates... I can always install it again when 0.10.20.2 is out

---

### Post by zika on 2011-01-21
> **dino99 said:**
> seems you dont use main server as these updates have been done a few days ago on my systemI've never left Main server for a minute in several years... :)

---

### Post by zika on 2011-01-21
> **meborc said:**
> from changelog:
```
gstreamer0.10 (0.10.31.3-1) experimental; urgency=low

  * debian/control.in:
    + [B]Conflict with gstreamer0.10-plugins-bad0.10 (<< 0.10.20.2) because
      of the moved selector and valve plugins[/B]. There's no file conflict.
  * New upstream pre-release:
    + debian/libgstreamer.symbols:
      - Update new symbols to the latest pre-release version.
```

I went ahead and removed the "bad" plugin, it was holding back too many updates... I can always install it again when 0.10.20.2 is outWhat stops me is the removal of rhythmbox-radio-browser...
I'll see...

It seem that it went well.
Autoremove wiped:
```
freepats ...
Removing libass4 ...
Removing libcdaudio1 ...
Removing libcelt0-0 ...
Removing libdca0 ...
Removing libdirac-encoder0 ...
Removing libofa0 ...
Removing libfftw3-3 ...
Removing libflite1 ...
Removing libgme0 ...
Removing libiptcdata0 ...
Removing libkate1 ...
Removing libmimic0 ...
Removing libmms0 ...
Removing libmodplug1 ...
Removing libmpcdec6 ...
Removing librtmp0 ...
Removing libsoundtouch1c2 ...
Removing libwildmidi1 ...
Removing libzbar0 ...
Removing streamripper ...
```
(I, always, mix radio-browser in RB with real Radio menu... Would not like to loose that option...)

---

