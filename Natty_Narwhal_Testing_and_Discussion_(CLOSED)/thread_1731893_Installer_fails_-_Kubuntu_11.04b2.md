---
title: "Installer fails - Kubuntu 11.04b2"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by SeijiSensei on 2011-04-17
I tried installing 11.04b2 from the CD today.  I have a quad-core Acer with 4 GB of memory and an NVIDIA 9500 GT graphics card.  The display is a Sony KDL-40V3000 television using a DVI<>HDMI cable.  I've been running 10.10 successfully on this configuration for months and recently upgraded to KDE 4.6.2 from backports.

The installer displayed the Kubuntu splash screen with the animated dots.  However when it was ready to move on to installation, it crashed with a video panic.  It switched to text mode to write the panic to the screen then hung.  I'm afraid I don't have the exact texts of the errors for you.  I could probably write them down and post them if it would be helpful.

I've had persistent issues with installing to this video/display combination, but not crashes like this one.  In every version of Ubuntu and Kubuntu I've installed, the texts are displayed in an unreadable miniscule font.  I can manually intervene and add an

```
Options "DPI" "100x100"
```

in the Device stanza of xorg.conf after I've generated that file with the nvidia-xconfig application.  I was fully prepared to follow the same annoying routine again this time around, but I never got far enough into the installation to do so.

---

### Post by ikt on 2011-04-17
[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

Remote debugging ftw!

---

