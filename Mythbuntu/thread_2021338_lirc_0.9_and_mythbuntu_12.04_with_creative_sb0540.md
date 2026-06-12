---
title: "lirc 0.9 and mythbuntu 12.04 with creative sb0540"
date: 2012-07-09
forum: Mythbuntu
---

### Post by Totzo on 2012-07-09
Hi all,

I just updated my mythbox from 11.04 to 12.04 and had an issue with my creative sb0540 usb ir remote. It's fixed now and I thought I'd post here in case anyone else is tearing out clumps of hair!

Basically from what I can figure out the lircd was trying to load a kernel module which didn't exist and failing to launch as a result.

I changed LOAD_MODULES="true" to LOAD_MODULES="false" in /etc/lirc/hardware.conf

Secondly I had to change where mythtv frontend looks for the lircd socket from  /dev/lircd to /var/run/lirc/lircd (this was changed in lirc 8.6 and newer apparently)

Hope this helps someone :)

---

