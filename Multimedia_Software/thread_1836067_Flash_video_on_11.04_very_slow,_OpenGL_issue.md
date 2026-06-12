---
title: "Flash video on 11.04 very slow, OpenGL issue?"
date: 2011-08-30
forum: Multimedia Software
---

### Post by papacarlo on 2011-08-30
I have the following issue, after the upgrade to 11.04 x64 the online flash video in Firefox/ Opera works very slow(slide show). 
I use gnome without Unity.
My hardware is fast enough to play video even in HD(Notebook HP Compaq Presario CQ56-103SG with 2,3 GHz, ATI HD 4250), proprietary ATI graphics driver is installed, all updates are installed.

I've found that the issue was OpenGL/Compiz. If OpenGL option was switched off, the performance of flash video increases, but after that, the window manager did not worked properly(artifacts, errors etc.)

Under 10.10 flash video works fine, with full activated 3D desktop effects...

thanks for your hints!

---

### Post by Enigmapond on 2011-08-30
Open Firefox and install the Flash-Aid addon:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Run the script and let it install the current version of flash and delete anything conflicting. Changes will be system-wide.

PS Welcome to the forum!

---

### Post by lovinglinux on 2011-08-30
> **Enigmapond said:**
> Open Firefox and install the Flash-Aid addon:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Run the script and let it install the current version of flash and delete anything conflicting. Changes will be system-wide.

PS Welcome to the forum!

Make sure to get [version 2.2.1 of Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/"), to avoid a bug that affects Firefox 6 compatibility.

---

### Post by drawkcab on 2011-08-31
If you are running x64 then install the x64 flash beta and you will no longer hate your life.

[http://www.ubuntugeek.com/how-to-install-adobe-flash-11-beta-2-on-ubuntu-64-bit-using-ppa.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-11-beta-2-on-ubuntu-64-bit-using-ppa.html)

---

