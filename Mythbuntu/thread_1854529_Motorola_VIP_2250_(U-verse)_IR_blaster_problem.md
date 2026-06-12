---
title: "Motorola VIP 2250 (U-verse) IR blaster problem"
date: 2011-10-04
forum: Mythbuntu
---

### Post by clmbngbkng on 2011-10-04
Hi all,

I've been running Mythtv with U-verse for a while with a Motorola VIP 1216
but it ended up making a high pitch noise so that was replaced with a
Motorola VIP 2250.

The VIP 1216 worked just fine with the blaster and as the VIP 2250 uses the
same remote I should just need to move my IR blaster to the new box, right?
Wrong.

I've tried irw to see if my settings are still reading correctly and on
screen it is reporting the correct button presses as well as checked out the
LIRC site to see if there was anything specific for the VIP 2250 and there
was nothing.


I'm currently running 0.24.1+fixes on Ubuntu 10.04, any suggestions?

Thanks!

---

### Post by clmbngbkng on 2011-10-05
BUMP

Will take all the help I can get.

---

### Post by azmyth on 2011-10-06
I would try adding a frequency to your lirc file. Usually put the statement after the toggle_bit_mask like below.

frequency    56400

---

