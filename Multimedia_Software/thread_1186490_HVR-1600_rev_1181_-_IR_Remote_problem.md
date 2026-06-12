---
title: "HVR-1600 rev: 1181 - IR Remote problem"
date: 2009-06-13
forum: Multimedia Software
---

### Post by tmkt on 2009-06-13
After 2 days of trying, compiling lirc_pvr150, using irw, mode2..
I am not getting any results from my HVR-1600 remote..
Save me from having to buy a bluetooth remote or something..

Jaunty - Mythbuntu..

 dmesg|grep lirc
[   12.705467] lirc_dev: IR Remote Control driver registered, major 61 
[   12.728885] lirc_pvr150: chip found with RX and TX
[   12.729148] lirc_dev: lirc_register_plugin: sample_rate: 0
[   12.811930] lirc_pvr150: firmware of size 302355 loaded
[   12.812036] lirc_pvr150: 743 codesets loaded
[   12.856181] lirc_pvr150: Hauppauge PVR-150 IR blaster: firmware version 2.1.0
[   12.858707] lirc_pvr150: cx18 i2c driver #0-1: no devices found


IRW - no results..

Edit:
Working now installing intrepid IR worked, upgraded to Jaunty and continued working, so not sure why it wasn't working.

---

