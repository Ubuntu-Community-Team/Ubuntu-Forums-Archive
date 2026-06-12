---
title: "Plans for HTPC"
date: 2009-12-12
forum: Multimedia Software
---

### Post by Keith_Beef on 2009-12-12
I've been thinking for a couple of years about building an HTPC, and now looks like a good time for me to go ahead and do it.

I have some spare bits of hardware sitting around doing nothing, that I have used with Ubuntu so I know they work:
[LIST]
[*]Intel Q6600 CPU,
[*]Coolermaster GeminII heat sink,
[*]a bunch of 120mm fans,
[*]an nVidia graphics card,
[*]a Streamzap remote and USB receiver,
[*]a PCI WiFi card,
[*]a 512MB stick of DDR2 RAM.
[/LIST]

Whenever I buy a CD or DVD, I rip it and store it on a NAS, wired to a wireless router in the basement.
At the moment, I have a small Vaio connected to an stereo in the living room, so I can play music up there. Yesterday, I used VLC to watch a film over wireless, and it worked perfectly well.

So I was thinking of using these parts to build an HTPC by adding what I have to the following:
[LIST]
[*]a Socket 775 motherboard, either ATX or mATX
[*]a case
[*]a power supply
[*]a CompactFlash adapter and card or a Solid State Disc.
[/LIST]

The purpose of going for a CompactFlash adapter and card is to reduce the number of moving parts, so reduce noise and power consumption. All media files will be on the NAS, so I don't need storage in the HTPC, just a system disc. I have grown wary of Solid State Discs, after reading that there have been reliability problems, but I wonder if a system disc would be prone to the same problems (since there would be far fewer write operations than on a general purpose disc).

The Coolermaster GeminII is quite a big heat sink, big enough to sit two 120mm fans on it. I'm wondering is an *underclocked* Q6600 SLACR would run cool enough to do away with fans altogether.

Here's a small image of the heatsink.
[IMG]http://t0.gstatic.com/images?q=tbn:a-0QqBmFLPJPMM:http://www.devicepedia.com/wp-content/uploads/2007/02/coolermaster-geminii.jpg[/IMG]

And here are photos in a post I found discussing it.
[IMG]http://damagedmind.com/xmb/viewthread.php?action=attachment&tid=135&pid=505[/IMG]
[IMG]http://tweakers.net/ext/i/productsurvey/5526/4004.jpg[/IMG]

I can find 32GB CompactFlash cards for around $140 - $160 plus another $40 for the SATA adapter, or a 32GB SSD for around $120 (with no need for an adapter. A 400 Watt PSU would cost a little less than $100, and the case depends on the size of motherboard. More sticks of RAM might be worthwhile, but can be added easily later.

Dedicated HTPC cases seem WAY too expensive, and I don't really need a volume knob or a vacuum-fluorescent display... but there are some neat little mATX cases out there.

So here's the real stumbling block for me: how to choose a motherboard to fit the big heat sink, a case to accept the two, choose between integrated graphics (improve airflow, reduce heat and power consumption), choose the size of CompactFlash, and choose an HTPC installation.
Mythbuntu, XBMC, Boxee, Moovida? 

I would appreciate comments from anybody who has built an HTPC, or is planning one.

K.

---

### Post by specvthis on 2009-12-21
That heatsink is a monster. Absolute beast.

I say with Boxee's fast growing support and soon to be release Settop box I would say go with Boxee. The app store has grown considerably and with the hardware you are throwing around it will easily play/decode everything. It has HD-Accelerated decoding and show keep your system running cool.

Case. I have no idea what case would support that heatsink. I would recommend getting a cheap video card that supports Hardware Acceleration since Boxee and XBMC support it out the door.

---

### Post by Ubuntaqua on 2009-12-22
Using a Compact Flash card to reduce noise while at the same time using a giant monster like this Quad core seems insane to me.

You want a HTPC you do not need all that horsepower. If you want HD movie playback, a core2 Duo is enough, or any cheaper CPU with a nvidia card using VDPAU (almost all nvidia 8000 series card and later can use VDPAU). You will save heat (less noise from fans), power, and size.

I've built my HTPC a few month ago using a mini-ITX mainboard, with a dual core Atom, and a ION chipset. the samll nvidia integrated graphic card. It handls HD 1080p very well.

One other problem with a big CPU/fan like that is size : it's harder to find a nice looking HTPC case to put in hte living room.

---

