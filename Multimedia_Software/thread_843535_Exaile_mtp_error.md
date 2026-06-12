---
title: "Exaile mtp error"
date: 2008-06-28
forum: Multimedia Software
---

### Post by Blind Tiger on 2008-06-28
I'm trying to get my Sansa Clip to work via mtp with Exaile 0.2.13.  I have installed all the current libraries.  When I run Exaile from the terminal,  I get the following output:

> usb_claim_interface(): Bad file descriptor
LIBMTP PANIC: Could not open session on device 1
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1599
LIBMTP_Get_First_Device: Error Connecting
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
Clearing stall on IN endpoint
Exception in thread Thread-15:
Traceback (most recent call last):
  File "threading.py", line 460, in __bootstrap
    self.run()
  File "threading.py", line 440, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/home/lance/.exaile/plugins/mtpdevice.py", line 109, in connect
    if self.connecting: self.disconnect()
  File "/home/lance/.exaile/plugins/mtpdevice.py", line 211, in disconnect
    self.mtp.disconnect()
  File "/usr/lib/python2.5/site-packages/pymtp.py", line 448, in disconnect
    raise NotConnected
NotConnected


Does anyone have a solution to this error?

---

