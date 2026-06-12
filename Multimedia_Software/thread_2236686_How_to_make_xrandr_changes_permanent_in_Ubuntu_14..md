---
title: "How to make xrandr changes permanent in Ubuntu 14.04"
date: 2014-07-28
forum: Multimedia Software
---

### Post by bproffit on 2014-07-28
I have scanned the forums and found all kinds of tips on how to make xrandr changes permanent, but none of them seem to work with Ubuntu 14.04.  In fact, most of them reference directories that don't exist in that distro.  Since I installed a KVM switch, Ubuntu now boots in 1024x768 rather than 1366x768 mode.  I can change it with xrandr, but none of the tricks seem to make that change work across boots.  Any idea what is different about 14.04 and where I can make them permanent?

Thank!

---

### Post by Yellow Pasque on 2014-07-28
/etc/X11/xorg.conf does not exist by default, but you can create one. Start with a skeleton and add the modeline in the Monitor section as shown here: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf:](https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf:)
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

