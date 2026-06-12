---
title: "Experts: Is this hardware specification okay?"
date: 2008-03-24
forum: Mythbuntu
---

### Post by IntuitiveNipple on 2008-03-24
I wonder if those MythBuntu/MythTV experts amongst you could review this proposed specification for a future-proof and expandable TV, PVR, and Home Theatre system with front and back-end combined in one PC. I've been doing a lot of reading of the Wikis, forums, and product pages trying to identify hardware that is well-supported by Linux and MythTV and won't present insurmountable obstacles.

The system will be used by my father - someone who finds even logging in a difficult concept. His eye-sight and hearing are beginning to weaken so it will be used with at least a 1.8m diagonal projector screen and surround-sound. His current TV is an old 24-inch widescreen CRT which has just died so anything will be a vast improvment. The aim is to build something now that is not going to become obsolete for many years (6+).

I suspect the most important decision is to use Nvidia video (since that seems the only one well supported by drivers) with an HDMI connector built-in on the motherboard and surround-sound speaker outputs too. At a later date additional larger hard disks can be added.

I've got a few questions I can think of right now:

[LIST=1]
[*]Are the Hauppauge TV cards compatible with the AMD CPUs (The LambaTek shop gave a warning and said to ask about compatibility) ?
[*]Is the CPU specified sufficient for full 1080p decoding if he should want that in the future?
[*]With [libdca](http://www.videolan.org/developers/libdca.html) for DTS audio sources will the system be able to deliver surround sound via the mobo audio outputs, and if so, will that require using OSS rather then ALSA/Pulseaudio?
[*]Having the FreeView and FreeSat tuners, will one remote control handle both (I presume the remote interfaces to MythTV so it decides what to do) ?
[*]Does MythTV pick up Electronic Programme Guide data from the signals, or will an Internet connection and subscription service be required?
[*]Which architecture should be used, 32-bit (x86) or 64-bit (amd64) - reasons ?
[/LIST]

Key requirements:

[LIST]
[*]All hardware in one box (so no separate AV Receiver)
[*]Drive a projector using VGA
[*]Option to drive HDMI TV in the future
[*]Surround-sound with on-board amplification
[*]Record channel 1, view (and record?) channel 2
[*]Picture-in-Picture
[*]Remote Control
[/LIST]

I started off picking components from just about anywhere but then discovered that LambaTek seem to carry stock for everything that is required at competitive prices (including replacement projector lamps and a screen) which hopefully will save on shipping costs.

[Antec Fusion 430 HTPC micro-ATX Enclosure](http://www.antec.com/ec/productDetails.php?ProdID=08738) [£95.16 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B79255)
[IMG]http://www.mythtv.org/wiki/images/e/e0/Fusion.jpg[/IMG]
[LIST]
[*]14(H) x 44.5(W) x 41.4(L) cm
[*]VFD display ([MythTV setup](http://www.mythtv.org/wiki/index.php/LCDproc))
[*]PSU 430 Watt ATX12V v.2.0, Active PFC
[*]Black with silver aluminium front
[*][Video Review](http://video.google.com/videoplay?docid=-7555005557176259748)
[/LIST]

[Hauppauge WinTV NOVA-T 500](http://www.hauppauge.co.uk/pages/products/data_novat500.html) [£43.86 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=1242473)
[LIST]
[*]Dual digital DVB-T receiver
[*][Freeview](http://www.freeview.co.uk/home)
[*]Remote control
[*]PCI
[/LIST]

[Hauppauge WinTV Nova HD S2](http://www.hauppauge.co.uk/pages/products/data_novahds2.html) [£59.53 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B76654)
[LIST]
[*]Single HD DVB-S2 and DVB-S satellite tuner
[*][FreeSat](http://www.freesat.co.uk/) BBC & ITV HD TV ([Astra 2 28.2E](http://www.ses-astra.com/business/en/satellite-fleet/index.php) - same as Sky TV)
[*]Remote control
[*]PCI
[/LIST]

[Abit AN-M2HD-LE](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket+AM2) micro-ATX motherboard [£39.31 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?origin=gbase22.2&prodID=B97195)
[[IMG]http://www.abit.com.tw/upload/products/an-m2hd_top_140.jpg[/IMG]]("http://www.abit.com.tw/upload/products/an-m2hd_top_500.jpg")
[LIST]
[*]HDMI
[*]Nvideo Geforce 7050PV/NF630a
[*]Socket AM2
[*]7.1 channel audio
[*]Dual monitor (HDMI and VGA D-sub)
[*]1 x PCI-E x16, 1 x PCI-E x1, 2 x PCI
[*]Gigabit Ethernet
[/LIST]

AMD Athlon 64 x2 4200+ 2.2GHz 65W 90nm [£31.28 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B56326)
or
AMD Athlon 64 x2 5600+ 2.8GHz 89W 90nm [£73.21 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B69331)

Corsair DDR2 Twinx2 XMS2-6400 2GB 2x128mx64 240 4-4-4-12 64m [£28.16 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B94175)

Hard Disk: Deskstar P7K500 250GB SATA-2 3.5inch 7,200rpm 8MB 0A35399 [£27.02 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B89420)

[LG GGC-H20L](http://uk.lge.com/products/model/detail/bluray_ggch20l.jhtml) Super Multi Blue Blu-ray Disc Drive [£82.50 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B89098)
[LIST]
[*]Blue-Ray, 6x BD-Rom
[*]HD DVD-Rom Drive, 3x HD DVD Rom
[*]DVD-RAM/-R/+R/-RW/+RW dual-layer
[*]CD R/RW
[/LIST]

[Emprex Wireless 9029URF III MCE Keyboard](http://www.emprex.com/02_products_02.php?id=225) for Windows XP Media Center Edition [£19.21 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=B97165)
[LIST]
[*]Keyboard
[*]Trackball mouse
[*]Remote control
[*]2.4GHz USB receiver
[/LIST]

[Creative Inspire T7900](http://uk.europe.creative.com/products/product.asp?category=4&subcategory=789&product=10321) 7.1 Speaker System [£50.95 from LambaTek](http://www.lambda-tek.com/componentshop/index.pl?prodID=1144349)
[LIST]
[*]8 Watts RMS p/channel ( 6 channels)
[*]20 Watts RMS centre speaker
[*]24 Watts RMS subwoofer
[/LIST]

---

### Post by utar on 2008-03-25
Hi


I built a media centre PC at the start of the month with the same case and TV card.

The case is very nice, and looks 'flash' under my HDTV.  The only one problem I had was if I touched the front panel a static discharge would reset the computer.  This was easily fixed though by attaching a wire between the front panel and the power supply casing (if you google you will find this is quite a common problem.)

TV tuner works well, some people report that occassionally one tuner 'drops out', however I haven't seen this myself.

Only thing to be careful with is HD playback.  I have a 2.66Ghz C2D and this can stuggle when the camera pans on 1080p h264 content, and this is with TV shows which will have a bit rate considerable less then bluray.  I found using mplayer instead of the internal player fixed this, however I doubt my CPU will have the power to playback bluray (even if the software was available on Linux).

The problem is that accerated video decoding (with the possible exception of mpeg2 which is not processor intensive) is not possible under Linux.  As such I may be tempted to save money and lose the bluray drive and instead get a std DVD drive.

No internet connection is needed for the freeview EPG, although not sure about sat.  One would be benefical though so that you can remote manage the box in case of any problems and to make updating easier.

One remote can control all of Mythtv.





Utar

---

### Post by IntuitiveNipple on 2008-03-25
Thanks for your feedback, it has already helped me adjust the CPU specification and feel more confident generally.
> **utar said:**
> 
The case is very nice, and looks 'flash' under my HDTV.  The only one problem I had was if I touched the front panel a static discharge would reset the computer.  This was easily fixed though by attaching a wire between the front panel and the power supply casing (if you google you will find this is quite a common problem.)

Thanks! That is really useful to know ahead of time. 

Do you find the depth of the case, especially when cables are plugged in (like thick VGA cables) makes it stand out a bit far? I noticed it'll not fit in many furniture cabinets because of that.

> **utar said:**
> 
TV tuner works well, some people report that occassionally one tuner 'drops out', however I haven't seen this myself.

Yes, I'm on the linux-dvb mailing list and seen a few reports of Nova-T disconnects with the latest builds. It looks like it is solvable if it occurs though.

> **utar said:**
> 
Only thing to be careful with is HD playback.  I have a 2.66Ghz C2D and this can stuggle when the camera pans on 1080p h264 content, and this is with TV shows which will have a bit rate considerable less then bluray.  I found using mplayer instead of the internal player fixed this, however I doubt my CPU will have the power to playback bluray (even if the software was available on Linux).

On that basis I've added a 2.8Gz 5600+ to the list as an option. It sounds as if one of the issues is how good the libraries the player uses are, and again that is solvable.

> **utar said:**
> 
The problem is that accerated video decoding (with the possible exception of mpeg2 which is not processor intensive) is not possible under Linux.

My expectation is that in a year or so accelerator products might become available so if he finds himself wanting to watch a lot of Blue-Ray movies there may well be a solution longer term.

> **utar said:**
> 
 As such I may be tempted to save money and lose the bluray drive and instead get a std DVD drive.

I considered that, but wanting it to be future-proof now I thought the LiteOn is a good choice since it is relatively inexpensive and covers all the formats from CD through DVD to HD/Blue Ray, and can write CD/DVD too.

> **utar said:**
> 
No internet connection is needed for the freeview EPG, although not sure about sat.  One would be benefical though so that you can remote manage the box in case of any problems and to make updating easier.

Yes, updates and remote management is part of the plan. My question was more about the programme guides since I noticed in the USA the need for Schedules Direct.

---

### Post by volkswagner on 2008-03-25
> Do you find the depth of the case, especially when cables are plugged in (like thick VGA cables) makes it stand out a bit far? I noticed it'll not fit in many furniture cabinets because of that.


With my DVI cable Crammed against the back of my cabinet, the face of the box is 18.25 inches away from the back of the cabinet.  You should allow two inches for cables/connectors.

I love this case.  The VFD is useful.  I was not able to have a large clock display (images not readable when selecting large clock in myth setup).  It is hard to read past 6-8 feet depending on eye sight.  Once you get used to the menu navigation it is great to easily play music without powering the TV/Display.

---

### Post by utar on 2008-03-25
> **IntuitiveNipple said:**
> Thanks for your feedback, it has already helped me adjust the CPU specification and feel more confident generally.

No problem, glad I can help!

> **IntuitiveNipple said:**
> Do you find the depth of the case, especially when cables are plugged in (like thick VGA cables) makes it stand out a bit far? I noticed it'll not fit in many furniture cabinets because of that.

It is a deep case, I had to look around to find a TV stand which was big enough.  I agree with the last poster then you need at least a couple of inches of clearence at the back for cables etc.

> **IntuitiveNipple said:**
> Yes, I'm on the linux-dvb mailing list and seen a few reports of Nova-T disconnects with the latest builds. It looks like it is solvable if it occurs though.

Seem to be, in case you haven't seen this post this is meant to be a workaround for the problem.  I haven't tried it myself though.

[http://www.linuxtv.org/pipermail/linux-dvb/2008-March/024322.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-March/024322.html)

> **IntuitiveNipple said:**
> On that basis I've added a 2.8Gz 5600+ to the list as an option. It sounds as if one of the issues is how good the libraries the player uses are, and again that is solvable.

The fast the better in my experience!

> **IntuitiveNipple said:**
> My expectation is that in a year or so accelerator products might become available so if he finds himself wanting to watch a lot of Blue-Ray movies there may well be a solution longer term.

> **IntuitiveNipple said:**
> I considered that, but wanting it to be future-proof now I thought the LiteOn is a good choice since it is relatively inexpensive and covers all the formats from CD through DVD to HD/Blue Ray, and can write CD/DVD too.

I suspect it will be longer myself.  As a minimum Nvidia will need to release new drivers and there will need to be substantial backend work to support accelerated graphics.

Depends if your dad is likely to want to watch bluray movies.  One 'solution' would be to dual boot into Windows so that accelerated graphics could be used.

I've been toying with this myself as I have finally treated myself to a HDTV.  My current thoughts (which are getting off topic!) are by the time I have bought a windows and powerdvd licence and the bluray drive I might as well buy a PS3.  At least that way it will work out of the box.

> **IntuitiveNipple said:**
> Yes, updates and remote management is part of the plan. My question was more about the programme guides since I noticed in the USA the need for Schedules Direct.

You dad will love the media PC.  I'm really glad I decided to build one personally.



Utar

---

### Post by IntuitiveNipple on 2008-03-27
> **utar said:**
> Depends if your dad is likely to want to watch bluray movies.  One 'solution' would be to dual boot into Windows so that accelerated graphics could be used.

He doesn't even own DVDs yet and he keeps talking about buying a video recorder :)

It's a Windows-free zone so there'll be no dual-booting. 

I think as the Nouveau drivers move along more functionality will appear. Once enough hardware information is documented other developers like myself have the opportunity to add accelerator functionality.

It looks as if this specification is pretty much okay - at least I've not had any negative responses so far.

---

