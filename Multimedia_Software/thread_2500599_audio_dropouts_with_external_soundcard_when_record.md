---
title: "audio dropouts with external soundcard when recording screen with OBS"
date: 2024-09-06
forum: Multimedia Software
---

### Post by greensoma on 2024-09-06
Hi there,

I am having audio dropouts sometimes when recording screenrecordings with OBS-Studio. All is running good so far, the card Roland Rubix 24 got detected automaticaly under my ubuntu 24.04 and seems to run well most off the time. But every few minutes I get audio dropouts in my recordings. then simply the sound is muted for the time of some milliesecinds and makes ugly holes in my recordings. Any idea what might trigger this? I checked the cable and the microphone. Both are fine, and the dropouts still are there when exchanging them. 
How can I debug this?

---

### Post by TheFu on 2024-09-06
Likely due to the USB interface not having a perfect connection. I see this with some old USB storage devices, though I don't see it with my audio microphone.  It could also be caused by having too much data trying to use a USB bus that can't handle all of it.  With USB3, I cannot imaging that would be any problem, but since USB buses are shared inside the system, there could be other traffic on the bus impacting all USB devices.  

Do you use USB storage?  Try without that.

Is your computer fast enough to handle the processing requirements for OBS?  Use a more CPU efficient video recording codec and a smaller resolution to lower CPU use below 50%.

Just some ideas for things to try.

---

### Post by greensoma on 2024-09-11
I think as well that USB might be causing this issues. I also had strange mouse issues with the same short dropouts.  I plan to buy an extra USB card and try to split the trafic on two devices. My pc is quite fast. 16 core with a big gpu should handle this with ease. 
Thanks for your thouts.

---

### Post by Autodave on 2024-09-12
USB....especially if you are using a USB hub....powered or unpowered.  I have seen it many times.

---

### Post by greensoma on 2024-09-18
Hey guys, for everyone stumbilng over this thread. Seems like using an extra standard PCIe usb 3.0 card solves the issue. Not sure if just seperating my mouse and keyboard usb traffic from the soundcard maybe is doing the trick or if the drivers might work better. Anyways it seems fixed for now. 
Its really strange that the onboard usb made issues. Its a quite new ASUS mainboard. Maybe to new? Anyways. I hope its fixed now. Thanks!

---

### Post by TheFu on 2024-09-18
```
lsusb -t

```Shows which devices are on which USB bus.

And if this is solved, please, please, use the Thread Tools button to mark it SOLVED. That greatly helps the community.

---

### Post by greensoma on 2024-09-20
I realised it isnt solved. I did a real test today and I still get dropouts. will have to research deeper on this one.

---

### Post by greensoma on 2024-09-20
Ok there is something totaly wrong with my USB now. Can barely move my mouse. Switched the mouse and have the same problem. Will do a system upgrade now and hope that it might fix this. wish me luck.

---

