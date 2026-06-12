---
title: "Intel HD Graphics i5 not detecting monitor"
date: 2012-02-23
forum: Multimedia Software
---

### Post by snafu_az on 2012-02-23
I have an HP touchsmart 610 all-in-one that i have been trying to install Ubuntu 11.10 64bit on.  I have been working on this over a month now and the only way i can ge it to work is if I put nomodeset or i915.modeset=1 in grub.

With nomodeset it comes up in vesa mode, which is 1280x1024. The display on this unit is 24" 1920x1080.

If I don't use nomodeset the screen cycles through white screen then red, then blue then green. it jus does this over and over.

I hae installed all the updates, the edgers drivers and tried multiple suggestions found on other threads here, and on other site.  So far nothing has worked.

i have even tried mint, fedora, centos and open suse.  They all do the same thing if i don't use nomodset.

One thing I do find in Xorg.0.log is ....

    11.562] (II) intel(0): Output VGA1 has no monitor section
[    12.200] (II) intel(0): Output HDMI1 has no monitor section
[    12.248] (II) intel(0): Output DP1 has no monitor section
[    12.888] (II) intel(0): Output HDMI2 has no monitor section
[    12.936] (II) intel(0): Output DP2 has no monitor section
[    12.936] (II) intel(0): EDID for output VGA1
[    13.576] (II) intel(0): EDID for output HDMI1
[    13.624] (II) intel(0): EDID for output DP1
[    14.264] (II) intel(0): EDID for output HDMI2
[    14.312] (II) intel(0): EDID for output DP2
[    14.312] (II) intel(0): Output VGA1 disconnected
[    14.312] (II) intel(0): Output HDMI1 disconnected
[    14.312] (II) intel(0): Output DP1 disconnected
[    14.312] (II) intel(0): Output HDMI2 disconnected
[    14.312] (II) intel(0): Output DP2 disconnected
[    14.312] (WW) intel(0): No outputs definitely connected, trying again...
[    14.312] (II) intel(0): Output VGA1 disconnected
[    14.312] (II) intel(0): Output HDMI1 disconnected
[    14.312] (II) intel(0): Output DP1 disconnected
[    14.312] (II) intel(0): Output HDMI2 disconnected
[    14.312] (II) intel(0): Output DP2 disconnected
[    14.312] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer

I think this is where the problem is but don't know how to fix it.

Forgot to mention Windows 7 works fine so it's not a hardware problem.

Any help would be appreciated.

---

