---
title: "How to force Sansa Express to MTP mode?"
date: 2009-01-23
forum: Multimedia Software
---

### Post by askvictor on 2009-01-23
I have a Sansa Express media player. When plugged in it tries to connect as an MTP device, but if that fails, it falls back to a UMS/MSC device. The problem is that music transferred by MSC doesn't come up in the correct order on the player - it seems it's designed mainly for MTP. When plugged into ubuntu it comes up as a disk. If I try to configure it as a MTP device in amarok, amarok sometimes picks it up, then drops it again, and other times it crashes. If I run mtp-detect it finds the device and prints a lot of info, ending in:
```
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_Filelisting_With_Callback(): call to ptp_mtp_getobjectpropssupported() failed.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: LIBMTP_Get_File_To_File_Descriptor(): Could not get file from device.
Error 2: (Look this up in ptp.h for an explanation.)
PTP: Closing session
ERROR: Could not close session!
OK.

```

I'm using 8.04
I think the same problem is described in: [http://ubuntuforums.org/showthread.php?t=710074](http://ubuntuforums.org/showthread.php?t=710074)

Any thoughts? Can I disable ubuntu (via udev or HAL or something) from loading the device as a MSC device?

---

