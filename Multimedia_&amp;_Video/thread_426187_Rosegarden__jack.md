---
title: "Rosegarden / jack"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by pkslot on 2007-04-28
When i start up Rosegarden, this message pops up:

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

I've installed JACK and its running fine. Before i start rosegarden, i start Jack, so it's allready running.

Any one who knows the how to deal with this problem?

---

### Post by luctor on 2007-04-28
You need the low-latency kernel.
The system timer is in the kernel (as far as i know ..) and has nothing to do with jackd (as far as i know :) )

[http://packages.ubuntu.com/feisty/admin/linux-lowlatency](http://packages.ubuntu.com/feisty/admin/linux-lowlatency)

Rob

---

### Post by pkslot on 2007-04-29
Thanks, but if i install this low-latency kernel, what will happen then? What am i mingeling with?

---

### Post by luctor on 2007-04-30
If you for some reason don't like this kernel, you can always boot to the generic kernel. When the lowlatency kernel is installed the 'old' kernel isn't removed

I haven't really noticed much differences with the low-latency kernel. Off course the alsa/jackd stuff works better, less Xruns etc. But all other stuff seems to work as normal .

---

### Post by pkslot on 2007-04-30
Ok, great, sounds like no problem.

But what about other stuff, like installed drivers for nvidia?

---

### Post by deadgobby on 2007-04-30
I have low installed and see no difference.  It runs fine and has not crashed on me yet.

---

### Post by dvs9000 on 2007-05-05
> **luctor said:**
> You need the low-latency kernel.
The system timer is in the kernel (as far as i know ..) and has nothing to do with jackd (as far as i know :) )

[http://packages.ubuntu.com/feisty/admin/linux-lowlatency](http://packages.ubuntu.com/feisty/admin/linux-lowlatency)

Rob

Hi,
I there a pakage for edgy too?
I've been browsing around for but haven't found it yet.
grtz
a linux newbie

---

