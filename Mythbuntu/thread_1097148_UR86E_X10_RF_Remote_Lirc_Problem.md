---
title: "UR86E X10 RF Remote Lirc Problem"
date: 2009-03-15
forum: Mythbuntu
---

### Post by tobiz on 2009-03-15
I've been tryng to get a UR86E X10 RF remote to work with Mythbuntu 8.10 with minor success.  The remote looks like the ATI/Nvidia Wonder, ie shape and number of buttons etc. I've tried to configure this with Myth Control Centre as an ATI/Nvidia X10 RF remote.  If I run mode2 --device=/dev/lirc0 --raw the key presses are returned.  mode2 will not run without the --raw option, ie if omitted it says --raw has to be used.  Irrecord runs and the key-codes can be captured, they look similar to that reported by others for the UR86E.  However, if I run irw and press any keys I get nothing, there doesn't seem to be a way of running irw with options similar to mode2 nor any way of setting such an option in any config file.  Any ideas how to get this remote working with Mythbuntu would be very welcome.

---

