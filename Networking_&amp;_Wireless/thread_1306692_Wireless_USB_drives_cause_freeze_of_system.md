---
title: "Wireless USB drives cause freeze of system"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by M_Visser on 2009-10-30
Hi all,
With 9.10 my system keeps on freezing on me. 9.04 had the same problem and it was caused bij two drivers who were simultaniously loaded (as I understood it). 
I fixed it with blacklisting the rt2500usb which left the 7500 working. 

This fix doesn't work with 9.10. Need some help repairing the system to keep it from completely freezing on me so I have to restart the hardware.

---

### Post by M_Visser on 2009-11-04
The problems seems to come from
(gnome-settings-daemon:1571): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
 so not the wireless connection after all. 

Hoping for suggestions

Extra info. Computer crashes
25.820026] Kernel panic - not syncing: Fatal exception in interupt
] Pid 1030, comm: gdm-binary Tainted: G     D    2.6.31-14generic #48-Ubuntu
][drm: intelfb_panic occured, switching back to text console. 

Then everything dies 

HELP

---

