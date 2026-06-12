---
title: "Avant and Emerald still here but GONE"
date: 2009-03-26
forum: Multimedia Software
---

### Post by VastOne on 2009-03-26
Greets...

Have had Avant and Emerald working flawlessly for over a year and today, out of nowhere neither will work..They are loading, but not working. If I kill and then restart Avant, the "normal" flash of it appears to start but it never shows up at all. My emerald theme is not loading at all. 

There have been no changes to my nVidia driver, nothing within the past updates have touched the video side, unless there has been an update to X that I did not see or pay close enough attention to...

Compiz is on the fritz too....No cube actions or anything related to Compiz that also ran flawlessly until today

Enlighten me please

---

### Post by Lunx on 2009-03-27
Is your 'puter still set to extra under the visual effects tab in appearance? I had similar issue a while back because that setting changed itself for some odd reason.

---

### Post by VastOne on 2009-03-27
> **Lunx said:**
> Is your 'puter still set to extra under the visual effects tab in appearance? I had similar issue a while back because that setting changed itself for some odd reason.

No.  The Extra affects has been turned off and it will not allow me to turn it back on with a generic message that it could not be enabled,

The same is true for the Normal selection

Running Compiz-Check script I get the following:


vastone@VastOne-UbuntuHH:~/Downloads$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8500 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

_______

The following is from my xOrg.0.log

Failed to initialize the GLX module; please check in your X
NVIDIA(0):     log file that the GLX module has been loaded in your X
NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
NVIDIA(0):     you continue to encounter problems, Please try
NVIDIA(0):     reinstalling the NVIDIA driver.

Thanks

---

### Post by VastOne on 2009-03-27
> **Lunx said:**
> Is your 'puter still set to extra under the visual effects tab in appearance? I had similar issue a while back because that setting changed itself for some odd reason.

Was able to install nVIdia's latest drivers and get everything back the way that it was working before...

Sure wish I knew what the culprit was that did in all my settings...but...

SOLVED!!!

Thank you!

---

### Post by Lunx on 2009-03-27
> **VastOne said:**
> Sure wish I knew what the culprit was that did in all my settings...but...

SOLVED!!!

Thank you!

No worries, I've got no idea why it happens either, but at least you got it sorted.

---

