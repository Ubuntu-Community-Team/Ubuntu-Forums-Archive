---
title: "SPDIF on Dell D620 thru D-port not working"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by dragonflyFZX on 2008-02-06
Hi,

I have a Dell Latitude D620 running up-to-date 7.10 Kubuntu.  I have a port replicator that has an SPDIF coaxial port, which I connect to my amp.  But I dont get digital sound...

Has anyone with this setup succeeded?

Here is some info

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 20
 1 [default        ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:1d.7-8.3, full

bjvca@dragonfly:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

