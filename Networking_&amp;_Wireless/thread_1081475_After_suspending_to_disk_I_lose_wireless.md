---
title: "After suspending to disk I lose wireless?"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by semitone36 on 2009-02-26
Yup.  

Basically, when I bring my laptop out of sleep mode it isnt able to find any wireless networks, even if it was connected to one when I put it to sleep.

Not really sure where to start trouble shooting on this one.  Its not that big of a deal but it would be nice if I could just put my computer to sleep when moving between classes instead of having to constantly shut down and reboot.

Any ideas?

---

### Post by smani on 2009-02-26
Which wlan card does your laptop have? The drivers for some cards are not (yet) able to correctly put the device in to sleep and to make it wake up again after resume. The solution in that case is to unload the module (driver) from the kernel as the laptop suspends, and then reinsert it on resume. This can be done by adding
SUSPEND_MODULES="module_name"
to
/etc/pm/config.d/modules (create file if necessary).
To find out what module your card is using, try looking at the output of
```
sudo lshw
```.

---

