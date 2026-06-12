---
title: "Creative Labs SB0950 ExpressCard Sound Blaster X-Fi Notebook Audio System"
date: 2013-02-05
forum: Multimedia Software
---

### Post by FAYZER on 2013-02-05
Could someone help me get this device working in stereo on Ubuntu 12.10?  I'm having, in a way, the reverse problem of many people in the forums.  The output modes I have in the mixer has only surround sound modes (4.0, 5.0 and 5.1 speaker modes), no 2.0.  I think the root of the issue is that it is an expresscard solution which uses an analog jack that can be both a headphone jack OR an analog surround output with a special dongle that comes with it.  I think the ALSA drivers expect a device with two outputs, but that is just my guess.  I only use this device as a step up from the headphone amp in my laptop, which doesn't drive studio headphones very well. The output I get right now is attempts to phase shift across four speakers and is producing popping sounds.  I'm new to Linux, but I am a software engineer/programmer.  

UPDATE: I noticed that when I switched to 5.0 speaker mode, my headphone was temporarily crystal clear.  Later the poping static came back. (Even at low volume).  It seemed like playing with the fade and balance controls in the mixer sometimes would temporarily fix the issue again, but the static always comes back eventually.  It seems to be something where it either happens or not when playback begins.  (i.e. if I play a two hour video and the audio is fine, it will continue to be fine for the duration of playback.  If I play something else or even reopen the same file, the issue may return.

Here is an amazon link to the device
[http://www.amazon.com/gp/product/B001BS3A3E/ref=oh_details_o01_s00_i00](http://www.amazon.com/gp/product/B001BS3A3E/ref=oh_details_o01_s00_i00)

My laptop is a Clevo W870CU based custom build from M-Tech:
ChipSet: Intel PM55
CPU: Core i7-820QM (4x1.73GHz+HTT, 45nm, 8MB L3, 2.5GT/s QPI, 45W)
8GB RAM
ATI/AMD Radeon Mobility 5870 (running AMD Driver 13.1).
500GB drive (Split between Windows 7 and Ubuntu 12.10)
Onboard Audio: 6-Channel Realtek ALC888 HD Audio

---

