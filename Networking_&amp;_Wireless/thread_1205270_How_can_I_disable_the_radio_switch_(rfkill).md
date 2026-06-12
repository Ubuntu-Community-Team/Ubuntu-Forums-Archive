---
title: "How can I disable the radio switch (rfkill)?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Cherry Cotton on 2009-07-05
I’m using the unstable Karmic Koala right now, and a new version of my wireless driver, “ath5k”, has added support for the radio switch (a.k.a. “airplane switch”, or “kill switch”) on my ThinkPad X61 Tablet, allowing me to use it to turn off wireless support. That’s great, obviously, but I actually liked it when it didn’t work, because then I used the switch for something else: my custom /etc/acpi files used the radio switch state (detected through “thinkpad_acpi”) to determine which direction my tablet screen should rotate (clockwise or counterclockwise) when I put the system in tablet mode.

Short version: How do I make everything ignore the radio switch? I want it enabled only enough that “thinkpad_acpi” can see it, but not so much that it actually serves its intended purpose of disabling wireless signals. Any ideas?

Thanks!

(I can post those custom ACPI files if you want. The short version there is that “/sys/devices/platform/thinkpad_acpi/hotkey_radio_sw” is used to detect the switch state—which is used as “should the screen rotate left or right” when changing to tablet mode—and I’ve placed a file in “/etc/acpi/events/” that detects the radio switch’s ACPI hotkey and runs a short script that refreshes the tablet orientation. Okay, that wasn’t short... sorry...)

---

