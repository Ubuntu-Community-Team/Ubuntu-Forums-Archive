---
title: "LIRC only works sometimes"
date: 2007-11-20
forum: Mythbuntu
---

### Post by Beakster on 2007-11-20
Hi,

Sometimes my LIRC doesn't work.  I have found out why, but I don't know how to fix it.

It is because the event is seems to be assigned a event number randomly.  Sometimes when I boot I get:

/dev/input/by-path/pci-0000:00:0d.0--event-

and sometimes when I reboot I get:

/dev/input/by-path/pci-0000:00:0d.2--event-

Note the difference between the 0 and 2 at the end.

Is there someway I can always force it to be the same?

Thanks
-Chris

---

### Post by Beakster on 2007-11-20
Forgot to mention, the IR receiver is attached to my Leaktek Winfast DTV1000T DVB Card.

---

### Post by roseway on 2007-11-20
You can adapt the procedure described at [http://ubuntuforums.org/showthread.php?t=183545&highlight=nova](http://ubuntuforums.org/showthread.php?t=183545&highlight=nova) which is for the Nova-T 500 RC but I'm sure will apply equally to any RC which uses /dev/input.

---

### Post by Beakster on 2007-11-20
Thanks, that worked perfectly! :)

---

### Post by roseway on 2007-11-20
You're welcome. :)

---

