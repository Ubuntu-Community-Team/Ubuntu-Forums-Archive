---
title: "Mythbuntu crashes when I turn off and on my TV"
date: 2010-05-12
forum: Mythbuntu
---

### Post by Eternal Ponderer on 2010-05-12
I've been running mythtv since 0.17 on the same TV and never had this problem.  About 3 months ago, on mythbuntu 9.10, turning off and on my TV started to crash my mythbuntu box.  I spent weeks trying to figure it out: turning off all power management, switching nvidia drivers, using scripts that would keep the computer active and not turn itself idle.  Out of frustration, replaced all hardware with new.  I upgraded to 10.04, and the same problem persists.  The only common link is my TV.  I can put both boxes (new and old) on a standard CRT or LCD and it will stay up and running without ever crashing.

After turning off the TV the box will stay up.  However, when I turn the TV back on, it crashes.  Keyboard and mouse on console don't do anything, and I can no longer ping the box.  The only response I can get from the box is the remote receiver blinks its red light when I send a command from the remote.  If it matters, I'm using this as a frontend only, the backend is on a separate box.

It's completely baffling.  Why does turning on my TV crash the box?  I've got an nvidia 6200 PCIe DVI and an onboard Intel GMA X4500 HDMI on this box.  I don't use the X4500 because analog audio doesn't work, for whatever reason my TV will only accept the HDMI audio on the HDMI cable, which is fine, but that renders my analog headphones useless (which sucks when you've got sleeping kids in the house).

Any tips on how to resolve this would be greatly appreciated.   Thank You.

---

### Post by ian dobson on 2010-05-12
Hi,

This sounds alot like an xserver/graphics card driver problem. When you switch the TV back on the computer sees this and tries to rerad the EDC? data from the TV and blows.

Does your TV have a VGA input, if yes can you just try using VGA just to see if it's a problem with the device detection.

Maybr you can try forcing the Xserver to not do device detection and use fixed paramaters.

Also what version of the nvidia driver are you using? I've see in the release notes for a new nvidia driver that they fixed a crash caused by no scrren being detected and the driver reports a CRT is attached.
 
Regards
Ian Dobson

---

### Post by Chris Musampa on 2010-05-12
You could try checking the earth connections on the PC and TV are solid, it could be that one of them is floating, I had a similar problem a few years back with a printer.

---

### Post by Eternal Ponderer on 2010-05-13
Ian - Don't know how to set EDC information, but did disable EDID, with no luck.

Chris - for kicks, I put the TV and computer on new surge protector on a different outlet... No luck

I also went into TV diagnostics (Sony kdsr60xbr1) and reset the TV to factory settings... No luck.

I tried nvidia-96, 173, and the current 195.  All the same results; TV still crashes box when TV turned on.

Note when the box crashes, the last image still remains on the screen, it's not a total wipe out of video.  Also, if audio was playing, it will loop the last fractional second of audio.

Anyone have any idea how I might be able to debug this in realtime?  I can't see anything in logs that indicates a problem.

---

### Post by iponeverything on 2010-05-13
My first thought would be hardware gone bad on the mythbox.

I had a bad capacitor on my motherboard that was causing some very strange issues. I would also test the voltage coming out of your power supply, it might be failing and very unpredictable things happen when voltage is not right.

---

