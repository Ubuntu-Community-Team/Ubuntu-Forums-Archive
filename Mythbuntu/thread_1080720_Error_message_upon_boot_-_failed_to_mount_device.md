---
title: "Error message upon boot - failed to mount device"
date: 2009-02-25
forum: Mythbuntu
---

### Post by bag123 on 2009-02-25
All,

Another issue.  When my box boots up, it gets into the front-end and then posts up an error message that states:
```

Failed to mount device: /dev/sde
Showing the default MythGallery Directory
```

I don't know what /dev/sde is.  Honestly, I don't.  How do I find out?  That might help me understand whether I need it mounting...

The error is very repeatable - it pops up every time without fail.

Please help me to fix it either by:

1. Pointing me in the right direction to find out what /dev/sde is and helping me to mount it at boot time

or

2.  Bypassing the problem by telling it to not try mounting the device.

Your help in trying to help me learn either method would be very much appreciated.

Many many thanks in advance.

Bag123.

****************

Other info:

Using 8.10
Normal default install - not a custom setup.
I've checked both mtab and fstab - neither mention a /dev/sde
Box has slots for CF/SD cards etc.  Could that be the device it's looking for?

---

### Post by ajgreeny on 2009-02-25
> Box has slots for CF/SD cards etc.  Could that be the device it's looking for?Yes, I suspect that is the reason.  It could be worth looking in your System > Preferences > Sessions to see if you have it set to always remember and load the last session, including running applications.

---

