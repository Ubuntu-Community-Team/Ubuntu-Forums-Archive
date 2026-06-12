---
title: "LG226W &amp; e-GeForce 7600 GS woes"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by skaramanger on 2008-04-20
Hello,

I've been using the above combo with the NV driver for some time now. Tried to install the nvidia drivers for my card without success. I was hoping that someone would be kind enough to decipher the output from a run of get-edid.

```
yyyyyy@xxxxxxxx:~$ sudo get-edid | parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID
```

Might this have anything to do with LG and MS little patent agreement or is it just  the video card or both?   Like it says :(

TIA

Skaramanger

---

