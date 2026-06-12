---
title: "Get wireless driver configuration to stick?"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by Craigular.B on 2009-03-19
I'm running 8.10 on my MacBook Pro 4,1, and I'm having wireless issues. I installed wicd because I had heard it might solve some random disconnects/reconnects I had, and it did. The problem is, now I have to go into the Hardware Driver menu, deactivate the Broadcom STA driver and then reactivate it for wicd to recognize the wireless. Otherwise, I can sit at the wicd window for however long I want and lick "Refresh" but it won't pick up the wireless.

Any suggestions? I put this here instead of the Apple forum because I think (I hope at least) it's more of a general issue and not specific to the MacBook Pro. I'll accept if it needs to be moved, though.

Thank you!
-Craig

---

### Post by pytheas22 on 2009-03-20
That's strange.  Could you please post a screenshot of your wicd Preferences window?  I'm thinking it may just be a matter of changing one of the values there.

---

### Post by Craigular.B on 2009-03-20
This is my preferences window AFTER I reload the Broadcom STA driver (I capped the wrong window before I loaded it). The thing is, the wired and wireless values are the same, and before I reload the driver the values are still correct.

The other thing is, if I ifconfig in the Terminal before I reload the driver, only eth0 (ethernet adapter) and lo come up. However, after I reload the driver and log out/in and ifconfig in the terminal, eth1 comes up (my wireless) along with the other 2 adapters.

-Craig

---

### Post by pytheas22 on 2009-03-20
wicd looks alright.  It sounds like the STA module is not being loaded by the system at all until you disable/enable it in Hardware Drivers.  If you type these commands, does wicd work:
```

sudo rmmod wl
sudo modprobe wl
sudo ifconfig eth1 up
```

Those commands should bring the interface up manually.  If they work, we can write a boot script that would run those commands automatically when you start your computer, which should solve the problem with wicd.

---

### Post by Craigular.B on 2009-03-20
Just tested the commands-thanks for the fast responses, btw!

So, ```
sudo rmmod wl
``` did not work when I tried it first. Said module wasn't there or something similar. However, when I tried ```
sudo modprobe wl
sudo ifconfig eth1 up
``` it brought the interface up and wicd started picking up wireless networks!

So now I just need to know how to write a boot script and I'll be all set! :D

Thanks!
-Craig

---

### Post by pytheas22 on 2009-03-20
Glad to hear that those commands brought up the interface as expected (the messaged about the module not being found on the first command is nothing to worry about).

To write a boot script so that they commands run automatically, first type:

```
sudo gedit /etc/init.d/wifi-fix.sh
```

A blank file will open.  Add these lines to it:
```

#!/bin/bash

modprobe wl
ifconfig eth1 up
```

Then save and close the file, and run these commands:
```

cd /etc/init.d
sudo chmod +x wifi-fix.sh
sudo update-rc.d wifi-fix.sh defaults
```

At this point, you should be all set--reboot your computer and wicd should work on its own.  If not, let me know.

---

### Post by Craigular.B on 2009-03-21
Thanks a lot pytheas! Everything's working from boot now. You rock!:guitar:

-Craig

---

