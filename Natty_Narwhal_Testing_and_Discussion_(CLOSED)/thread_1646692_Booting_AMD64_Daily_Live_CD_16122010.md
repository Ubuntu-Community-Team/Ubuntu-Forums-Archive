---
title: "Booting AMD64 Daily Live CD 16/12/2010"
date: 2010-12-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nperry on 2010-12-16
Unable to boot this CD. 

Checked MD5sum on image, re-done image twice and re-downloaded.

Getting this error message at plymouth boot - 

> FATAL: Error inserting crc32c_intel (lib/modules/2.6.37-9-generic/kernel/arch/x86/cryto/crc32c-intel.ko) No Such device

stdin: error 0

I have attached image, any ideas?

Neil

---

### Post by lachild on 2011-02-10
I am getting this problem on Alpha 2 as well.  Where you ever able to get his problem resolved?

---

### Post by go7Ul1ai on 2011-02-10
I tried the daily today for amd64 and it booted and installed fine, the only issue was with this image were the icon sets installed (no Humanity, mono-dark etc) so I downloaded Alpha 2 and works perfectly.

---

### Post by lachild on 2011-02-10
Nope tried the daily image and I get the same error above.  After 10 minutes of hanging then the screen starts scrolling a bunch of garbage down the screen followed but the error above then the system locks up completely.

Is there a way to manually add the module...  through using a driver disk or adding it to the flash drive?  Would that work?

---

### Post by Optln on 2011-02-10
I'm using 2.6.37 kernel from ppa on Maverick and having this problem as well. So it's probably a kernel issue.

---

### Post by lachild on 2011-02-11
Does anyone know if a bug report has already been filed on this?   If not I can create one.


Thanks

---

### Post by lachild on 2011-02-11
NM I found it

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/690606 ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/690606")

---

