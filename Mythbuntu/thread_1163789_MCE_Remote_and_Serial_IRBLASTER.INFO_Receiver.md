---
title: "MCE Remote and Serial IRBLASTER.INFO Receiver"
date: 2009-05-19
forum: Mythbuntu
---

### Post by prof3205 on 2009-05-19
I'm sure this has been asked a 1000 times already, but if you could bear with my and help just one more time it would be greatly appreciated.

I've just installed the new 9.04 release and ran all of the updates and, so far everything seems to work all right.  Here's my hardware:

Intel MB with Celeron 2.0GHz
512MB Memory
200GB HDD
nVidia GeForce 6600 with VGA and S-Video
Hauppauge PVR-150
MCE Version 2 Remote (that came with the PVR-150)
IRBLASTER.INFO RS-232 IR Blaster (I didn't get the IR Receiver that came with the PVR-150)

So, my questions are:

1. Will the remote work with this combination of HW (I wasn't sure if I should have purchased the RS232 IR Receiver instead of the IR Blaster)?

2. If so, where do I go from here?  I'm seeing a bunch of posts about downloading, compiling and configuring LIRC, or getting the KnoppMyth scripts, etc.  But I'm not using a external cable tuner box so I'm not sure about which are the right instructions.

3. Would a Universal Remote be better?  (I have a couple of them as well)

Any help would be greatly appreciated.

---

### Post by phroman on 2009-05-19
Well, you're definitely going to need an IR Receiver, to receive the IR signal your remote sends out.  The blaster is generally used to send IR signals/commands to other devices, like cable/satellite receivers, and control them from your myth box.  Lirc is installed in 9.04 by default.  If you can get a supported IR Receiver, your remote "should" work once you set it up in Myth Control Center.  (MCC)

---

### Post by prof3205 on 2009-05-21
That was the problem.  I got a USB IR Remote (from an old Gateway Computer that a friend loaned me) and viola, it WORKS!!!

I just ordered a similar part from eBay for about $20 and we'll see it that works as well.

Thank you all!

---

