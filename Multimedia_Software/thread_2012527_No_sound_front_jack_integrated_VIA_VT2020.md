---
title: "No sound front jack integrated VIA VT2020"
date: 2012-06-29
forum: Multimedia Software
---

### Post by Mortesins93 on 2012-06-29
Hello,
I've installed Ubuntu 11.10 on a asrock 890gm pro3 motherboard and everything is working fine expect for the front audio jack. Its integrated audio chip is the VIA VT2020. The strange thing is that if I try a liveCD of the same ubuntu version (11.10 64bit) the front audio works fine, the only thing is that when I plug in the headphones the volume gets muted but, after unmuting it, it works. I checked the alsa version with the following command:
```
cat /proc/asound/version
```
and they both are the 1.0.24 version. Should I try reinstalling alsa? Could it be a kernel problem (I've update it a few times)?  Could the installation of audacity, avidemux or vlc caused problems? Should I try uninstalling them? I'd prefer not to reinstall the whole system.
Thanks in advance.

---

