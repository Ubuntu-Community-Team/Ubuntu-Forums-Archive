---
title: "Disk checked every boot"
date: 2010-07-13
forum: Mythbuntu
---

### Post by itlarson on 2010-07-13
I am building a new mythbox for my parents.  It is a combined frontend/backend built on a dual core Ion motherboard with a 1g hard drive, and single usb tuner.  My problem is it wants to check the hard drive every time it boots. This takes quite a long time, and it refuses to let me abort the test.  Any ideas why it is doing this?  Which logs should I check?

---

### Post by libssd on 2010-07-13
Try this at the command line:

```
sudo tune2fs -c 51 /dev/sda1
```

The output should look something like this:

tune2fs 1.41.11 (14-Mar-2010)
Setting maximal mount count to 51

For more info: man tune2fs

---

### Post by LowSky on 2010-07-13
check that the time is set correctly in BIOS

---

### Post by itlarson on 2010-07-13
Thanks I'll try both those things.  I was a bit worried there might be something wrong with the drive.

---

