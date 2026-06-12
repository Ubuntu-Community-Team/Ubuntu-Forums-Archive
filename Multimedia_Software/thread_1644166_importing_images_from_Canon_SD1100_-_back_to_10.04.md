---
title: "importing images from Canon SD1100 - back to 10.04"
date: 2010-12-12
forum: Multimedia Software
---

### Post by serrs on 2010-12-12
This camera (Canon SD1100) does not look like a USB hard drive, which is fine as long as your importing works.  Remembering that F-Spot had treated me well, I plugged in my wife's Canon into my Ubuntu 10.10 laptop (and then workstation).  Shotwell, has NO knowledge that it should be importing .avi files.

No worries, Nautilus has some kind of helper to treat it like a filesystem.  So I start copying ALL the files off, even the large AVI files.  It turns out that Nautilus or helper either have a memory leak OR they copy whole files into memory before writing to disk.  Either way I got OOM Killer... The gvfs process was 2.3GB when killed.

I then tried F-Spot, but since F-Spot is not supported on 10.10 it appears that not much work has gone into configuring it.  Less polish and doesn't see .avi files.

After the better part of a day...  I installed **10.04** into VMware Workstation and used the **old F-Spot**.

This regression is very sad.  I'd be happy to try recommendations.

---

