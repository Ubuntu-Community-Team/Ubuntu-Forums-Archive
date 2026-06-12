---
title: "HD DVR - High Definition Digital Video Recorders"
date: 2009-06-08
forum: Multimedia Software
---

### Post by pedja_portugalac on 2009-06-08
Yesterday I get one of this boxes as I subscribed 12 months cable TV access (mine is over satellite). It's Thomson DSI8020CAB. The key characteristics are:

- Supports H264 / AAC / VC1 with HDMI/HDCP digital output
- Compliant with open standards (DVB, multiple conditional access, ..)
- Built-in dual broadcast tuner/demodulator and up to 500 Gbyte hard-disk drive for digital audio/video recording 

The quality of video is impressive on full HD TVs. One can record anything on internal hard drive for later viewing among lot of other options. But my internal hard drive is just 250GB big and you can imagine how fast it can be full with HD movies or documentaries. 

I was touched by the reportage from National Geographic channel about Dogtown and Pit Bull rescue operation where 22 pit bulls, forced to fight, were saved from american football star Michael Vick. So I recorded it in HD format and planed to move it from the box into my computer for compression and other personal settings. 

That's when this box start to disgust me. There's one USB and one Ethernet hub on the back of the box but neither is functional, here in Portugal. I thought, I'll remove hard disk from the box and connect it to my computer as an external usb disk even if it was guaranty sealed with some kind of plastic I had to broke. 

[img]http://img44.imageshack.us/img44/7338/thomsondsi8020cab.jpg[/img]

Well, at first Ubuntu recognized it as USB disk but wasn't able to mount it. I reboot to vista, same thing. Googling told me it is probably file system problem. Till now everything points me to exFAT, newest microsoft proprietary file system. I am not sure if it's exFAT cause it's proprietary file system, patch for linux kernel still doesn't "officially" exist and Ubuntu recognized it from the first plug, just like windows vista. Both were unable to mount it whatever I've tried. No way to activate it under vista and under Ubuntu I have patched my kernel with so many junk from the net, I'll have to reinstall whole system to be safe again. In my opinion, this hard disk is badly encrypted or whatever, everything but not partitioned and formated normal way. 

Any idea?

I'll be happy to hear your experiences, if any, about this or another HD DVR receiver box or ways to explore "normally" inaccessible disk.

---

### Post by steefjeqv on 2009-06-09
Hi,

I'm not able to help you with this particular problem.
One things for sure : a lot of companies offering tv content do nasty things with the settop boxes they provide. Like encrypting harddisks.

I suppose any linux based settopbox will be more flexible.

The only stuff I use is called VDR and it basically turns your linux computer into a DVB settopbox.
It's versatile and offers lots of possibilities through plugins :
- removing advertising
- recording
- timeshifting
- net streaming
- CAM support
and so on.

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

Greetings,
Steven

---

### Post by pedja_portugalac on 2009-06-09
Hi Steven

I also have one of this gadgets (Pinacle DVB USB stick) but it's only meant to receive terrestrial broadcastings. Here in Portugal, it's new and there's only 4 channels + 1 test HD channel. So if we want to have good quality programs we have to pay and receive those by cable or satellite and they are always codified. 

The good side of this new boxes is support for HD video/audio and possibility to register shows on internal hard drive. The bad one was explained in my first post above.

I am wondering now if it is possible to buy an external HDMI card which support input signal (todays computer comes with HDMI only OUT hub). That way, using some program we could pretend our computer is a TV screen and capt the signal coming from the box.

Cheers and tot ziens

---

### Post by pedja_portugalac on 2009-06-09
Another idea comes to my mind now. 

I have 2 of this boxes at home. One, big, with hard disk for registering in my living room and another, small, without that option in my bed room. All the channels are same on both boxes, HD and normals.

What if I put another SATA disk, formated exFAT but not encrypted in a place of the original one? Will it be able of registering there or the box software is also within that disk? 

I'll have to open small box from the bed room to see if there's a small hard drive containing box software or it's built inside motherboard.

I have to find one same SATA disk.

---

### Post by steefjeqv on 2009-06-14
Hi,

Replacing the disk is a possible solution, but the box will most likely not accept this new disk. 

As for digital broadcasting, the situation here in Belgium isn't much better.

I can receive six FTA terrestrial channels.

Cable is even worse. You need a subscription, nearly all channels are encrypted and can only be watched using the box offered by the provider (nothing else). You can buy or hire this mediocre box from them.

The only more or less good provider is via satellite. It's encrypted but you can use your own hardware.

If your cable provider uses DVB-C with encryption, it may be possible to use VDR. You'll need something like this though :

[http://www.dvbshop.net/product_info.php/info/p2258_Mystique-CaBiX-C2--DVB-C--HDTV--CI-Connector--Windows-Linux.html]("http://www.dvbshop.net/product_info.php/info/p2258_Mystique-CaBiX-C2--DVB-C--HDTV--CI-Connector--Windows-Linux.html")
Combined with this :
[http://www.dvbshop.net/product_info.php/info/p2260_Mystique-View-CI-Interface--f--1-CAM--for-PCI-and-or-3-5-.html]("http://www.dvbshop.net/product_info.php/info/p2260_Mystique-View-CI-Interface--f--1-CAM--for-PCI-and-or-3-5-.html")

Greetings,
Steven

---

