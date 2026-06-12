---
title: "Recording static?"
date: 2009-03-26
forum: Mythbuntu
---

### Post by FrankVolkel on 2009-03-26
Hi all, 

I'm new to MythTV and Mythbuntu. I have no problems viewing Live TV, however, all my recording yields static. I have performed a reconfiguration from the backend several times but to no avail. 

I am using a Hauppauge HVR 1300 tuner card, V4L for the video device and the Television input. I am not using any list grabber, as my country does not support them. 

Any form of assistance is greatly appreciated (=

---

### Post by FrankVolkel on 2009-03-27
I managed to get recording to work by downloading and installing the latest Conexant firmware as documented at [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600). However, I ran into further audio problems. 

Audio from the tuner was crackling and so were those from the playback. Some quick Googling revealed that this was probably due MythBuntu errornously outputting the audio to the front, which results in clipping and thus, crackling. 

I fixed it by installing a fresh copy of Ubuntu 8.10, followed by MythTV components individually. However, this time round, I am unable to get any audio from the tuner. The audio device is working as playback via VLC works and so does CD playback in MythTV. 

As always, any help is appreciated.

---

### Post by FrankVolkel on 2009-03-27
Having scowled the net for a couple of hours, I'm yet to find anything helpful in resolving the issue (other than the fact that the 1300 is an Eurpoean equivalent of the 1600 and uses CX88 instead of CX18)

lspci displays the following: 

01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: Hauppauge computer works Inc. Device 9601
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
	Subsystem: Hauppauge computer works Inc. Device 9601
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa

01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: Hauppauge computer works Inc. Device 9601
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802

---

