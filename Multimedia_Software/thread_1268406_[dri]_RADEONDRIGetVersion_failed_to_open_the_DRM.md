---
title: "[dri] RADEONDRIGetVersion failed to open the DRM"
date: 2009-09-16
forum: Multimedia Software
---

### Post by PeEllAvaj on 2009-09-16
I just ran an update on this laptop to the latest version of the kernel (.31), in preparation for Karmic, and I've been having issues with the ATI card in the computer.  Specifically, I can't get compositing back.

The most relevant error I have been able to find is in the Xorg.0.log from x startup:
[dri] RADEONDRIGetVersion failed to open the DRM

Any recommendations?  I have tried moving between fglrx versions, I have tried switching to the opensource drivers, but nothing get's compositing back.

Thanks!

---

### Post by markbuntu on 2009-09-17
WHat card do you have????

---

### Post by MarcoPau on 2009-09-20
Same problem here, card is 01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450.


Any hint?

---

### Post by Yellow Pasque on 2009-09-21
Make sure the intel modules aren't loaded and interfering. This is a known, high-priority bug: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/392039](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/392039)

Fortunately, you can work around it (read the comments in that bug report).

---

### Post by PeEllAvaj on 2009-09-21
Mobility Radeon HD 3400 Series is the card I'm using.

I have tried the module blacklisting that you shared from the Launchpad bug. It looks like the modules were loading, but I have added the blacklist and prevented from drm and i915 from loading (tried having each running), and fglrx is loading properly.

glxinfo still returns:
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


/var/log/Xorg.0.log reports the following errors with the card:
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(EE) RADEON(0): Acceleration initialization failed
(EE) GLX error: Can not get required symbols.

---

### Post by Yellow Pasque on 2009-09-22
The log indicates you're using the open-source radeon driver, but you keep mentioning Catalyst/fglrx. Check that your xorg.conf is set to load flgrx, and if necessary, run:
```
sudo aticonfig --initial
```

---

### Post by PeEllAvaj on 2009-09-22
Wow, that fixed it.

I distinctly remember fglx being specified in my xorg.conf file at many points throughout this ordeal. It must have gotten reset at some point while trying to install/upgrade/downgrade/reinstall fglrx (which required me to remake the xorg.conf file probably 10-16 times).

I wonder if it was the combination of the blacklisting and the actually specifying the fglrx driver that fixed it, or if it was the 8.660 version that came out.

THANK YOU SO MUCH!

---

