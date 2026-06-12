---
title: "IR Blaster help"
date: 2008-01-07
forum: Mythbuntu
---

### Post by murchball on 2008-01-07
I'm reinstalling Mythbuntu on my backend and I'm having trouble setting up my serial IR Blaster (from irblaster.info) on my cable box (SA3250HD). The frustrating thing is that I had this working correctly on my previous install. I see the blaster flash when I try to change channels (either through Myth or with irsend) which leads me to believe that I either have incorrect info in lircd.conf or incorrect placement of the blaster, but I haven't moved the blaster and I'm using the same lircd.conf that worked in my previous install (the AT8400 from lirc.sourceforge.net) Does anyone have any other ideas that I can try?

Thanks!

---

### Post by spiregrain on 2008-03-29
I found I could get it to work by adding the softcarrier argument to /etc/modprobe.conf/lirc-serial, like this:

```
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8 softcarrier=1
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8

```

---

