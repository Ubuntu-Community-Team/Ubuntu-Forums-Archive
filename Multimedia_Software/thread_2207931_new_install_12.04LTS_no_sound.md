---
title: "new install 12.04LTS no sound"
date: 2014-02-25
forum: Multimedia Software
---

### Post by blm14 on 2014-02-25
OK, so, brand new dell precision T7610 (yes, I am happy!). Installed ubuntu 12.04LTS 64bit from the alternate ISO because I needed full disk encryption. I also have an NVIDIA gtx 770 (yes, happy again!). I opted for the additional sound card when I ordered the machine because it appeared that this was the only way to get any sound... I am pretty sure that the card is a PCI Express Sound Blaster X-Fi Xtreme Audio card.

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ID 280 Analog [ID 280 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Creative [HDA Creative], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Creative [HDA Creative], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



OK, so it looks like it sees everything.

$ lspci |grep Audio
00:1b.0 Audio device: Intel Corporation C600/X79 series chipset High Definition Audio Controller (rev 06)
02:00.0 Audio device: Creative Labs Device 0012 (rev 01)
03:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)



There are three audio output jacks on this beast. One is on the aforementioned PCI x1 audio card, one is on the motherboard, and the third is on the front panel. I have attempted to attach both headphones and external speakers to all three and no audio is forthcoming.Gnome shell audio tool see them: [http://imgur.com/rScn3F3But](http://imgur.com/rScn3F3But) no sound, ever. :(

---

