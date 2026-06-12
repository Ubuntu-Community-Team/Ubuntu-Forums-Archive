---
title: "using 12.04 lts, recent update to nvidia drivers causing problems"
date: 2013-10-18
forum: Mythbuntu
---

### Post by zapstrap on 2013-10-18
I've had this machine up and running for several years now. Every time I upgrade, something usually breaks; but, I'm used to that. This time I'm a little out of my depth. I've been using the nvidia proprietary driver (173) from the beginning, as it was the only game in town at that time. Recently it was recommended to upgrade to the open source 304 driver. This has not worked out for me. The display routinely freezes, and I have little option but to either hit the reset button, or log in remotely and force a reboot. This is really a bugger to deal with if say, I'm in the middle of updating the myth backend server settings, and the display freezes.

How do I go back to the 173 driver?

---

### Post by zapstrap on 2013-10-20
Anyone? The machine is now almost completely unuseable; as it won't run for long enough to use synaptic to reconfigure the machine. Should I post this in a different forum?

---

### Post by monkeybrain20122 on 2013-10-20
The 304 is proprietary as well. To go back just uninstall the 304 and reinstall 173 and reboot. Did you try that? (use synaptic, it is really easy)

---

### Post by zapstrap on 2013-10-20
The machine won't run long enough to get through reconfiguring with synaptic. The video freezes within the first 2 minutes.

---

### Post by zapstrap on 2013-10-20
K, got it to stay up long enough to remove 304. Much better, thanks!

One thing though: when I run the additional drivers utility, it shows nvidia_173 as active but not enabled. It showed 304 in the same state when it was installed. If I run the nvidia x server configuration tool, it showed 304 when it was there, but now shows 173. This is what I wanted, but just curious as to why Additional Drivers shows something that is not correct.

---

### Post by novellahub on 2013-10-21
Could it be the newer driver drops support for your model of Nvidia card?

---

