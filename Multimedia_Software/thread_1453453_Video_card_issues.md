---
title: "Video card issues"
date: 2010-04-13
forum: Multimedia Software
---

### Post by sfm9497 on 2010-04-13
I am attempting to make a video machine only... which mean I have a Compaq 6435cl and I have installed the latest verion of ubuntu on it.
All I want this machine to do is play video from off the net on my LCD HD TV.
The video on board was all choppy when going into full screen mode so I put in a 3dfx Voodoo card and the same thing happens.
I cannot figure out how to install the drivers for this card in ubuntu so I was wondering if I should by a new video card. 
Do you have a recomended video card for ubuntu that would push HD video?
 
Many thanks
 
Stephen

---

### Post by cascade9 on 2010-04-13
For anbody else looking, heres the page with the hardware specs for the Compaq 6435cl- 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bpb11714&lc=en&dlc=en&cc=us&lang=en&product=240130](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bpb11714&lc=en&dlc=en&cc=us&lang=en&product=240130)

3DFX Voodoo cards.....I assume voodoo banshee. Long time no see for one of them. There are drivers for them with linux, but I doubt that would help.  

If you are playing full screen flash videos from the net, I've found that they tend to be choppy unless you've got very new hardware. If it is downloaded HD video, then your hardware isnt good enough to decode HD without problems. In this case, a newish nVidia card that does VDPAU (hardware decoding for video) would work. 

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)
[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

Only having AGP or PCI choices narrows down what you can use- the nVidia hardware only supports VDPAU from the 8 series onward, an the last nVidia AGP cards were 7 series. So, you've got to get a PCI card. A 8400GS PCI is probably the best choice from what is avaible.

---

### Post by sfm9497 on 2010-04-13
Thanks for your advice with my issue...
The video I mosy stream in my house is from tv.blinx.com and the most video come from megavideo...
It's fun watching the old tv shows. 
 
At this point I'm wondering if I should just invest in a new barbones system for this project.

---

