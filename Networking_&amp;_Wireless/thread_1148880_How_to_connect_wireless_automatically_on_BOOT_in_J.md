---
title: "How to connect wireless automatically on BOOT in Jaunty (Gnome)"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by drivebull on 2009-05-04
I recently discovered how to make Network Manager connect automatically to wireless on boot (in Jaunty, Ubuntu 9.04).

Open a Terminal Window and type: gconf-editor

Navigate the Configuration Register:
/system/networking/connections/1/connection

The variable "autoconnect" is set to FALSE (default).
Check it to make it TRUE.

That's it!

It should also work on Intrepid, but I didn't test it.

---

### Post by RedSingularity on 2009-05-04
I am surprised you had to do that.....usually it is set like that already.

---

