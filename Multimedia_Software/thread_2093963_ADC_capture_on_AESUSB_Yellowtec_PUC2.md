---
title: "ADC capture on AES/USB Yellowtec PUC2"
date: 2012-12-12
forum: Multimedia Software
---

### Post by jkorten on 2012-12-12
For my home sound recording system - two channel. I recently received a Yellowtec PUC2 lite, which allows me to capture the AES bit stream (same format as s/pdif) coming out of my analog to digital converter using Audacity in Windows.

I was fooling around with this device in Ubuntu and none of the "mic" selections worked. (The PUC2 device shows up in Audacity as "yellowtec PUC2: USB Audio (hw:1,0):0db:0). 

All resulted in a sound that made me think nobody knew what the sample rate was (a kind of noisy electronic hash sound correlated to my voice test).

Then once - magically the following device appeard in the selection list. USB device 0x46d:0x9a6:USB Audio (hw:2,0):0db:0

And it worked!

I cannot get this device back. I think I launched m2tech's driver at one point (snd-usb-asyncaudio). But I tried that again and I can't find that USB device that worked as an input selection.

I realize I am speaking about shadows here and somebody actually knows what I'm talking about and might be able to guide me here. Where did that input selection come from and why can't I get it back?

Thanks much.

Jerry

---

