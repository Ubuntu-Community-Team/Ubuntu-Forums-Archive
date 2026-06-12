---
title: "HDMI remote control"
date: 2009-02-14
forum: Multimedia Software
---

### Post by freakalad on 2009-02-14
Running Ubuntu Intrepid Ibex (will add Mythbuntu or some such later; probably in a VM). 
GPU is a ATI Radeon Saphire HD 3450 with VGA, DVI & HDMI interfaces.
Connected to a Sony Bravia TV/Monitor.
Got audio & video working OK over the HDMI; using proprietary driver courtesy of EnvyNG & using ALSA as my audio mixer of choice.

The Bravia has a HDMI remote control feature, whereby you can control HDMI-capable devices from a control sub-set on the remote (Indicated as "BRAVIA Sync" on the RC; also referred to CEC or "Consumer Electronics Control").
Media control: play, pause, stop, fwd, rew

Does anyone know if there's some way to make use of this feature? Expect I may have to make use of some LIRC drivers/libraries for some of the functionality.

---

### Post by GrahamJM on 2009-02-23
It would be very nice if there was suitable support for CEC for any adapters. At the moment it doesn't look like any video cards support it.

From a reading of the specs, it requires the video driver to get involved in order to handle the physical vs logical addressing mechanism. Devices attached to the display are provided with a logical address that is provided via a discovery process by the display...

---

