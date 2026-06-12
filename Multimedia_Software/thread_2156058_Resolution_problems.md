---
title: "Resolution problems"
date: 2013-06-20
forum: Multimedia Software
---

### Post by thehim on 2013-06-20
Hi all, I'm having resolutions as per said.
My current build is AMD A4-3400 on Asrock Board, 8GB ram, 500GB HDD, using onboard Graphics connected to a Denon Receiver via HDMI, then to a Samsung LED TV.
On Lubuntu 12.10, using properiatary drivers for AMD instead of Xorg, as I don't know how to configure.

The ideal resolution for Denon Reciever is 1920 x 1080.
However whenever i select this resolution on AMD Catalyst Center, my panel is gone, 
My cursor can move beyond the screen, and goes 'missing' i.e. it's not the full desktop.

When i switch to 1600x900, everything becomes normal.
Is there a way to solve the resolution to be able to use 1920x1080?

Any advice is greatly appreciated. :)

---

### Post by TheFu on 2013-06-20
Simplify your setup and get it working.  Remove the receiver and plug directly into the TV and setup the resolution the TV supports.  After that works, then drop back to the receiver and try it with the same resolution.

Verify that the GPU HDMI version output matches what the TV supports and that the receiver does too. 1.2, 1.3, 1.4, 2.0 ... all are a little different.

Also, have you tried using a different display device?  Soemthings HDMI protocols are slightly different between different deivces and everything gets screwy.  I've had to reboot TVs to get the HDMI sync working again and I have a projector that seems to loose signal every 20 minutes regardless of the source or the cables used.

Oh - cheap HDMI cables are a known issue, especially if they are longer than 5 ft.  Only after reproducing the issue with different high-quality cables would I rule that out.

sorry, no real answer. Good luck!

---

### Post by TheFu on 2013-06-20
Oops. Looked like the posting failed.

---

