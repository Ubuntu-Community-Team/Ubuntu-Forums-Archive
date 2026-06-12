---
title: "Color calibration"
date: 2013-01-07
forum: Multimedia Software
---

### Post by Da_Panther on 2013-01-07
Hey,
I've been looking around all evening, but I can't seem to find how to calibrate my color profile, other than with XGamma .... none to pleasant to use when you are fussy like me.

Anybody manage to calibrate the color profile on 12.10? I'm running an early 2008 MacBook 2.4 core 2 duo. thanks.

---

### Post by tgalati4 on 2013-01-07
tgalati4@Dell600m-mint14 /var/log $ apt-cache search color calibration
gir1.2-gxps-0.1 - GObject introspection data for the gxps library
libgxps-dev - handling and rendering XPS documents (development files)
libgxps-doc - library for handling and rendering XPS documents (documentation)
libgxps2 - handling and rendering XPS documents (library)
argyll - Color Management System, calibrator and profiler
argyll-dbg - debugging symbols for argyll
colorhug-client - Tools for the Hughski Colorimeter
dispcalgui - Graphical user interface for the Argyll CMS.
gir1.2-colorhug-1.0 - GObject introspection data for the Hughski Colorimeter
kgamma - monitor calibration panel for KDE
libcolorhug-dev - Devel files for the Hughski Colorimeter
libcolorhug1 - Library for the Hughski Colorimeter
libgxps-utils - handling and rendering XPS documents (utilities)
r-cran-rocr - GNU R package to prepare and display ROC curves

Mac OS X has some nice, integrated color management tools that work across many applications and are easy to use for a quick calibration or a more-detailed color analysis.  I have yet to see such tools in linux.  I'm not familiar with Argyll, but you might check it out and tell us its deficiencies.

---

