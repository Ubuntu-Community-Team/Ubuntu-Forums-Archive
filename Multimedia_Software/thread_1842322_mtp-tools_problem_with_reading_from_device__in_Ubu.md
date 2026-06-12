---
title: "mtp-tools: problem with reading from device  in Ubuntu 11.04"
date: 2011-09-11
forum: Multimedia Software
---

### Post by teg85 on 2011-09-11
Hello,

When I plug in my Sony NWZ-S516, Ubuntu 11.04 properly detects a new device and a new window with its files pops up. I can copy files to and from the device without any problems.
To create a playlist I tried to use mpt-tools. Unfortunately, it didn't work.
I got the following message:
```

Attempting to connect device(s)
 Device 0 (VID=054c and PID=0326) is a Sony Walkman NWZ-S516.
 LIBMTP PANIC: Unable to read device information on device 15 on bus 1,  trying to continuemtp-folders: There has been an error connecting. Exit

```Strace log contains lots of EAGAIN (Resource temporarily unavailable) errors.
Could anyone help me?

---

