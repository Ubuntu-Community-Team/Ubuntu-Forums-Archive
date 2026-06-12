---
title: "New Myth box spec"
date: 2009-01-27
forum: Mythbuntu
---

### Post by canoemoose on 2009-01-27
Hello!
I'm currently speccing up a Myth box, and just wanted to run what I've come up with past the rest of you just to make sure I've not done anything stupid.  Here goes:

```
Antec Fusion Remote case
Antec 430w ATX PSU
Asus M2n68-AM motherboard
AMD Athlon X2 4850e 2.5GHz processor
500GB hard drive for recordings
80GB hard drive for OS and stuff
DVD drive
2GB Kingston RAM
WinTV Nova-T 500 TV card
Zotac 8400GS 512MB graphics card

```

It's being linked to a standard definition (PAL) CRT TV via SCART at the moment (I'm getting a s-video to SCART adapter), with plans to get a better screen in the future.

I'm in the UK, so any comments from other people here would be especially interesting, especially about the interactive (red button) service - Does this work with MythTV??

I also have the (interesting) problem of interfacing the old video player to the new setup.  I'd prefer to interface the video machine to the Myth box so I can convert the video stuff to DVD or whatever.  I have an old analogue TV card out of a machine I made my server from so I could use that and use the video machine's ability to modulate the signal to appear as a TV channel I suppose. Any better ideas??

When I'm happy I've got everything right on paper the fun bit starts - boxes of bits everywhere!!  I'll probably post again then about partition sizes, types and mount points.

Cheers for now and sorry about the long post,
Canoemoose

EDIT: Does anyone know if the iMon display on the case has a WiFi adapter built in??  I seem to remember reading somewhere it had but I can't find it any more.  Am I going mad??

---

### Post by zzztownsend on 2009-01-27
can't comment on the rest but I've been fighting with the nova t 500 for 18 months now. It is now reliable and and I would recommend as a good buy

the nvidia driver for the 8400 series card is good for VGA out. But the SVIDEO out works OK but the display is too big for the screen (if that makes sense) so the edge of the display can't be seen (open source VESA driver scale is OK but poor performance jerky video etc). This can be corrected in mythfrontend setup, but not for desktop - apps and places menu etc not visible.

others may be able to suggest if SVIDEO out works properly on other cards in PAL-I UK !!

cheers

Matt

---

### Post by canoemoose on 2009-01-27
> **zzztownsend said:**
> can't comment on the rest but I've been fighting with the nova t 500 for 18 months now. It is now reliable and and I would recommend as a good buy

the nvidia driver for the 8400 series card is good for VGA out. But the SVIDEO out works OK but the display is too big for the screen (if that makes sense) so the edge of the display can't be seen (open source VESA driver scale is OK but poor performance jerky video etc). This can be corrected in mythfrontend setup, but not for desktop - apps and places menu etc not visible.

others may be able to suggest if SVIDEO out works properly on other cards in PAL-I UK !!

cheers

Matt
Cheers for your quick reply!  Can the graphics card issue not be resolved in Xorg.conf??

What about the red button stuff? More out of interest than anything.

---

### Post by canoemoose on 2009-01-28
Right.  I think I confused myself with the iMon display WiFi adapter - I've not been able to find anything about it anywhere.  I have, however, been able to find [this]("http://www.abit.com.tw/page/en/multimedia/multimedia_detail.php?pMODEL_NAME=AirPace+Wi-Fi&fMTYPE=AirPace+Family") so I thought it'd do instead.  Howver, this leaves me with no expansion slots for future upgrades (Graphics card in PCI-e big slot, NIC in PCI-e x1, Digital TV card in PCI 1, Analogue TV card in PCI2 for video machine interfacing) but I suppose this can't be helped.

Does anyone know if the nvidia S-Video issue is only applicable to 8400 series cards??  If so I could use [this]("http://www.ebuyer.com/product/129792") - What does anyone think??

Cheers
Canoemoose

---

### Post by zzztownsend on 2009-01-28
played with xorg.conf for a long time before coming to the conculsion that the nvidia proprietary driver does not accept manual modelines 

see nvnews.net for forums on nvidia cards - there's a linux section. the nvidia linux driver developers occasionally post there, and read forums as informal bug reports.

I haven't got teletext or 'red-button' working on the nova-t-500 but I haven't tried very hard either.
I think the red button tv channel content is available just by changing to the relevant channels. eg 301, 302, 303 etc

cheers

matt

---

### Post by canoemoose on 2009-01-28
> **zzztownsend said:**
> played with xorg.conf for a long time before coming to the conculsion that the nvidia proprietary driver does not accept manual modelines 

see nvnews.net for forums on nvidia cards - there's a linux section. the nvidia linux driver developers occasionally post there, and read forums as informal bug reports.

I haven't got teletext or 'red-button' working on the nova-t-500 but I haven't tried very hard either.
I think the red button tv channel content is available just by changing to the relevant channels. eg 301, 302, 303 etc

cheers

matt
Cheers!  I'll go and have a look.  I suppose if I couldn't get it to work "properly" I could always administrate the box via ssh or remote sessions or something.

---

### Post by canoemoose on 2009-01-30
OK.  The spec I think I've settled on is as follows:

```
Antec Fusion Remote case
Antec 430w ATX PSU
Asus M2n68-AM motherboard
AMD Athlon X2 4850e 2.5GHz processor
500GB hard drive for recordings
80GB hard drive for OS and stuff
DVD drive
2GB Kingston RAM
WinTV Nova-T 500 TV card
XFX GeForce 7200GS graphics card (256 MB, but will grab another 256 MB from RAM if needed)
Abit Airpace WiFi card
```

I'll probably chuck an old analogue Hauppauge TV card I have lying around into it to connect the video machine to; from memory the card has video inputs as well as RF ones.

As before, shout if you think I've done something stupid!

--
Cheers
Canoemoose

---

