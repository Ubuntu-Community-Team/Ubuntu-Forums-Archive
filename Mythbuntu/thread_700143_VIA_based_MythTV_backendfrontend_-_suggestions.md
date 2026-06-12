---
title: "VIA based MythTV backend/frontend - suggestions?"
date: 2008-02-18
forum: Mythbuntu
---

### Post by JGJones on 2008-02-18
MythTV Server with frontend

Dear all,

I am looking at building a Mythubuntu backend/frontend setup for at home and have decided on the following system:

Mini-ITX motherboard:

EPIA EX 15000G - with 1.5GHz VIA C7 CPU and CX700M2 chipset
(This does come with hardware decoder for MPEG2/4 and WMV9 so the processor grunt isn't an issue here)

Comes with a single DVI output (no HDMI) but means it's capable of 1080p HD (the hardware decoder can do this)

For the geekiness factor here's the specification of board:

> Specifications: 1.5GHz C7 CPU; CX700M2 chipset; Supports up to 1GB on 240-pin DDR2 533 DIMM socket; 6 channel audio (VIA VT1708A High Definition Audio Codec); VIA UniChrome™ Pro II 3D/2D AGP graphics with MPEG-2/4 and WMV9 video decoding acceleration.

Rear Panel Connectors: DVI connector; RJ45 10/100 LAN; 2x USB 2.0; miniDIN for S-Video output; 1x Triple RCA jack for composite video and stereo audio outputs; 1x Triple RCA jack for component video output; S/PDIF coaxial connector; S/PDIF optical connector.

Board pin headers and connectors: Headers for additional 4x USB 2.0 ports on 2x connectors; 1x Firewire 1394; Front-panel audio header (HP-out and MIC-in); Audio Line-in; LPC; LVDS connector to support 1-CH LVDS panel; Video pin connector for VGA output; CCIR656/601 video input and SMBUS; PS2 mouse/keyboard header; 1x IDE 66/100/133; 2x SATA connectors; 2x Fan pin connectors for CPU and System fans; 20 pin ATX power connector; PCI Slot.

Additional parts that I would purchase to go with the board above:

1GB RAM
HDD (size to be decided - might be 500GB)
Compact Flash to SATA adaptor (boot Mythubuntu off a Compact Flash)
Slot loading DVDRW suitable for case below
Hoojum cubit3 case (this can be bought in case only from Scan) 

As the board comes with a single PCI card, this would be obviously the TV tuner. I'm from the UK and use Freeview so I'm looking for a suitable DVB-T card, preferly dual tuner if the board can support this - what's a good recommended card?

The reason I have gone with a VIA hardware is that I am keen to reduce power consumption - VIA CPU's use very little power - I'll rather not run a 300-400W PC all the time under the TV where it wouldn't use much power. This is another reason why I am looking to boot it up from the Compact Flash - allows to have HDD use minimal power until it's needed - for this, I'll probably have no swap partition (especially not on Flash!) however must I need swap? Not a problem if i do, will set it on HDD.

This would be a backend server as well as used as the primary frontend. The other frontends are a multiple of laptop's - usually at most 2 other frontends are used at the same time, but most of the time it's just 1.

Any issues I might get with the hardware above? Or should I switch instead to a more powerful dual core based system?

As you all might know - there isn't any HD content on Freeview so the lack of HDMI is not an issue (plus there's no support for HDCP on Linux anyway so that rules out Blueray players for the meantime). However the times where I might play HD content would be directly from a MPEG2/4 file but I have no HD TV's so again not an issue.

Anyway questions:

[LIST]
[*]Recommended DVB-T card - preferly dual tuner with decent signal pickup
[*]Can the VIA cope with multiple incoming streams (if using dual tuner card)?
[*]Can the VIA cope with multiple frontends (1 or 2 at most?) - bear in mind it's not HD content mainly
[*]BUT if using HD content (ie from MPEG4 file) and streaming to other frontend - can it cope?
[*]err...that's it for now :D
[/LIST]

Cheers

---

### Post by foxbuntu on 2008-02-20
I can't say much for DVB-T cards, however:

1) Multi incoming streams shouldn't be an issue, this will depend on the DVB-T card and if its a hardware encoder or not, RAM speed, and HDD Speed

2) Multiple frontends again should not be an issue with SD content, but 1 or 2 should be a max, the CPU you listed above will strugle with that much traffic if are running all streams across your network, wired better than wifi

3) The processor and board listed above would be under powered to handle any HD content, HD Playback comsumes many CPU cycles and I would suggest a high power processor for any HD playback or recording

---

### Post by ozybushwalker on 2008-02-20
I have a mini ITX board with a CLE-266 video controller and VIA C3 1GHz CPU. This copes with playback of PAL SD digital TV comfortably.

I suspect your configuration would probably cope comfortably with HDTV IF there is a suitable driver supporting the MPEG hardware acceleration of the chipset.

[_This page_]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats") suggests the OpenChrome drivers don't support the hardware acceleration of the CX700M2 for HDTV resolution.

I don't know if the Unichrome driver (see [_this page_]("http://unichrome.sourceforge.net/")) 
supports HDTV resolution with the MPEG hardware of the CX700M2.

Concerning DVB cards, I have had good results with the DVB portions of the Leadtek Winfast DTV-1000T and DTV-2000H. (Both cards have an analogue TV capture function but I haven't used them.) There is an incomplete list of supported DVB cards at [_this page_.]("http://www.linuxtv.org/wiki/index.php/DVB-T_Devices")

The MiniMyth distribution (see [_this page_]("http://www.linpvr.org/")) is specifically oriented towards Mini ITX systems without a hard drive.

---

### Post by david_f1976 on 2008-02-21
I used to have the Hauppauge Nova T-500 which is a dual DVB tuner. Unfortunately, I had issues picking up all of the channels. I have since switced to the plain single-tuner Nova T (which has a more sensitive tuner)  and receive a much better signal and all channels. If your freeview reception is good enough you may be able to get away with the 500.

As for your general choice of hardware it might be worth considering going up to Micro-ATX if you can afford the space. There will be much more processing power there and with modern components and possibly some undervolting you should be able to bring the whole system in at a similar power draw. It would also give you more PCI slots for tuners.

For example one of my Mythtv frontends is a VIA SP800 (in a hoojum case by the way - good choice if you do go round this route) with 512mb ram, a 2.5" hard drive and a laptop optical drive it consumes about 30W at idle. I've never seen it go above 40W.

Compare this with my desktop micro-ATX system which has a laptop core 2 duo processor, 2gb ram, a 2.5" hard drive and a full-sized optical drive. This system is nigh on silent, draws a similar idle load to my VIA setup and even on full stress draws <70 W. Although this was an expensive setup the new AMD low power processors will get you close to this at a fraction of the price (and cheaper than your VIA board as well). Check out the forums at [www.silentpcreview.com](www.silentpcreview.com) for more information if you're interested.

---

### Post by JGJones on 2008-02-25
I've just noticed this article which might benefit anyone looking at building a low power PC (ideal for use as HTPC where you do want low power if using it for long times)

[http://arstechnica.com/guides/buyer/guide-200802-green.ars](http://arstechnica.com/guides/buyer/guide-200802-green.ars)

Cheers

---

### Post by norrisj on 2008-02-26
Yes, very interesting article, 14-25W under load, pretty good.

So would the board be suitable for a backend-only system?  I have a mac-mini Core2 for my front-end and I'm looking into low-power "always on" setups for the backend.  My main concern is the CPU-power needed to store/transmit/decode HD content, which is highlighted above, but I assume it is mostly the front-end taking this load?

James

---

### Post by SteveGodfrey on 2008-06-20
Did you get anywhere with this? I'm looking at getting the new MSI Titan to used as a combined backend/frontend. I'm a little concerned as the VIA driver support seems pretty poor.

Thanks



> **JGJones said:**
> MythTV Server with frontend

Dear all,

I am looking at building a Mythubuntu backend/frontend setup for at home and have decided on the following system:

Mini-ITX motherboard:

EPIA EX 15000G - with 1.5GHz VIA C7 CPU and CX700M2 chipset
(This does come with hardware decoder for MPEG2/4 and WMV9 so the processor grunt isn't an issue here)

Comes with a single DVI output (no HDMI) but means it's capable of 1080p HD (the hardware decoder can do this)

For the geekiness factor here's the specification of board:



Additional parts that I would purchase to go with the board above:

1GB RAM
HDD (size to be decided - might be 500GB)
Compact Flash to SATA adaptor (boot Mythubuntu off a Compact Flash)
Slot loading DVDRW suitable for case below
Hoojum cubit3 case (this can be bought in case only from Scan) 

As the board comes with a single PCI card, this would be obviously the TV tuner. I'm from the UK and use Freeview so I'm looking for a suitable DVB-T card, preferly dual tuner if the board can support this - what's a good recommended card?

The reason I have gone with a VIA hardware is that I am keen to reduce power consumption - VIA CPU's use very little power - I'll rather not run a 300-400W PC all the time under the TV where it wouldn't use much power. This is another reason why I am looking to boot it up from the Compact Flash - allows to have HDD use minimal power until it's needed - for this, I'll probably have no swap partition (especially not on Flash!) however must I need swap? Not a problem if i do, will set it on HDD.

This would be a backend server as well as used as the primary frontend. The other frontends are a multiple of laptop's - usually at most 2 other frontends are used at the same time, but most of the time it's just 1.

Any issues I might get with the hardware above? Or should I switch instead to a more powerful dual core based system?

As you all might know - there isn't any HD content on Freeview so the lack of HDMI is not an issue (plus there's no support for HDCP on Linux anyway so that rules out Blueray players for the meantime). However the times where I might play HD content would be directly from a MPEG2/4 file but I have no HD TV's so again not an issue.

Anyway questions:

[LIST]
[*]Recommended DVB-T card - preferly dual tuner with decent signal pickup
[*]Can the VIA cope with multiple incoming streams (if using dual tuner card)?
[*]Can the VIA cope with multiple frontends (1 or 2 at most?) - bear in mind it's not HD content mainly
[*]BUT if using HD content (ie from MPEG4 file) and streaming to other frontend - can it cope?
[*]err...that's it for now :D
[/LIST]

Cheers

---

### Post by lytke on 2008-06-25
Hi

I've got an EX10000 board (same as EX15000 - without fan) laying in a box - forget about getting x up and running with std. 8.04 installation. :(

Got x up and running with 7.10 and complied drivers from viaarena.com - but live tv was slow motion

On the other hand I have an ASUS matx board with an underclocked low power AMD using approx 65watt with good responce when using the remote :)

---

