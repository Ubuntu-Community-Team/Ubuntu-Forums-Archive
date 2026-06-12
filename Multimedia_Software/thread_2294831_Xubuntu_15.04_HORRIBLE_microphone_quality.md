---
title: "Xubuntu 15.04 HORRIBLE microphone quality"
date: 2015-09-13
forum: Multimedia Software
---

### Post by LastHylian on 2015-09-13
I've had this issue when using both a Blue Yeti microphone and now, most recently, the Astro A40 gaming headset with the Mixamp. The Blue Yeti has some professional grade recording quality, but when I was using it, everything came out sounding distant or like I was talking through a tin can. I switched over to a Windows machine and the quality was night and day. I returned the Blue Yeti and am now using the Astro A40, but again, it sounds like I'm using a cell phone.

I first noticed when my friends in Teamspeak pointed it out, so I did some recording with arecord (16 bit little endian, 48000, stereo) to check and sure enough, the quality is terrible. I've tried editing my /etc/pulse/daemon.conf file to 

 default-sample-format = s32le
 default-sample-rate = 48000
 alternate-sample-rate = 96000

but there is no noticeable difference. ANY HELP is greatly appreciated!

---

