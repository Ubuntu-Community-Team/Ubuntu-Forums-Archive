---
title: "em28xx problems"
date: 2008-07-01
forum: Multimedia Software
---

### Post by ar0n on 2008-07-01
Hi!

I have a problem with this driver... I've never used v4l so i don't really understand it.
I want to use a USB 2.0 AV Grabber called GrabBeeX+

It has an s-video, stereo and a composite video input.
The sound and video are attached trough a saa7113h and EMP202 AC97 chip.
The USB is attached to the em2800-2 chip.

I tried to load the module, after that I tried to compile it, but i still get the same effect.

It does not create a video device file :(.

```

Linux video capture interface: v2.00
em28xx v4l2 driver version 0.0.1 loaded
usbcore: registered new interface driver em28xx
ACPI: EC: non-query interrupt received, switching to interrupt mode
usb 5-5: new high speed USB device using ehci_hcd and address 4
usb 5-5: configuration #1 chosen from 1 choice
usbcore: registered new interface driver snd-usb-audio

```

If you can please help me !

Thanks!

---

### Post by heffo_j on 2008-07-01
Hi there,

Can't really help you. 

Just leeting you know I posted yesterday about not being able to get the same chipset working in my UTV3 TV box.

V4Linux site suggests that the chip should work. I can;t find anywhere that has a step by step how to on getting these things going; I'm guessing that there is so many alternatives out there that it is difficult to do so.

Best of luck and I'll watch this thread to see if someone comes up with some answers.

Regards
John

---

### Post by ar0n on 2008-07-02
Hi!

got it to work... I modified the source and added my usb id and device.
So it works now ... If you need one I can create a patch so you can test it.

All I need is an lsusb and the chip names on your board and the exact model of your capture device.

;)

Aron

---

