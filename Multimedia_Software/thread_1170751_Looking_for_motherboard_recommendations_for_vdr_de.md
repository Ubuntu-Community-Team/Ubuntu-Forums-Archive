---
title: "Looking for motherboard recommendations for vdr desktop"
date: 2009-05-26
forum: Multimedia Software
---

### Post by flyingdutchman on 2009-05-26
Hello

Would like to see what people use for motherboards for a VDR tv config.
I would like to use a mini itx board to minimize power and noise.
So small board with following requirements:
[LIST]
[*]Fanless or low noise fan
[*]board graphic controller with vdi/hdmi connector, with Linux VDR/Xorg support for H.264 ( HDTV 1080p, DVB-S2 video capable + blu-ray video format)
[*]Audio either via HDMI or digital out
[*]PCI slot capable of using riser/extender card to support at least 2 PCI slots for DVB tuners
[*]IDE for blu-ray player and Flash drive
[*]Sata for disk (recording)
[/LIST]
How much memory should it support, would 2G be enough, would like to use inram filesystem booted from flash.
For video I get the impression that either Nvidia or Intel based chips should be preferred.

Some boards have a LVDS interface, can this be used as extra front panel display?

I had a look at Jetway's J9F2-KHDE board, initially it looked good, but it has ntel graphics chipset that from what I saw on various forums cannot handle H.264 ( blu-ray) video format.


From the various forums I get the impression that the video drivers support for via boards is a nightmare, same for ati based boards.

Looking forward to some feedback.

---

### Post by xzero1 on 2009-05-26
You might be interested in this blog post: [http://blog.charlies-server.com/2007/09/13/hd-video-playback-in-linux](http://blog.charlies-server.com/2007/09/13/hd-video-playback-in-linux)
Though it is a bit dated, what I took note of was the quality of using the video card vs using the cpu. Now this may not apply to the current cards, but might want to check into this before building your system. When you have your system built and tested please post back on the results.

---

