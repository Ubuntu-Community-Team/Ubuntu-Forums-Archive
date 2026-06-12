---
title: "MTP Mode - Sony Walkman &amp; Lucid"
date: 2011-09-17
forum: Multimedia Software
---

### Post by mahavishnu on 2011-09-17
I'm trying to mount my Portable Audio Device (Sony Walkman E345) in MTP mode, in order to scrobble my tracks to lastfm.

Don't know what I'm doing wrong.
I have installed all mtp package from synaptic.

Her's the mtp-detect result:



> sudo mtp-detect 
libmtp version: 1.0.2

Listing raw device(s)
Device 0 (VID=054c and PID=03fc) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
   Found 1 device(s):
   054c:03fc @ bus 1, dev 5
Attempting to connect device(s)
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Device or resource busy
outep: usb_get_endpoint_status(): Device or resource busy
usb_clear_halt() on IN endpoint: Device or resource busy
usb_clear_halt() on OUT endpoint: Device or resource busy
usb_clear_halt() on INTERRUPT endpoint: Device or resource busy
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
Unable to open raw device 0
OK.
ubuntu@ubuntu-desktop:~$ 


---

