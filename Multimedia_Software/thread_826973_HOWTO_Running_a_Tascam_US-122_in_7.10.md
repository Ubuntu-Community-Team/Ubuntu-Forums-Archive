---
title: "HOWTO: Running a Tascam US-122 in 7.10"
date: 2008-06-12
forum: Multimedia Software
---

### Post by pneaveill on 2008-06-12
[http://ubuntuforums.org/showthread.php?t=194490](http://ubuntuforums.org/showthread.php?t=194490) reveals my problem, but I am not sure how to proceed from here.


> niceguy@niceguy:~/Desktop/usx2y# make
as31 ld2-ezusb.asm
including file: an2131.asm
Begin Pass #1
Begin Pass #2
niceguy@niceguy:~/Desktop/usx2y#


> lsusb
Bus 002 Device 002: ID 8086:1120 Intel Corp.
Bus 002 Device 003: ID 0644:800e TEAC Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 001: ID 0000:0000

> niceguy@niceguy:~/Desktop/usx2y# sudo fxload -s /home/niceguy/Desktop/usx2y/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/002/003
can't modify CPUCS: Broken pipe

I know that the broken pipe thing there is the ~/002/003 that is somehow not being written to and I cannot figure out why. Hoping for some assistance on this.
anyone with ideas?  Please?!

---

### Post by K.Mandla on 2008-06-15
Moved to Multimedia and Video.

---

### Post by pneaveill on 2008-07-04
Where is the move?  I am still needing help on this, but cannot find where you moved it to.

---

