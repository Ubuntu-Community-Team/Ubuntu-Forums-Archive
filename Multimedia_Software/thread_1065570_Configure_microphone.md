---
title: "Configure microphone"
date: 2009-02-10
forum: Multimedia Software
---

### Post by DPic on 2009-02-10
I have a webcam with a built in microphone, as well as a separate one. If i look up their device names in Device Manager, i can manually input them into VLC's open capture device and they'll work. 

BUT

They do not show up for any applications like Empathy for voice and video chat. I can record a video in Cheese Webcam Booth, but it has no sound. Sound recorder doesn't detect them either. So how do i configure my mic to work in Ubuntu? 

Thanks!

P.S. Plugging one in at a time doesn't do it

P.P.S. If somebody wants to help me test voice/video calls with Empathy or GMail Chat TO Empathy, let me know.

---

### Post by DPic on 2009-02-10
Anybody??

---

### Post by DPic on 2009-02-10
Thanks to someone on #ubuntu, i got things working

I used gstreamer-properties to select my microphone

BUT does anybody know why they my Mic wasn't already default and if it's possible to change that?

---

### Post by DavidTangye on 2009-03-04
> **DPic said:**
> Thanks to someone on #ubuntu, i got things working
I used gstreamer-properties to select my microphone
Thanks a lot: this has fixed my problem too. I set the 'Default Input' to OSS as it seems to control a USB headset correctly, and 

[LIST=1]
[*]the Capture setting in the mixer is now set unmuted, whereas before it would keep resetting to muted
[*]I can now make recordings via my USB headset eg using the Sound Recorder app.
[/LIST]

---

