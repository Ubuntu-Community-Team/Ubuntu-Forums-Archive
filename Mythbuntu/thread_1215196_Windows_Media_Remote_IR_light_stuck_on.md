---
title: "Windows Media Remote IR light stuck on"
date: 2009-07-16
forum: Mythbuntu
---

### Post by tshannon on 2009-07-16
I recently hooked up a windows media center usb remote to my mythbox, and loved how easy it was to configure and get up and running with Mythbuntu, but every now and then when the machine is rebooted the red ir transmitter light is stuck on, and the remote doesn't work.

I've restarted lirc but the light stays on.  The only way I can get it to turn off and act normally is by rebooting the machine, and sometimes that doesn't work.  It may take multiple reboots to get it to work correctly.

Unplugging the receiver and plugging it back in doesn't fix it, although it does turn the light off.

---

### Post by azmyth on 2009-07-16
Does this happen when the remote is idle for a few days or does it happen while in use? I'm using a different device but if it's idle for four days it hangs and it's nasty to get back (takes a few reboots, moving ports). In the end, I added the user to visudo for reboot and then have a cron reboot every three days at 5AM.

---

### Post by tshannon on 2009-07-19
Nope, it only seems to hang when the machine is rebooted, and only sometimes.

---

### Post by pfk001 on 2009-07-19
I had the same issue.  Finally figured out that during the boot process LIRC was receiving a signal and locking it up.  My tv and receiver were putting out an IR signal that it was picking up.  To prevent LIRC locking up I wait until the computer has booted before I turn on the tv and receiver.

---

### Post by tshannon on 2009-07-21
You're right.  As long as my TV is off when I startup my mythbox, it works fine.

Thanks for the tip.  Is there any way to cycle? the usb device after boot so I don't have to reboot if it gets stuck again?

---

