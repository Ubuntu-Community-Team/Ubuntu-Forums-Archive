---
title: "Skype - Problem with audio playback"
date: 2009-08-23
forum: Multimedia Software
---

### Post by samirjohn on 2009-08-23
Also, how do I get my Creative (Live! Cam) webcam to work on Ubuntu 9.04?

---

### Post by JoshStrobl on 2009-08-23
I assume your webcam is USB, so go under options then do the following:
Sound In: make sure its USB Device
Sound Out: Pulse or headset
Ringing: Default Device

---

### Post by samirjohn on 2009-09-06
I don't see "USB Device", under "Sound In" in SKYPE.

---

### Post by samirjohn on 2009-09-06
I got the sound to work now. Here are the settings I used in Skype:

In the "Sound Devices" (under Options), I set the following:

Sound In: HDA Intel (hw:Intel,0)
Sound Out: pulse
Ringing: pulse

Next problem: When I go to "Video Devices" and hit the "Test" button, I get a haze of green lines jittering about, in the little test screen (looks like one of those old screen savers!). I ccne see my USB cam light up, whihc means the OS has detected it. In fact, in the "Video Devices" window I see "USB Camera ... (/dev/video0)", under "Select WebCam". That's the only option I see in the drop-down.

Any Idea how I can get this test to work?

Thanks a lot!

---

### Post by andersja on 2009-10-06
samirjohn, 

Try this link for more info about Skype & webcam compatibility:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

