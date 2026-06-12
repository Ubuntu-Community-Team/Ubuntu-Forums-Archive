---
title: "Cannot connect Sansa e280 in Juanty"
date: 2009-05-21
forum: Multimedia Software
---

### Post by RingoNZ on 2009-05-21
It was working fine in previous versions with Amarok 1, but in Ubuntu Jaunty with Amarok 2 I cannot connect to it even as a USB device. I get the following error from mtp-detect:

libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   SanDisk: Sansa e280 (0781:7421) @ bus 0, dev 7
Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
Unable to open raw device 0
OK.

My Sansa e280 is running Rockbox, but in MTP mode it boots into the default Sansa firmware. I have tried MSC mode and that does nothing. I don't think it ever worked in previous versions of Ubuntu either.

---

