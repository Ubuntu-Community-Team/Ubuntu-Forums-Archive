---
title: "Mac will not boot"
date: 2007-10-15
forum: Mac OSX
---

### Post by k1001001 on 2007-10-15
Hey guys. No matter how hard I try, I cannot get my girlfriend's iBook G4 to boot and I am stumped as to why it won't. It just sits at the white screen with an Apple and a spinning wheel. So far I have tried to zap the PRAM, boot into single-user (terminal) mode, boot into safe mode, and I have even booted from the install disk and run the Disk Utility check. There were errors on the disk, but even after the Disk Utility fixed them, the computer still won't boot.

Here's some of the output when I boot into single-user mode:
```
using 1310 buffer headers and 1310 cluster IO buffer headers
Extension "com.apple.driver.KeyLargoATA" has no kernel dependency
CSRHIDTransitionDriver::probe booting into single user .. do not match
FireWire (OHCI) Apple ID 31 built-in active, GUID 001451ff fe99b126
ADB present:84
Security auditing service present
BSM auditing present
disabled
rooting via boot-uuid from /chosen: (big number)
Waiting on (big string ID line)
Got boot device = IOService: (big Hard drive gobly-gook)
BSD root: disk0s3, major 14, minor 2
```

It hangs at this point and gives no prompt. It seems like the computer is pretty much locked from booting.

If anyone has any clues as to what I can do to save this computer, let me know.

---

### Post by hellion0 on 2007-10-15
Try running Disk Utility a second time. If it's still got errors, the HDD is trash. That's all I can think of.

---

### Post by k1001001 on 2007-10-16
I tried using the Disk Repair on Disk Utility again, and still no luck. I started the computer in verbose mode, and it looks like the above text, but with this at the end:
```
CSRHIDTransitionDriver::stop
IOBluetoothHCIController::start Idle Timer Stopped
```

Any other hints as to what could be wrong? Is this hard drive done for?

---

### Post by k1001001 on 2007-10-17
UPDATE: The solution to this problem was to use the restore disks and to do an 'Archive and Install.' This saves your old files and re-installs OSX. I should have done this in the first place. [Here is how to do an Archive and Install.]("http://docs.info.apple.com/article.html?artnum=107120")

---

