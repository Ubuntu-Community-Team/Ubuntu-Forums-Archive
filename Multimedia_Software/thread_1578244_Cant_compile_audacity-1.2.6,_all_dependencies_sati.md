---
title: "Cant compile audacity-1.2.6, all dependencies satisfied"
date: 2010-09-20
forum: Multimedia Software
---

### Post by Vigh on 2010-09-20
configure: error: Unable to locate a suitable configuration of wxWidgets v2.4.x.
The currently available configurations are listed below.  If necessary, either
install the package for your distribution or download the 2.4.x version of
wxWidgets from [http://wxwidgets.org](http://wxwidgets.org).
To help configure find the right version set WX_CONFIG to point to it.
wxWidgets 2.5.x and 2.6.x are NOT supported!

but I thought I installed widgets 2.4??? where did they go???

help please

---

### Post by Vigh on 2010-09-20
I need to set wx-config to point to wxwidgets2.4 how do I do this?

---

### Post by mc4man on 2010-09-20
Edit: usually not a great idea to post ?'s about the same  - you should have mentioned you built wxwidgets2.4 rather than doing a package install which would be the preferred method
=======================================================================
You use alternatives, pick the wgtk option (if you have all the 2.4 and 1.2 libs installed 


```
sudo update-alternatives --config wx-config
```

Ex. (on maverick - note this requires some packages installed

> sudo update-alternatives --config wx-config
There are 6 choices for the alternative wx-config (providing /usr/bin/wx-config).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
* 0            /usr/lib/wx/config/gtk2-unicode-release-2.8   288       auto mode
  1            /usr/bin/wxbase-2.4-config                    247       manual mode
  2            /usr/bin/wxgtk-2.4-config                     248       manual mode
  3            /usr/lib/wx/config/base-unicode-release-2.6   267       manual mode
  4            /usr/lib/wx/config/base-unicode-release-2.8   287       manual mode
  5            /usr/lib/wx/config/gtk2-unicode-release-2.6   268       manual mode
  6            /usr/lib/wx/config/gtk2-unicode-release-2.8   288       manual mode

---

