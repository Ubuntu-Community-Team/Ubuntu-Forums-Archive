---
title: "ath5k: wifi disassociate and stop working casually"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by asbesto on 2010-02-25
Hi, from about 4 days I have this very weird problem on my eeepc 701

My wifi card disassociates from the AP and there's no way to re-associate.

I had to manually disable the card and re-enable again via the eeepc tray.

This happens many times in a day ](*,) , it's totally casual, and started to happen about 4 days ago. Before that, I always had a rock-solid connection!

here's what I obtain in logfiles:

```

[70693.324675] ath5k phy1: noise floor calibration timeout (2432MHz)
[70704.324622] ath5k phy1: noise floor calibration timeout (2432MHz)
[70712.585871] ath5k phy1: failed to wakeup the MAC Chip
[70712.585885] ath5k phy1: can't reset hardware (-5)
[70712.633442] ath5k phy1: failed to wakeup the MAC Chip
[70712.633457] ath5k phy1: can't reset hardware (-5)
[70712.693904] ath5k phy1: failed to wakeup the MAC Chip
[70712.693919] ath5k phy1: can't reset hardware (-5)
[70712.740309] ath5k phy1: failed to wakeup the MAC Chip
[70712.740325] ath5k phy1: can't reset hardware (-5)
[70712.799276] ath5k phy1: failed to wakeup the MAC Chip
[70726.324600] __ratelimit: 20 callbacks suppressed

```

This seem the well known (and UNSOLVED!! #-o) bug: [http://bugzilla.kernel.org/show_bug.cgi?id=14561]("http://bugzilla.kernel.org/show_bug.cgi?id=14561") ... the only difference is that I don' need to reboot the 701.

I don't understand why this bug appeared to me only 4 days ago. The bug is present since 2009! :confused:

Any idea about this? Please help me, this is really disturbing!

---

### Post by asbesto on 2010-02-27
BUMP? Possible that in all the forum there's no one that can help in this issue? :???:

---

### Post by asbesto on 2010-03-10
This forum is really becoming useless. I think I need to move to debian ASAP. :(

---

### Post by webaake on 2011-01-01
This script solved it for me on my acer aspire One 110 with ath5k chip:
```
#!/bin/sh

#stop everything using the ath5k module
/etc/init.d/networking stop
/etc/init.d/wicd stop
#remove the module
modprobe -r -f ath5k

#add it back
modprobe ath5k

#start everything back up
/etc/init.d/networking start
/etc/init.d/wicd start
```

I'm using wicd instead of network-manager which I strongly recommend. You probably can replace ath5k with your chip. Thanks to the original scripter on this forum, which I can't find right now.

---

