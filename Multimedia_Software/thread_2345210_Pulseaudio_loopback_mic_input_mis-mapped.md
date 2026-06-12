---
title: "Pulseaudio loopback mic input mis-mapped"
date: 2016-12-01
forum: Multimedia Software
---

### Post by coldspring2 on 2016-12-01
I am using Ubuntu 16.04 on a first Gen Zotac nvidia ION Motherboard.  These devices are notorious for miss-mapping HDMI output channels, but I have modified the HDMI 7.1 section of pulseadiou's default.conf file to have all signals coming out of the proper channels.  I am now attempting to run some Karaoke on the device so I have involved the rear mic loopback by  doing a:

pactl load-module loopback-module.

This generally works as it should and produces an analogue stereo input device which outpust a mono rear mic input to two speaker along with the HDMI audio coming from the karaoke software.

THE PROBLEM IS:  They should be sent out of the front-left and front-right speakers, however the mic signal is coming out of the front-left and rear-left speakers.  How do I remap this errant signal.  And if it is possible to remap the mono rear mic input to a desired speaker, How to I map it to just the front-center speaker?

Thanks for any help offered.

Chris

---

