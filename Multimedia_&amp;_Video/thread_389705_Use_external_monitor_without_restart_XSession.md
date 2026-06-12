---
title: "Use external monitor without restart XSession"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by alexlzl on 2007-03-21
Recently installed Ubuntu Egdy Eft on my Dell D610 laptop. I use external monitor port for presentation very often, one thing very annoying is: I have to restart XSession if it was started without the external monitor (projector) connected.

After spending couple of days struggling with all kinds of dual-monitor solution, the answer finally pops up from an very old post somewhere (Google is getting less helpful recently). I only tried with ATI Radeon:

```

Section "Device"
        Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        **Option "ForceMonitors" "LVDS,CRT1"**
EndSection

```

The default mode is "mirror", which is perfect for presentation. To adjust resolution to fit projector, you can use "xrandr -s".

To save power (since external CRT is always on), you can do "sudo radeontool dac off/on" to switch it off/on.

Hope this can help.

---

