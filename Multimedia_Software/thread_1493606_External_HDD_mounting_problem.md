---
title: "External HDD mounting problem"
date: 2010-05-26
forum: Multimedia Software
---

### Post by FA5878 on 2010-05-26
Hey guys, am hoping you can help me with this. I borrowed my mates HDD last week to back-up my data so I could do a clean install of Lucid Lynx (my upgrade from 9.10 didn't go quite as smooth as others).

While I writing data TO the HDD, a accidently kicked the USB cable out. I wasn't concerned at the time as its something that I have done thousands of times over the year.

However it seems to have done some damage, whenever I try to link it to the computer I get the following error message:

```
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdf1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details
```

Is there anyway of salvaging the data? If there is, how? I don't have a Windows machine and was wondering what the linux version of chkdsk is?

---

