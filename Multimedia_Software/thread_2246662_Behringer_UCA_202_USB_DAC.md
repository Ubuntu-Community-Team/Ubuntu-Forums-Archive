---
title: "Behringer UCA 202 USB DAC"
date: 2014-10-02
forum: Multimedia Software
---

### Post by bigalxyz123 on 2014-10-02
Hello forum,

Just installed Lubuntu on an old Sony Vaio laptop, previously running Windows 8 (with some difficulty).

I have a Behringer UCA 202 USB DAC plugged into a USB port, and it worked straight out of the box with Windows, but with Lubuntu, nothing.

The sound instead comes out of the laptop's internal speakers, but with lots of clicking and popping.

Can anyone advise what might be wrong & what I might need to do to fix it please?

Many thanks,
Alan.

---

### Post by Rob Sayer on 2014-10-04
Have you tried searching something like "ubuntu behringer uca202"?  You'll get a bunch of links re ubuntu studio, which involves using jack and probably isn't relevant.  But there seems to be some stuff like:

[http://jamie.lentin.co.uk/peripherals/behringer-uca-222/](http://jamie.lentin.co.uk/peripherals/behringer-uca-222/)

which indicates that using alsa instead of pulse would work better.  I try to avoid pulse audio anyway.  I don't see the point.

Unfortunately I find audio in linux really not very straightforward.  Good luck.

---

### Post by Rob Sayer on 2014-10-08
You may also want to check what output module your media programs are using.

---

