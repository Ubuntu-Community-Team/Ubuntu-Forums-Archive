---
title: "apps. to see TV"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by ShirishAg75 on 2006-07-21
Hi all,
       What apps. are there to see the TV? AFAI see MythTV is something equivalent to Media Centre kinda thing. Although I don't know what functionality it provides. My requirements are simple, first & foremost I should be able to watch TV & secondly, perhaps at a little later date to do some recordings in mpg4 with the CPU doing the stuff. O.k. I don't wanna get into compiling stuff or something like tht. Are there some nice/stable apps. for this at the moment or have I asked something 6 months earlier? 
              Thnx in advance.

---

### Post by catlett on 2006-07-21
I use TV Time. It is a basic tv viewer. I habe a winpauge tv card. TV Time is in the repositories. Just open Synaptic Package Manager and enter it's name in the search field, 
This is synaptics description
> A high quality television application
tvtime is a high quality television application for use with video
capture cards.  tvtime processes the input from a capture card and
displays it on a computer monitor or projector.  Unlike other
television applications, tvtime focuses on high visual quality making
it ideal for videophiles.

tvtime supports:
 * Deinterlaced output at a full interlaced rate of 59.94 frames per
   second for NTSC source, or 50 frames per second for PAL sources.
   This gives smoothness of motion and high visual quality.
 * Multiple deinterlacing algoritms for finding the optimal mode for
   your video content and available processor speed.
 * 16:9 aspect ratio mode for the highest available resolution when
   processing input from an external DVD player or digital satellite
   receiver.
 * A super-slick on-screen-display for the complete television
   experience, with a featureful menu system.
 * 2-3 Pulldown detection for optimal quality viewing of film content
   from NTSC sources.

You can find more information at [http://tvtime.net/](http://tvtime.net/)

---

### Post by ShirishAg75 on 2006-07-21
Thnx catlett,
                 although I've been able to successfully install tvtime, lirc as well as xmltv-utils all the 3 which were suggested but now comes how to configure the damn thing.
         The card has a SAA7130 chipset which is recognised by the kernel. Below is the lspci output :-

> 0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
**0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)**
**0000:03:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)**
0000:03:02.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)
0000:03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:03:07.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)


   I have put both the audio card i.e. i810 as well as the philips details in bold in case if tht provides something. 
          Now comes the big-roadwinding thing to configure stuff. For starters I don't know if I get PAL-B, D or K or what? How do I found out?

           The card works perfectly in XP, is there something there which could be used to know what things & how they can be configured ?

           Lastly found the tvtime site to be bit confusing hence asking here. Thnx in advance.

---

