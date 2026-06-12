---
title: "FYI: Solution to Xorg crash with FireGL V3100"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by mathiasv on 2006-11-30
Hey. 

After upgrading from Dappy to Edgy I began getting problems running LS-dyna prepost through ssh. With different intervals my Xorg crashed, shutting down all programs and forcing me to log in again. The driver installed in synaptics was: xserver-xorg-video-ati and /etc/X11/xorg.conf said:

```
Section "Device"
  Identifier  "ATI Technologies, Inc. RV370 5B64 [FireGL V3100 (PCIE)]
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

```

My solution which has stopped the frequent crashes, is as follows.
Through synaptics install: xorg-driver-fglrx.
Change /etc/X11/xorg.conf to:

```
Section "Device"
  Identifier  "ATI Technologies, Inc. RV370 5B64 [FireGL V3100 (PCIE)]
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

```

Hope this is useful to someone.
Mathias

---

