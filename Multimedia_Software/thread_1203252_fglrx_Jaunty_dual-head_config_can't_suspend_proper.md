---
title: "fglrx Jaunty dual-head config can't suspend properly"
date: 2009-07-03
forum: Multimedia Software
---

### Post by syncopatod on 2009-07-03
Hi,

I have a Radeon HD 4670 with two 1680x1050 LCD monitors running Jaunty 9.04 with fglrx.  The dual-head setup seems to work for the most part, with each monitor displaying its own left or right part of the desktop.

However, the screen never sleeps or suspends, despite the ServerFlags settings I have in the xorg.conf.  Additionally, if I force the display to sleep using "xset dpms force sleep", it works, but when I wake it up with keyboard or mouse activity, the display wakes up to clone mode -- both monitors display the same thing, and the virtual desktop scrolls left and right as my mouse moves on the left and right edges of the display.

How can I make the system sleep properly after the timeout I specify?  How do I make it wake up to a proper dual-head setting?  Currently, my only way to reset the bad display is to reset X.

```
Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Device"
        Identifier  "ati-a"
        Driver      "fglrx"
        Screen      0
        BusID       "PCI:1:0:0"
        Option      "ConnectedMonitor"  "DFP, DFP"
EndSection

Section "Device"
        Identifier  "ati-b"
        Driver      "fglrx"
        Screen      0
        BusID       "PCI:1:0:0"
        Option      "ConnectedMonitor"  "DFP, DFP"
EndSection

Section "Monitor"
        Identifier   "Acer AL2216W"
        Option       "DPMS"
EndSection

Section "Screen"
        Identifier "screen-a"
        Device     "ati-a"
        Monitor    "Acer AL2216W"
        DefaultDepth     24
EndSection

Section "Screen"
        Identifier "screen-b"
        Device     "ati-b"
        Monitor    "Acer AL2216W"
        DefaultDepth     24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "screen-a" Absolute 0 0
        Screen          "screen-b" RightOf "screen-a"
EndSection

Section "ServerFlags"
        Option "DontZap" "false"
        Option "StandbyTime"    "30"
        Option "SuspendTime"    "30"
        Option "OffTime"        "30"
EndSection

```

---

### Post by syncopatod on 2009-07-03
I would like to add that the same mess-up with the display cloning happens when I switch off one of the monitors and then switch it back on.  Seems like somebody is detecting when a monitor becomes unavailable but not when it becomes available.

---

### Post by zorgo1 on 2009-07-04
I see the same thing with the proprietary ati driver v9.6.

Booting with acpi=no doesn't help.

---

