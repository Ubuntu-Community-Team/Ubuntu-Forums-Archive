---
title: "Flashplayer Firefox/Chromium"
date: 2009-08-12
forum: Multimedia Software
---

### Post by Hawk__0 on 2009-08-12
I am trying to install flashplayer in firefox (64 bit kubuntu 9.04) and depending on which plugin I use (for some reason there is a plugin I can't find out how to remove) I either get a gray screen where the video is supposed to be, or the video plays and there is no sound.

How can I purge this other plugin, and how can I install a working player?

---

### Post by aysiu on 2009-08-13
Try pasting these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove swfdec-mozilla
sudo apt-get install --reinstall flashplugin-nonfree
``` Then close Firefox and start it again.

---

### Post by Hawk__0 on 2009-08-13
Didn't change anything :(

Just for the hell of it I tried seeing what the output of running firefox from the command line would do, this is all that showed up:

```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(npviewer.bin:16403): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

```

---

### Post by aysiu on 2009-08-13
That's something else entirely:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/369719](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/369719)

---

### Post by Hawk__0 on 2009-08-14
I gave up and installed 32 bit kubuntu9.10.  Installs went as normal.

---

