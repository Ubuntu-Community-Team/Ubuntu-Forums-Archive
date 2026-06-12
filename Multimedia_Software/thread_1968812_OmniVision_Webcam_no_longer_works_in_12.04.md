---
title: "OmniVision Webcam no longer works in 12.04"
date: 2012-04-29
forum: Multimedia Software
---

### Post by Steve1961 on 2012-04-29
I have a Dell monitor with an integrated webcam.  It's always worked out of the box with Ubuntu.  That is, before 12.04.

lsusb output:

Bus 003 Device 004: ID 05a9:264a OmniVision Technologies, Inc.

Any ideas anyone?

---

### Post by sakovias on 2012-06-10
> **Steve1961 said:**
> I have a Dell monitor with an integrated webcam.  It's always worked out of the box with Ubuntu.  That is, before 12.04.

Same problem on Dell Inspiron 1420 under Ubuntu Lucid. My camera stopped working today after reboot :( Running lsusb gives

Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam

The video test in gstreamer-properties says "/dev/video0 does not exist".

What's going on?

---

### Post by sakovias on 2012-06-17
I don't know what happened, but the problem has disappeared by itself :).

---

### Post by LK_gandalf_ on 2012-07-28
not for me...same problem, it only works for a couple of minutes on skype, than the webcam shut down without hope.:(

---

### Post by LK_gandalf_ on 2012-09-27
any news on this problem? The webcam ocntinue to crash after 2-3 minutes on skype...

---

