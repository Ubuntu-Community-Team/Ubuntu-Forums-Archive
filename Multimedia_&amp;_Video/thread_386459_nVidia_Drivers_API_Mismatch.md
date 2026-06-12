---
title: "nVidia Drivers: API Mismatch"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by w1llywonka on 2007-03-17
I have been following this guide of about 6 hours now, [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA), trying to get Beryl to work.    Basically I cannot install the nVidia drivers because when I do I get an error message saying API Mismatch your precompiled kernel interface is 7184, your nVidia drivers are 9746.  I tried uninstalling the drivers and then running Envy, which just turned my screen black and didn't do anything.  I also tried installed version 9775 of the nVidia drivers, didn't work.  I also tried disabling the nv module, that did nothing.  

What exactly do I need to do get the drivers to work?

---

### Post by packjamNL on 2007-03-17
Did you install the NVidia drivers before or after "Beryl"
You save yourself a lot of time to 1st install the NVidia drivers , -run -q, 
so maybe uninstall Beryl 1st.
My screensaver doesn't work with Beryl and gDesklets (launcher) has a huge black background I can't get rid off.
Maybe somebody knows how to set the prefs for that one.

---

### Post by w1llywonka on 2007-03-17
I installed the nVidia drivers first.  I don't know how to uninstall Beryl and would want to avoid going through the installation again.

---

### Post by w1llywonka on 2007-03-17
I completely reinstalled Ubuntu and followed the installation instructions again.  It failed to load the graphical interface and now I am stuck in the same place again.

---

### Post by w1llywonka on 2007-03-23
These instructions fixed the problem:  HOWTO: Install Latest NVIDIA Display Driver (Directly from Nvidia: current 1.0-9755) from Ubuntu Forums.  I don't know what exactly is different from the Beryl website instructions but finally it worked.

---

