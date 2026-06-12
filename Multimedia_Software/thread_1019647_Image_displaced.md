---
title: "Image displaced"
date: 2008-12-23
forum: Multimedia Software
---

### Post by finomeno on 2008-12-23
Hello!

I'm installing Intrepid on an laptop (Advent 7003) for a friend and I'm having a weird video problem. The image is displaced to the left leaving a black line to the right about 15px wide and cutting the same width off the image on the left side.

The weirdest thing about this is that it doesn't happen when I run 8.10 from the live cd, but as soon as I install it - the image shifts left.

Here's the output of "lshw -C display"
```

description: VGA compatible controller
product: VT8375 [ProSavage8 KM266/KL266]
vendor: S3 Inc.
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-2.0 vga bus_master cap_list
configuration: latency=32 maxlatency=255 mingnt=4

```

xorg.conf has surprisingly little left in it and no changes I make, including specifying the driver as either "s3", "savage", "vesa" or even "vga" seem to have any effect.

"vbetool post" got me to a black screen, I pressed ctrl+alt+backspace and the image was fine until I rebooted the laptop and had the same problem again.

Any suggestions on how to shift the image back to normal permanently?

Thanks in advance!

---

