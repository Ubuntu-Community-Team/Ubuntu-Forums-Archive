---
title: "mythbuntu loses sound on second tuner"
date: 2011-11-08
forum: Mythbuntu
---

### Post by bleve on 2011-11-08
I have 11.04 using two PVR-350 cards.  This did not work with mythbuntu 10 either so I hope it is just a configuration issue.  If both tuner cards are recording a show the sound stops working on card 2.  It records sound on both for about a minute or two but eventually the sound just cuts off on card 2.  I have 3 found ends and if I start live TV on one then go to another and start live TV the sound does the same thing.  It works for a minute or two but then I lose sound on the one using the second tuner.  

I have checked the mythbackend log on the backend and besides this message when the recording first starts, there are no other errors at the time:

> 2011-10-09 21:00:04.842 MPEGRec(/dev/video1) Warning: Audio sample rate 32000 Hz
                        is not supported by ivtv driver, using 48000 Hz instead.
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not
 properly capture VBI data on PVR-250 and PVR-350 cards.I see this message from both tuner cards.  

Thanks

---

### Post by bleve on 2011-11-09
I reproduced this with livetv and see the following in the syslog:

> Nov  9 19:50:24 myth01 kernel: [1206634.312015] ivtv1: Audio has died (Encoder OK) : ivtv_serialized_open
Nov  9 19:50:24 myth01 kernel: [1206634.312078] ivtv1: Detected in ivtv_serialized_open that firmware had failed - Reloading
Nov  9 19:50:25 myth01 kernel: [1206635.153363] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Nov  9 19:50:25 myth01 kernel: [1206635.254328] ivtv1: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
Nov  9 19:50:26 myth01 kernel: [1206635.518085] ivtv1: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
Nov  9 19:50:26 myth01 kernel: [1206635.632719] ivtv1: Firmware restart okay

Still investigating.   Let me know if you have seen this before.

---

### Post by bleve on 2011-11-09
Looks like it may be hardware related from what I have been reading.  I will try pulling the cards and changing order and such and see if that helps.

---

### Post by bleve on 2011-11-09
Well one of my cards is toast.  Any recommendations on a replacement.  It is going into a Pentium4, hence why I was using a card with the mpeg encoder on it.  

Thanks

---

