---
title: "System Beep Does Not If Compiz is Enabled"
date: 2009-12-16
forum: Multimedia Software
---

### Post by RichardGv on 2009-12-16
**Environment:**
Ubuntu 9.10 Desktop
Compiz 0.8.4 (1:0.8.4-0ubuntu2)
CCSM 0.8.4 (1:0.8.4-0ubuntu2)
Compiz Fusion Icon 0.1.0-2

**Problem:**
I found system bell/beep *(in sound theme "Ubuntu" ([FONT=monospace]/usr/share/sounds/ubuntu/stereo/bell.ogg[/FONT]), not the one playing in PC speaker)* does not work when Compiz is enabled, when "Audible Bell" in "General Options" in CCSM is enabled.
When I select "Metacity" instead of "Compiz" in "Select Window Manager" in Compiz Fusion Icon, the bell starts working.
All other sounds in "ubuntu" sound theme works correctly.
I wonder if it is a known bug, or caused by misconfiguration? Thanks in advance.

---

### Post by etank on 2010-04-06
I have had the exact same issue on Ubuntu (9.04) and Fedora (12). If you find the fix please post what it was.

---

### Post by RichardGv on 2010-04-07
> **etank said:**
> I have had the exact same issue on Ubuntu (9.04) and Fedora (12). If you find the fix please post what it was.

No, I did not find any way to fix it. Actually I switched to Gentoo and stopped using Compiz and GNOME. (I'm using fvwm now.) The system beep never worked since then, as I did not compile pcspkr to my kernel.

---

