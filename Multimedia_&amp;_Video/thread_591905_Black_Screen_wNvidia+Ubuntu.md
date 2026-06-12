---
title: "Black Screen w/Nvidia+Ubuntu"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by SoAnIs on 2007-10-25
Ubuntu 7.10 AMD64 Install. Worked fine. Enabled the Nvidia driver via the Restricted Drivers Manager. X fails, leads to a black screen. Monitor seems to be in standby mode (orange LED instead of green).
Nvidia GeForce 7900 GT, CRT Monitor. The card has 2 DVI ports and one S-Video/Component port. With the base of the card to the right the order is: Svid, DVI2, DVI1. I MUST use DVI2, DVI1 is bad.
LiveCD works. Default install works. Adding the Nvidia driver via the restricted drivers manager fails, & it then proceeds to stay failed.
Tried with normal (non AMD64 cd) same result.Tried 7.04 (normal and AMD64) same result.
Tried setting the "Driver" line in xorg.conf back to "nv". No change.
No errors in /var/log/xorg.0.log
Ctrl+Alt+Backspace does nothing.
Ctrl+Alt++ Does nothing.
Tried Dexconf.
Tried Dpkg-reconfigure -phigh xserver-xorg.
Tried Nvidia-xconfig.
Tried Nvidia-glx-configure enable
Tried the following settings in Xorg.conf in various sets (depending on various other forum posts & net searches, etc.)
Option "ConnectedMonitor" "CRT"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option  "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" "Off"
Option "UseEdidFreqs" "False"

---

### Post by sanddgroper on 2007-10-26
I tend to remember something like this with CRT monitors
if the screen resolution is to high for the monitor.Have you
tried running with a 800x600 resolution to see if it works then.

Cheers
Sandy

---

### Post by SoAnIs on 2007-10-27
Tried that, no effect.
Re-installed Ubuntu. Installed the driver via the Restricted Drivers Manager. Instead of rebooting pressed Ctrl+Alt+Backspace. Got the following error in xorg.0.log
Failed to initialize GLX extension (Compatible NVIDIA X driver not found.)
Synaptic listed Nvida-GLX-New as being installed, and that is the right driver for my card (7900 GT).

---

