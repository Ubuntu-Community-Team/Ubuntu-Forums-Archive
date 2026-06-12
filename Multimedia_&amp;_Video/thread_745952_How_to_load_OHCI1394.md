---
title: "How to load OHCI1394"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by Aztek on 2008-04-05
I have a Canon ZR830 that I'm trying to connect via a new Rosewill Firewire PCI card. The card uses the NEC uPD72874, which linux1394.org says is supported via the OHCI1394 driver. which is supposedly included in the kernel already. I'm wondering how I can load this driver and get this thing to work. In Kino under IEEE 1394 it says, "The IEEE 1394 Subsystem is not responding" and "The raw1394 module must be loaded, and you must have read and write access to /dev/raw1394"

Help please?

---

### Post by Aztek on 2008-04-05
bump

---

### Post by Aztek on 2008-04-12
Well I've been doing some reading and it appears that what I need to do is get the raw1394 driver up and running. Can someone point me to a how-to or something for loading drivers?

---

### Post by xc3RnbFO8P on 2008-04-12
Try this:
[http://ubuntuforums.org/showpost.php?p=4649034&postcount=4]("http://ubuntuforums.org/showpost.php?p=4649034&postcount=4")

---

