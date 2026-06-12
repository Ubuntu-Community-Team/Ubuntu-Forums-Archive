---
title: "Webcam in Dell monitor SP2208WFP unusable in Ubuntu?"
date: 2008-07-01
forum: Multimedia Software
---

### Post by DiabolusItalicus on 2008-07-01
Hello world!

A couple of months ago I bought a Dell XPS 420 and the Dell 22" SP2208WFP monitor with on-board webcam.
In spite of all my efforts, however, I'm unable to get the webcam work in my beloved Ubuntu 8.04 64-bit (while it works fine under MS Vista).

I checked dmesg and found that the monitor's webcam is detected, but the initialization fails:
> [ 51.898844] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[ 51.899238] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 51.899487] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[ 51.899489] uvcvideo: Failed to initialize the device (-5).
Frankly speaking, I'm stuck. Any idea, anyone?
Thanks in advance, and regards from Italy.

---

### Post by mohbana on 2008-11-22
same position.

---

### Post by cenze on 2009-01-20
Anyone made any headway on this issue?

---

### Post by gotanothergrot on 2009-06-10
Any new progress on this yet please??

---

### Post by sreejeshdnair on 2010-12-30
I am also at the same position? Can someone please help?

---

### Post by no2498 on 2010-12-30
i have seen this problem
am thinking you need to do a modprob of the uvc
i use a non uvc cam
so i dont keep up with the uvc cams

its like uninstall it then reinstall it
hope i pointed you the right way

---

