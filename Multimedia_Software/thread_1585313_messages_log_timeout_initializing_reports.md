---
title: "messages log: timeout initializing reports"
date: 2010-09-30
forum: Multimedia Software
---

### Post by erikh1216 on 2010-09-30
Hello everyone,

I have the following message being logged in my /var/log/messages log regarding a HID device. This seems to be an error message, but I cannot tell for sure whether or not this is a bad thing, what is causing it, and if it is bad how to fix it:

```
Sep 30 09:54:16 erikh kernel: [   19.429691] quanta-touch 0003:0408:3001.0002: timeout initializing reports
```This message is being logged right before the message that indicates that the kernel is using my device:

```
Sep 30 09:54:16 erikh kernel: [   19.430034] quanta-touch 0003:0408:3001.0002: hiddev96,hidraw3: USB HID v1.10 Device [QUANTA Optical Touch Screen] on usb-0000:00:1d.0-2/input0
```and I fear that this timeout is causing my device to not work properly (I have to log out before the device starts working). Does anyone know what could cause this "timeout initializing reports" and how to fix it?

Thanks in advance for your help!

---

