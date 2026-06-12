---
title: "Handycam driver for USB stream?"
date: 2009-02-28
forum: Multimedia Software
---

### Post by reader4 on 2009-02-28
I have a Handycam DCR-HC40 that allows the output to be streamed through a USB port and used as a webcam.  In Windows, this worked well with the Sony-provided driver and Skype.  In Linux, it appears that there may not be driver support for this feature... the camera is ID'd on the USB bus:

$ lsusb
Bus 001 Device 010: ID 054c:00c0 Sony Corp. Handycam DCR-30

but is not mounted anywhere, and does not have a /dev/... entry (that I can find).  Is there any way to mount this to /dev/video0 and use it as a webcam?  Not UVC, that I am aware (but maybe someone else knows differently).  Lots of unresolved questions about this on the internet.

---

### Post by 7.11brown on 2009-07-04
I'll make you feel better about this, I have a dcr-hc48, and same USB mode, and would like the webcam to work.  There is a way to use the firewire, but I have not gotten that to work, and have a functioning video

I have not yet found a solution for the USB webcam feature

---

### Post by deanerk on 2009-07-14
Came here looking for an answer to this as well.  I have a Handycam DCR-SR200.  Haven't had any luck getting it to stream and use as a webcam.  Just picked up a Logitech QuickCam Pro 9000 that I'm gonna try tonight, but would love to return it for my $100 if I could get the Handycam working...

---

### Post by deanerk on 2009-07-15
The Logitech Quickcam worked great with Skype right out of the box last night, BTW.

---

