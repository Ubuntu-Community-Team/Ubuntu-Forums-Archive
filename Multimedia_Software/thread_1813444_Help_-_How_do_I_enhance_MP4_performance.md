---
title: "Help - How do I enhance MP4 performance?"
date: 2011-07-27
forum: Multimedia Software
---

### Post by WinRiddance on 2011-07-27
Hi all. I've installed an older Intel/Compaq Evo machine with a single core 2.0 Ghz. processor and 2 GB of DDR ram in our livingroom, for movie viewing purposes. I'm intentionally using Xubuntu 11.04 without 3D to keep the used resources down to a minimum. There are no 3D games on this machine either since I'm using it strictly for watching movies on our TV. The graphic card is integrated with the 845 chipset/mainboard. It does receive up to 64 MB of Ram though which is drawn directly from the onboard 2 GB DDR. The following links provided me some linux related info. about this chip but I honestly have no idea how to use that since the intellinux site is set up horribly (IMO).

[http://www.intel.com/p/en_US/support/highlights/graphics/intel845g/](http://www.intel.com/p/en_US/support/highlights/graphics/intel845g/)
[http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

According to intel the graphics chip is the "Intel Extreme Graphics Driver" :p with full 2D and 3D support. I've tried Parole, VLC, Totem, and smplayer. MP4 problems on all of them but VLC and smplayer seem to work best. Here the details about this graphic chip:

[http://www.intel.com/support/graphics/intel845g/sb/CS-009078.htm](http://www.intel.com/support/graphics/intel845g/sb/CS-009078.htm)

So with a 2 Ghz. processor, low resources, 2 GB of DDR, of which 64 MB is dedicated to the graphic chip, I figured that playing movies wouldn't be a problem .. and it's almost not. I can play wmf, avi, mp3, and other codecs without any problem at all. Even BlueRay works fine as long as they're AVIs. But as soon as I try to play an MP4 movie the experience gets very unpleasant. No crashes, just endless stuttering and sometimes lack of audio. Is there perhaps some way that I can improve that performance permanently without buying another graphic card? The machine is an ultra slim form factor so I can't even add a narrow format card to it. I'm stuck with the embedded 64 MB chip but I'm hoping that someone here can help me to get the most out of it. Thank you.
.

---

### Post by WinRiddance on 2011-07-29
... bump ... :(
No tweaks or tips that anyone is aware of?
.

---

### Post by 4Orbs on 2011-07-29
My ^GUESS^ is that the problem is not because the file is mp4, but instead that the rip is true HD and the resolution of the mp4 is 720 or higher in pixel height. Probably hi-def audio also. Too much stuff going-on for your hardware to manage. The bluray rips work ok because they are avi and probably not HD anymore. I could be completely wrong in my understanding of such things.

---

### Post by BicyclerBoy on 2011-07-29
As you have tried to use the intel driver..
You may get a bit more out of the intel graphics by using the intel driver from xorg-edgers ppa.
Don't expect any h/w decode because only partial mpeg2 decode is possible in 845 chipset.
The GMA900 (845 chipset) has been partly forgotten in the pursuit of sandybridge support.

Can you configure the BIOS to get more video ram ?

---

### Post by WinRiddance on 2011-08-04
Thanks, but no, the bios won't allow me to assign more ram. According to a page from intel the ram is supposed to be assigned automatically, based on availability. The super slim factor Evo is capable of handling a maximum of 2GB ram which this machine has. The graphic chip is supposed to be as good as an AGP4x which I figured would be able to handle MP4 movies. With the amount of ram that's available, the graphics should be using 64 MB by default. So if that's not enough **then the answer to this thread is** ...

Need either another, more modern machine ... or do without MP4 movies altogether since none of 5 different media players that I tried are able to handle them. Bummer ...
.

---

### Post by rubylaser on 2011-08-04
I'm going to assume that the bitrate is too high for your hardware to handle.  Can you post a link to a sample and I'll try in on my ION HTPC?  Really, the best way to guarantee this works is to just get an NVIDIA 220 card (if you have an available PCI Express x16 slot) for around $45 and use VDPAU.  That will play anything you throw at it without breaking a sweat.

---

### Post by WinRiddance on 2012-01-27
Okay, this may not be the desired solution for everyone, **but it works for me** ... :D
I sold the computer that I was trying to use in our livingroom and then I sold my fairly high end laptop too. Following that I purchased a new Laptop with 8 GB of RAM, Quad core 64 bit  processor and 1 GB dedicated Intel grpahics chip, expandable as needed with additional system Ram. One direct HDMI port and 2 USB 3.0 ports as well (in addition to a couple of USB 2.0 ports). I also created an 8 GB swap partition. Then I did a fresh install of Xubuntu to which I later added Compiz for personal fun.

_Now I have a phenomenally performing machine_ in the livingroom, hooked up to our 48 inch flat screen with HDMI, and I'm happy as a clam. Being a laptop, it's environmentally friendly & energy saving. Everything runs as smoothly as you can only imagine, quality is crystal clear, and I can beat this machine with apps all I want and it won't crash or lock up on me. The other day I opened up 25 huge photos for simultaneous editing, while downloading, emailing, and browsing too. No problem at all, _hardly a performance decrease to notice._ My remote control is a wireless $30 mouse/keyboard combo.

**Normally I replace my system every 2 - 3 years anyway** but these hardware specs should be good enough for the next 5 years. My upcharge was only apx. $200 more than I would have paid for a cheaper system, and I more than made up for that with the sale of the other two computers. It really doesn't get much better than this ...

.:D

---

