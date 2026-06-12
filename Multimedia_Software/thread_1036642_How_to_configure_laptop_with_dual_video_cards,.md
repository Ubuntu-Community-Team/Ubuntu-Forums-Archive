---
title: "How to configure laptop with dual video cards,"
date: 2009-01-11
forum: Multimedia Software
---

### Post by evilmonkeygib on 2009-01-11
After install ubuntu will load normally, it starts gnome, but will not display the graphical interface, just a text based interface.

Tried startx - outputted:

Primary device is not PCI
(EE) No device detected.
Fatal server error:
no screens found
-- stopped for few seconds --
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): server error.
any solution?
 I also restarted gnome, but it didn’t help.


I found this on a forum, but it doesn’t tell you how to configure the xorg. [URL="https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/267241"]

"You have 2 graphic cards and xorg doesn't know which one to choose as primary adapter. You need to define it in section "Device" of your xorg.conf config file with a line like: BusID "PCI:02:00:00"
This is the exact problem I am having, but I have no idea how to fix it! 

I am running a Toshiba satellite. Ubuntu 8.10, model #A355D-S6887
AMD64, ATI HD3400 with crossfire X.

---

