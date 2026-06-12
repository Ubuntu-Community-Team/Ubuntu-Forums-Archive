---
title: "Audigy NX and Kubuntu 5.10 problems"
date: 2006-02-06
forum: Multimedia &amp; Video
---

### Post by weid83 on 2006-02-06
I'm having problems getting surround sound to work with my Audigy 2 NX (the usb one...).  I get stereo sound from amaroK using gstreamer engine with artsink plugin.  However when I try the artsink plugin in kaffeine with gstreamer part it just quits the program.  When I switch to kaffeine-xine I keep getting seg faults or device is busy.  So I created an /etc/asound.conf and added dmix.  I was then able to get stereo 2.0, 2.1 and 3.0 sound from kaffeine-xine.  However anything above that and passthrough all say the device is busy.  So I read that alsa 1.0.10 had dmix by default enabled on all channels, so I upgraded to that, but still have exactly the same problem...  Does anybody know the correct asound.conf settings to enable dmix on all channels or otherwise how to get surround sound working with the audigy nx?  This is the only thing keeping this box from becoming the replacement for my windows media center box...  Thanks in advance

---

