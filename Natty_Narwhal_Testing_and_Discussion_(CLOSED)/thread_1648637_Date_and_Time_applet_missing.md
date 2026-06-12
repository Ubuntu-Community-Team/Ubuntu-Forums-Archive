---
title: "Date and Time applet missing"
date: 2010-12-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-12-19
Do not have a Date and Time applet in Unity but noticed Daily Live had
the applet installed. Have nwmanager, battery, sound, about, mail and shutdown.
How does one get the Date and Time applet installed in the unity interface?

---

### Post by cariboo on 2010-12-19
Check to make sure you have indicator-datetime installed, if you do have it installed, purge it and re-install.

---

### Post by garvinrick4 on 2010-12-19
Was not installed.
Thank you: installed now.
```
rick@rick-laptop:/$ aptitude show indicator-datetime
Package: indicator-datetime              
State: installed
Automatically installed: no
Version: 0.1.90.is.0.0.6-0ubuntu1
Priority: optional
Section: misc
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 127 k
Depends: libc6 (>= 2.4), libdbus-glib-1-2 (>= 0.88), libdbusmenu-glib2 (>=
         0.3.90), libdbusmenu-gtk2 (>= 0.3.90), libglib2.0-0 (>= 2.26.0),
         libgtk2.0-0 (>= 2.18.0), libido-0.1-0 (>= 0.1.10), libindicator1 (>=
         0.3.15), libpango1.0-0 (>= 1.14.0)
Recommends: indicator-applet | indicator-renderer
Description: A very, very simple clock
 A simple clock appearing in the indicator bar
Homepage: https://launchpad.net/indicator-datetime
```

---

