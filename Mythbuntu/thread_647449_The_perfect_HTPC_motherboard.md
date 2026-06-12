---
title: "The perfect HTPC motherboard?"
date: 2007-12-22
forum: Mythbuntu
---

### Post by theacoustician on 2007-12-22
[http://usa.asus.com/products.aspx?l1=3&l2=11&l3=584](http://usa.asus.com/products.aspx?l1=3&l2=11&l3=584)

It has HDMI out onboard and promises "Full HD 1080p Multimedia Home-Theater Entertainment".  My question is does anyone have any experience with the board?  Are there proper drivers available?  I'd love to hear from any owners as I'm seriously considering nabbing this for a Myth client.

---

### Post by tgalati4 on 2007-12-22
Do some research.  Most motherboards can't support true 1080p throughput.  You can record and playback at compressed settings, but expect jerky performance with playback of true 1080p programs.  Unless this board drops legacy motherboard architecture and has only the latest throughput architecture, beware of 1080p advertising.

Many TV cards can handle 1080p but the busses that they plug into barely manage it.

For the time and money that you spend, it makes better sense to buy a $300 blueray player and rent Netflix for HD content.

Link didn't work for me, so I can't comment on this specific board.

---

### Post by theacoustician on 2007-12-23
> **tgalati4 said:**
> Do some research.
I already did.  The board is so new that the only reviews out there are from sites concerning themselves with high end gaming and assuming you're using Windows.  Hence, I came asking here hoping for more relevant commentary.

> **tgalati4 said:**
> Most motherboards can't support true 1080p throughput.  You can record and playback at compressed settings, but expect jerky performance with playback of true 1080p programs.I'm not sure what you're talking about here exactly.  I have a year old Dell workstation at my place of employment with a 2.4 GHz C2D and a 7900GT that handles 1080p material all the live long day with no issues.  I'm sorry you haven't had the pleasure of being able to experience it for yourself.

> **tgalati4 said:**
> Many TV cards can handle 1080p but the busses that they plug into barely manage it.Once again, I'm unsure of what you're trying to say here, since no broadcaster on Earth broadcasts in 1080p.  It was only just added under the DVB-S2 standard and just now being experimented with by European stations.  ATSC hasn't been amended for it, so its a complete no go in North America currently.

> **tgalati4 said:**
> For the time and money that you spend, it makes better sense to buy a $300 blueray player and rent Netflix for HD content.You understand that almost every BR player out there is profile 1.0, right?  100% of the "$300" players are 1.0.  With the uptake of profile 1.1 being manditory after November 1, you risk owning a $300 brick as there's no guarentee that profile 1.1. discs will play correctly on 1.0 players.  That coupled with the fact that I'm not exactly keen on the idea of allowing Sony the right to flash the firmware on my player whenever they see fit (review the BD+ specification if you don't believe me), I wouldn't say that it makes better sense for me personally.

> **tgalati4 said:**
> Link didn't work for me, so I can't comment on this specific board.Sorry about that.  Asus website seems to have slowed for me, so perhaps they're having server issues.  The board is the Asus P5E-VM HDMI.  Here is a link to it at Newegg: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237)

So back to the original question:
1. Does anyone have the motherboard?
2. What are your experiences with it in Linux, particularly in the HTPC setting?
3. How is the driver support?  Everything working 100%?

---

### Post by brundles on 2007-12-25
I've been looking at this board for the same reason - an onboard HDMI motherboard for HD content on an HTPC. The only reference I've found to it and the HDMI features specifically was on [Phoronix](http://www.phoronix.com/forums/showthread.php?t=6690).

TBH, I'm thinking that as I'll be using the SP/DIF to an amp for audio anyway there's not much benefit of HDMI over DVI-D (unless the board supports HDCP which I'm not sure it does). That said, I haven't yet looked for long enough to find an equivilant board with onboard DVI-D.

*Edit:* It's not the ASUS P5E-VM board, but this [Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=603712&highlight=intel+hdmi) thread indicates difficulties when using the Intel GMA3100 chipset (used by the P5E-VM) over HDMI.

---

### Post by theacoustician on 2007-12-26
> **brundles said:**
> I've been looking at this board for the same reason - an onboard HDMI motherboard for HD content on an HTPC. The only reference I've found to it and the HDMI features specifically was on [Phoronix](http://www.phoronix.com/forums/showthread.php?t=6690).

TBH, I'm thinking that as I'll be using the SP/DIF to an amp for audio anyway there's not much benefit of HDMI over DVI-D (unless the board supports HDCP which I'm not sure it does). That said, I haven't yet looked for long enough to find an equivilant board with onboard DVI-D.

*Edit:* It's not the ASUS P5E-VM board, but this [Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=603712&highlight=intel+hdmi) thread indicates difficulties when using the Intel GMA3100 chipset (used by the P5E-VM) over HDMI.

Interesting links.  Looks like I may wait a bit to see what else is said about the GMA3100 before buying.

I can confirm, however, that all the techincal documentation I've been able to find on the Asus board indicate its HDCP compliant.

---

### Post by tgalati4 on 2007-12-26
My experience is with cable-based HD using an C2D E6750 with 4 GB RAM, on an Intel P35 board with an nVidia 8600 GT (512 MB video RAM), and a Hauppage TV card.

It's true that over-the-air broadcast is only 1080i, but component, analog RGB signals from our cable company are upscaled/deinterlaced and the throughput of most motherboards today can't handle the on-the-fly compression/decompression of these signals without jerkiness, sparklies, or other weirdness.

It seems simpler to me to get a cheaper BlueRay player and rent the movies than try to rely on home-built pc to capture and replay high-def content.  And yes technology changes, look at the 5 flavors of HDMI and the HDCP fiasco.  It's a minefield for the casual consumer to negotiate to get any of this stuff to work.

---

### Post by jpeeters on 2007-12-28
> **theacoustician said:**
> 
Sorry about that.  Asus website seems to have slowed for me, so perhaps they're having server issues.  The board is the Asus P5E-VM HDMI.  Here is a link to it at Newegg: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237)

So back to the original question:
1. Does anyone have the motherboard?
2. What are your experiences with it in Linux, particularly in the HTPC setting?
3. How is the driver support?  Everything working 100%?

I have an Asus P5E-V HDMI board (which is similar to the VM one), and I have some troubles with audio over the HDMI interface. It does work more or less with Open Sound System, but I rather prefer alsa (and use standard ubuntu packages). I filed an ubuntu bug report as well as an alsa bug report, but I did not receive any feedback yet.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/176532](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/176532)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654)

---

### Post by brundles on 2007-12-28
Thanks for that jpeeters. 

What resolution are you running the display at? Did you have any problems with the display over HDMI or did it run out of the box with Gutsy?

---

### Post by jpeeters on 2007-12-28
I am running 1920 x 1080 on a sony kdl-40w3000 (1080p capable). Everything went fine with the standard ubuntu install (except sound output).

---

### Post by theacoustician on 2007-12-29
> **jpeeters said:**
> I have an Asus P5E-V HDMI board (which is similar to the VM one), and I have some troubles with audio over the HDMI interface. It does work more or less with Open Sound System, but I rather prefer alsa (and use standard ubuntu packages). I filed an ubuntu bug report as well as an alsa bug report, but I did not receive any feedback yet.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/176532](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/176532)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654)

No audio over HDMI isn't a deal breaker for me as long as it really displays at 1920x1080 and can be made to play video at that res.  Are you saying ALSA doesn't work at all or just doesn't work with audio over HDMI?  That might affect things some.  Did you try the Linux drivers on ASUS's website (under the Other category)?  Overall, would you recommend the board or suggest holding off till development progresses further?

---

### Post by brundles on 2007-12-29
Hopefully jpeeters will confirm, but assuming the audio chip is the same one on the P5B boards then it should be fine. For me, initially the audio will go over the old fashioned 3.5mm jack but will then be shifted to the S/PDIF. Both of these work perfectly well on the P5B board with ALSA so I'm assuming they will here too on the P5E.

---

### Post by jpeeters on 2008-01-01
Audio works, at least through the 3.5mm jack. I did not try S/PDIF yet. The board is working great overall!

---

### Post by GLMontyWV on 2008-01-02
Not to drift the thread too much but how would this board compare on video output, not sure I understand all those specs.

ASRock ALiveNF7G-HDready 
[http://www.asrock.com/mb/overview.asp?Model=ALIVENF7G-HDREADY](http://www.asrock.com/mb/overview.asp?Model=ALIVENF7G-HDREADY)

Graphics - Integrated NVIDIA® GeForce7 Series (NV44)
- DX9.0 VGA, Pixel Shader 3.0
- Max. shared memory 256MB
- Dual VGA Output: support DVI-D and D-Sub ports by independent display controllers
- Supports HDCP function with DVI-D port
- Supports 720p Blu-ray (BD) / HD-DVD playback
- NVIDIA® PureVideo™ Ready 
Audio - 7.1 CH Windows® Vista™ Premium Level HD Audio (ALC888 Audio Codec)
- Chipset embedded HDMI Audio 

HDMI_SPDIF header, providing SPDIF audio output to HDMI VGA card, allows the system to connect HDMI Digital TV/projector/LCD devices.
Chipset embedded HDMI Audio which supports HDMI signal through DVI-D port by using DVI to HDMI adapter (not bundled)
7.1 CH Windows® Vista™ Premium Level HD Audio (ALC888 Audio Codec)

Came real close to doing my build this weekend on this board and at the last minute switched to a Gigabyte board to get a few more PCI slots.  Maybe I'll use it for my next one.

Thanks, Monty

---

### Post by brundles on 2008-01-04
I suspect I already knoiw the answer to this one but can someone confirm whether the LAN port works on this board out of the box?

At the moment I'm not even getting a connection light on the router so I'm wondering if I've got a faulty board :(

*Edit:* Nevermind - it didn't pick it up during the install but after installation everything was good :).

---

### Post by jpeeters on 2008-01-05
The Lan port works out of the box, although not while installing Ubuntu 7.10. You need the atl1 module to get it working.

---

### Post by herodiade on 2008-01-05
brundles, or jpeeter : do you finally have tested Linux on an Asus P5E-VM HDMI ?

I'm looking to buy one, bug I've a couple of question :
- Does the BIOS support activating AHCI mode for Sata links ? (settings for this, if any, should be on the "Sata configuration" tab)
- Is the graphic controller already supported by Ubuntu ? at least for accelerated 2D (not vesa) ? if not by Gutsy, at least by Hardy ?

The xf86-video-intel/README documentation stop the "supported chipset lists" at G33, so it's very unclear wether G35 (GMA X3500) graphic chipset is somehow supported by the lastest intel xorg drivers.

---

### Post by brundles on 2008-01-05
> **herodiade said:**
> brundles, or jpeeter : do you finally have tested Linux on an Asus P5E-VM HDMI ?

I'm looking to buy one, bug I've a couple of question :
- Does the BIOS support activating AHCI mode for Sata links ? (settings for this, if any, should be on the "Sata configuration" tab)
- Is the graphic controller already supported by Ubuntu ? at least for accelerated 2D (not vesa) ? if not by Gutsy, at least by Hardy ?

The xf86-video-intel/README documentation stop the "supported chipset lists" at G33, so it's very unclear wether G35 (GMA X3500) graphic chipset is somehow supported by the lastest intel xorg drivers.

It installs out of the box on Gutsy although there is the quirk with the LAN port as mentioned above. Once it's up and running it's perfectly happy though.

I'm afraid tha AHCI/SATA stuff goes straight over my head so if you might need to elaborate on that so I can work it out for you 

Graphically it does work up to 1360x768 out of the box (on my HD TV anyway) but first go at playing back an x264 shows slight tearing. I've yet to play with newer graphics drivers (I've not even checked the restricted drivers yet) and stuff (there's a Gutsy package for the new Intel X.org bulid on another thread I'm looking at trying). 

In terms of Hardy, I'm after a stable system that won't get updated much when it's done so I'm not using the current builds of that I'm afraid.

Gotta run now but will update later.

---

### Post by herodiade on 2008-01-05
> **brundles said:**
> It installs out of the box on Gutsy although there is the quirk with the LAN port as mentioned above. Once it's up and running it's perfectly happy though.

I'm afraid tha AHCI/SATA stuff goes straight over my head so if you might need to elaborate on that so I can work it out for you 

Graphically it does work up to 1360x768 out of the box (on my HD TV anyway) but first go at playing back an x264 shows slight tearing. I've yet to play with newer graphics drivers (I've not even checked the restricted drivers yet) and stuff (there's a Gutsy package for the new Intel X.org bulid on another thread I'm looking at trying). 
.

Many thanks for the information. So the Intel G35 / GMA X3500 chipset is supported by xorg in Gutsy, that's a great news ! The network driver glitch during install seems minor to me.

AHCI [1] is a mode that expose all pure SATA features, like hotplug and NCQ (native command queuing), and unlike the "PATA/IDE compatible mode" aka "legacy mode" (which hide those advanced features for the sake of backward compatibility).  Moderns Intel SATA chipsets (like this one's ICH9) support AHCI, and also support the old IDE compatibility mode; the SATA operating mode (either AHCI or IDE) is usually configurable in the BIOS (but not always, hence my question).

In Linux (since 2.6.19), the AHCI drivers got factored out from the traditional PATA drivers to benefit code simplification and large quality improvments in libata; it has been worked on Alan Cox, Tejun Heo and Jeff Garzig : the new driver is very clean and stable [2].  So on Linux, if your BIOS has SATA configured to work on AHCI mode, you'll benefit this excellent driver (and hotplug and NCQ), while if the BIOS is configured for IDE mode, Linux will use the ata_piix driver (less good).

Windows Vista also support SATA chipsets configured in AHCI mode. But not Windows XP (lack of proper driver); that's why most moderns BIOS have an option to configure the SATA controllers in legacy/IDE mode or modern/AHCI mode : to keep compatibility with Win XP if needed. But some motherboard manufacturers don't provide the option to enable AHCI, they just fix the operating mode to legacy/IDE: it will always work (even for XP), but suboptimally.
  
I've found a picture of the Asus P5E-VM HDMI BIOS' main menu [3]. If you enter the "SATA Configuration" submenu on this, there should be a submenu named "Configure SATA as", and giving the options "IDE" and "AHCI". If yes: bingo, AHCI is supported. If the menu is not there, well... it's not supported.
  
Last question (sorry, I can't refrain ! I'm excited now you've proved that the graphic chipset works !) : does suspend-to-ram (aka "sleep") works too ?

Thanks again.
  
[1] [http://en.wikipedia.org/wiki/AHCI](http://en.wikipedia.org/wiki/AHCI) 
[2] [http://linux-ata.org/driver-status.html](http://linux-ata.org/driver-status.html)
[3] [http://resources.vr-zone.com/yantronic/p5evm/bios/main.png](http://resources.vr-zone.com/yantronic/p5evm/bios/main.png)

---

### Post by jpeeters on 2008-01-06
> **herodiade said:**
>  
I've found a picture of the Asus P5E-VM HDMI BIOS' main menu [3]. If you enter the "SATA Configuration" submenu on this, there should be a submenu named "Configure SATA as", and giving the options "IDE" and "AHCI". If yes: bingo, AHCI is supported. If the menu is not there, well... it's not supported.



AHCI is supported and works very well. The only thing that does not work yet is audio over the hdmi interface (with alsa that is, oss works but adds noise to the signal).

Another thing I want to get working is dual core ffmpeg support. Some demo 1080p titles are stuttering, as only 'one' cpu is used at 100% and the other one is idle...

---

### Post by brundles on 2008-01-06
> **jpeeters said:**
> AHCI is supported and works very well. The only thing that does not work yet is audio over the hdmi interface (with alsa that is, oss works but adds noise to the signal).

Another thing I want to get working is dual core ffmpeg support. Some demo 1080p titles are stuttering, as only 'one' cpu is used at 100% and the other one is idle...

Did you have to do anything to get Compiz running? I've only just started looking at it, but it seems to be running glx by default and picked up the graphics as the 965 rather than the G35.

*Edit:* Nevermind (again!). SKIP_CHECKS fixes that - and it doesn't seem to suffer from the media player crashes when using that that have been reported on other cards. What is beginning to annoy me is the tearing though.

jpeeters - Have you had any problems with tearing eithe rduring video playback (x264 in my case) or when dragging windows around with compiz fully enabled and the wobbly windows on?

---

### Post by jpeeters on 2008-01-07
I did not try compiz, so I can't say anything about it. I don't see tearing either  :) But I have to say that I still need to place the system in 'production', I currently only use it for some tests...

---

### Post by brundles on 2008-01-07
> **jpeeters said:**
> I did not try compiz, so I can't say anything about it. I don't see tearing either  :) But I have to say that I still need to place the system in 'production', I currently only use it for some tests...

I'm hoping that the pending update for the Intel drivers (2.2.1 is due out soon) will address some of the issues - it's been [reported that it will address the xv related crashes](http://www.phoronix.com/vr.php?view=NjI0Nw) which will be a good start.

jpeeters - Are you using an HDMI cable from the PC or DVI-D through the HDMI adapter? I swapped from the VGA - DVI-I connection to HDMI - DVI-D via the adapter and now get nothing when it should go to the desktop environment. The Ubuntu loading screen is fine (kind of) but nothing after that.

---

### Post by herodiade on 2008-01-08
Ok, here is a list of all the bugs or small glitches I found regarding this Asus P5E-VM HDMI motherboard on Linux as of now (I can't test any fix for them, nor fill bug proper bug reports since I didn't bought this motherboard yet). Most of those bugs are confirmed from multiple sources.

* Attansic L1 ethernet driver doesn't support TSO. This affects performance (and maybe stability). The driver's maintainer has proposed a patch for testing, but still wait for any tester feedback (so please, if you have one, give it a run). See here: [http://sourceforge.net/mailarchive/forum.php?thread_name=20071211214616.6c1ff27e%40osprey.hogchain.net&forum_name=atl1-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20071211214616.6c1ff27e%40osprey.hogchain.net&forum_name=atl1-devel)

* Attansic L1 ethernet driver doesn't support 64 bits DMA (only 32bits).  This is a know problem, that could have bad consequences if you use your machine in 64 bits mode with more than 4 Go RAM, but there's a workaround in recent kernels, See [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=5f08e46b621a769e52a9545a23ab1d5fb2aec1d4](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=5f08e46b621a769e52a9545a23ab1d5fb2aec1d4) and [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=cdcc520d7b73445c3552a70786afed9a2b22c010](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=cdcc520d7b73445c3552a70786afed9a2b22c010)

* Attansic L1 ethernet driver (atl1 module) on the Ubuntu Gutsy install CDRom is either affected by one of the above or is (more probably) simply missing from the CDRom's install kernel. So the network  driver misses during installation. The default Gutsy *installed* kernel has the driver properly installed and working though. See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149147](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149147)

* hda intel - ALC833 : the digital audio output over HDMI is not yet supported by alsa under Linux (the oss driver seems to work, though, and the analog output works fine with alsa). This has been reported both in alsa's bugtracker and on xorg-devel mailing-list. Keith Packard (intel xorg driver lead developer) stated that support for this would need lot of work, involving both alsa and xorg developers, and needing changes in the modsetting kernel driver (DRM). So it will take time. See [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654) and on xorg ml : [http://lists.freedesktop.org/archives/xorg/2008-January/031674.html](http://lists.freedesktop.org/archives/xorg/2008-January/031674.html) . There's also an Ubuntu launchpad bug : [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/176532](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/176532) . So for now, none of the Intel's IGP does support digital audio over HDMI using alsa on Linux.

* G35 / GMA X3500 xf86-video-intel driver produce tearing when playing h264 over HDMI. A bug has been reported the xorg mailing-list: [http://lists.freedesktop.org/archives/xorg/2008-January/031732.html](http://lists.freedesktop.org/archives/xorg/2008-January/031732.html) and on xorg bugtracker, and is still open: [http://bugs.freedesktop.org/show_bug.cgi?id=11311](http://bugs.freedesktop.org/show_bug.cgi?id=11311)

* G35 / GMA X3500 xf86-video-intel driver does not recognize the DVI output, when using the HDMI-to-DVI converter supplied with the motherboard. Or the converter may be flawed. Or this could be an HDCP related problem. But the converter seems to works correctly (since the display over DVI work while booting, when in console/fb, and when using xorg's vesa driver (but not the xorg's intel driver)). Displaying over direct HDMI (without DVI conversion) works fine too. The bug is present in xf86-video-intel 2.1.1 release (ie. as in Gutsy) as well as in january 06 2008 git head (according to kdekorte on #xorg IRC channel yesterday), and with the driver in Fedora Core 8 as well.  This problem has been reported on this thread and on xorg mailing-list (see here [http://lists.freedesktop.org/archives/xorg/2008-January/031599.html](http://lists.freedesktop.org/archives/xorg/2008-January/031599.html) ).  A bug had been reported in Xorg's bugtracker : [https://bugs.freedesktop.org/show_bug.cgi?id=13968](https://bugs.freedesktop.org/show_bug.cgi?id=13968) (but may not be fixed before the imminent intel driver 2.2.1 release that should be included in Ubuntu Hardy).

* Compiz blacklists the graphic chipset/drivers (this can be workarounded with echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager). In Ubuntu Gutsy, this blacklisting system appear to be implemented in compiz-0.6.0+git20071008/debian/compiz-manager, and based on [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) . I don't know if a bug should be reported on Ubuntu's launchpad or in Compiz' bt, but there's already this: [https://bugs.launchpad.net/dell/+bug/140833](https://bugs.launchpad.net/dell/+bug/140833)

Apart those few minor glitches/bugs (well, the non working DVI out problem is more than a minor annoyance, and wait for someone to report a bug here [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/) , and the Attansic L1 patch need a test before 2.6.24 is out), the Asus P5E-VM HDMI motherboard seems working quite well with current Ubuntu Gutsy, and only require free divers. Right ? Oh, did someone tested firewire support ?

Edited on Wed Jan  9 15:49:34 CET 2008 to complete the list and infos.

---

### Post by brundles on 2008-01-08
That's a good summary. 

Something else that should be mentioned is that compiz support isn't really finished yet either. Currently the onboard graphics actually gets reported as a blacklisted card (although you can override this).

Oh, and on the subject of the tearing I think that's down to the xv stability/performance issues which they plan to address in the next Intel driver release (2.2.1)

---

### Post by herodiade on 2008-01-08
> **brundles said:**
> That's a good summary. 

Something else that should be mentioned is that compiz support isn't really finished yet either. Currently the onboard graphics actually gets reported as a blacklisted card (although you can override this).

Oh, and on the subject of the tearing I think that's down to the xv stability/performance issues which they plan to address in the next Intel driver release (2.2.1)

Ah yes, thanks, I forgot about the compiz blacklisting (and the need to set SKIP_CHECKS). This blacklisting system appear to be implemented in compiz-0.6.0+git20071008/debian/compiz-manager, and based on [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) . I don't know if a bug should be reported on Ubuntu's launchpad or in Compiz' bt.

And to keep track of everything here: the "video tearing" problem had been reported on xorg mailing-list too, here : [http://lists.freedesktop.org/archives/xorg/2008-January/031732.html](http://lists.freedesktop.org/archives/xorg/2008-January/031732.html) and seems to be a known bug [http://lists.freedesktop.org/archives/xorg/2008-January/031744.html](http://lists.freedesktop.org/archives/xorg/2008-January/031744.html) (I found nothing on fd.o bt though).

**EDIT**: finally, I found the "video tearing" in freedesktop.org bugtracker, and this bug is in NEEDINFO status : [http://bugs.freedesktop.org/show_bug.cgi?id=11311](http://bugs.freedesktop.org/show_bug.cgi?id=11311) (and duplicate of this bug : 
[http://bugs.freedesktop.org/show_bug.cgi?id=12648](http://bugs.freedesktop.org/show_bug.cgi?id=12648) and [http://bugs.freedesktop.org/show_bug.cgi?id=12633](http://bugs.freedesktop.org/show_bug.cgi?id=12633) ).

---

### Post by brundles on 2008-01-08
Going back to that HDMI-DVI convertor not working for a second, have you seen any indications of whether a dual link cable would work? I've seen a single mention on Phoronix about it but nothing else. I just wondered if anyone else had seen or tried it before I shell out for the cable.

---

### Post by theacoustician on 2008-01-08
> **herodiade said:**
> 
* G35 / GMA X3500 xf86-video-intel driver does not recognize the DVI output, when using the HDMI-to-DVI converter supplied with the motherboard. The converter seems to works correctly (since the display over DVI workwhile booting and when in console/fb, until xorg is started). Displaying over direct HDMI (without DVI conversion) works fine too. The bug is present in xf86-video-intel 2.1.1 release (ie. as in Gutsy) as well as in yesterday's git head (according to kdekorte on #xorg IRC channel yesterday), and with the driver in Fedora Core 8 as well.  This problem has been reported on this thread and on xorg mailing-list (see here [http://lists.freedesktop.org/archives/xorg/2008-January/031599.html](http://lists.freedesktop.org/archives/xorg/2008-January/031599.html) ).  But no bug report has been made on the xorg bugzilla yet (so no much chance for the bug to be fixed before the imminent 2.2.1 driver's release, and therefore before Ubuntu Hardy release). support ?
I really don't this is correctly presented.  By spec, HDMI 100% backwards compatible with single-link DVI.  A HDMI-DVI converter is a passive component, you can't write a driver for that.  If HDMI is working correctly, then is impossible for DVI to not work.  What is more likely is that the motherboard is HDCP compliant and the monitor is not or the converter is just junk.  If the first is true, then I don't think you'll ever get a proper resolution.  You'd essentially have to strip HDCP.  The second is fixed by buying a better HDMI->DVI adapter.

---

### Post by theacoustician on 2008-01-08
> **brundles said:**
> Going back to that HDMI-DVI convertor not working for a second, have you seen any indications of whether a dual link cable would work? I've seen a single mention on Phoronix about it but nothing else. I just wondered if anyone else had seen or tried it before I shell out for the cable.

No, dual link will not help.

---

### Post by herodiade on 2008-01-09
> **theacoustician said:**
> I really don't this is correctly presented.  By spec, HDMI 100% backwards compatible with single-link DVI.  A HDMI-DVI converter is a passive component, you can't write a driver for that.  If HDMI is working correctly, then is impossible for DVI to not work.  What is more likely is that the motherboard is HDCP compliant and the monitor is not or the converter is just junk.  If the first is true, then I don't think you'll ever get a proper resolution.  You'd essentially have to strip HDCP.  The second is fixed by buying a better HDMI->DVI adapter.

Well, the facts are:
.
* No one managed to get the DVI (through HDMI-to-DVI) output working under xorg using xf86-video-intel driver with this G35 motherboard
* But the console and boot splash/messages displays well through DVI. So 1) the converter is not totally junk, 2) it can minimally work with the tested monitors, 3) the problem depends on the driver used (vesa/framebuffer vs. xorg-intel)
* Someone reported on #xorg IRC having this motherboard's DVI to work with the xorg VESA driver, but not with Intel's driver (same conclusions as above)
* Anyone who tried, got a fine working HDMI connection (straight, without DVI conv) to monitor (so contrary to your saying, we can have a HDMI ok and still DVI not working)
* The G35 chipset is quite new. AFAIK, this Asus P5E-VM is the only G35 based motherboard on the market so far

Given those facts, I find the probability of a bug in intel's xorg driver or kernel's drm with DVI under G35 much more plausible than a problem with the connector or HDCP.

It would be interesting if someone who reported this problem with the Linux driver tested the Asus P5E-VM DVI connection under Windows: if it works, we could say for sure that the converter works and that it's not a compatibility problem with monitors (your two hypothesis), but a plain xorg driver bug. It would also be useful if someone else here could confirm having DVI working with the vesa driver.

Here ( [http://lists.freedesktop.org/archives/xorg/2008-January/031723.html](http://lists.freedesktop.org/archives/xorg/2008-January/031723.html) ), Luc Verhaegen, a radeonhd developer, says that he needs some specification to write support for dvi->hdmi dongles. But anyway, the bug doesn't necessarily have to be related to the HDMI-to-DVI conversion: it could just be a general xf86-video-intel driver problem with DVI on G35 (whether DVI conversion is passive or not, and whether there's any conversion involved or not).  The intel driver's output detection and the kernel drm modsetting are full of conditionals tests/switchs, per chipset, per output type.

G35 is quite new, and not much tested. The problem could be a very trivial bug, like the intel driver not even trying to detect the DVI output in the case of G35 (you know, a "case" missing on a "switch" statement, or something).

---

### Post by theacoustician on 2008-01-09
> **herodiade said:**
> Well, the facts are:
.
* No one managed to get the DVI (through HDMI-to-DVI) output working under xorg using xf86-video-intel driver with this G35 motherboard
* But the console and boot splash/messages displays well through DVI. So 1) the converter is not totally junk, 2) it can minimally work with the tested monitors, 3) the problem depends on the driver used (vesa/framebuffer vs. xorg-intel)
* Someone reported on #xorg IRC having this motherboard's DVI to work with the xorg VESA driver, but not with Intel's driver (same conclusions as above)
* Anyone who tried, got a fine working HDMI connection (straight, without DVI conv) to monitor (so contrary to your saying, we can have a HDMI ok and still DVI not working)
* The G35 chipset is quite new. AFAIK, this Asus P5E-VM is the only G35 based motherboard on the market so far

Given those facts, I find the probability of a bug in intel's xorg driver or kernel's drm with DVI under G35 much more plausible than a problem with the connector or HDCP.

It would be interesting if someone who reported this problem with the Linux driver tested the Asus P5E-VM DVI connection under Windows: if it works, we could say for sure that the converter works and that it's not a compatibility problem with monitors (your two hypothesis), but a plain xorg driver bug. It would also be useful if someone else here could confirm having DVI working with the vesa driver.

Here ( [http://lists.freedesktop.org/archives/xorg/2008-January/031723.html](http://lists.freedesktop.org/archives/xorg/2008-January/031723.html) ), Luc Verhaegen, a radeonhd developer, says that he needs some specification to write support for dvi->hdmi dongles. But anyway, the bug doesn't necessarily have to be related to the HDMI-to-DVI conversion: it could just be a general xf86-video-intel driver problem with DVI on G35 (whether DVI conversion is passive or not, and whether there's any conversion involved or not).  The intel driver's output detection and the kernel drm modsetting are full of conditionals tests/switchs, per chipset, per output type.
All of your facts can be explained by HDCP issues.  HDCP doesn't kick till after POST, so the TDMS pins are mapped correctly, proving DVI works.  HDCP problems can be induced by not properly mapping HDMI pin 15 to DVI pin 7, thereby explaining why HDMI works.

HDMI used the DVI specification for TDMS signaling.  To be a certified HDMI product and carry the HDMI logo, it has to meet the spec.  By spec, HDMI type A must be 100% backwards compatable with DVI single link.  If you don't believe me, go read the spec.  Why is it that passive HDMI-DVI converters can be used on consumer devices without a "driver rewrite".  Its because their function is defined by spec.  If I'm wrong, a driver isn't the solution.  Its a clear case of consumer fraud at that point and then its time for a class action lawsuit.

As I've said, DVI-HDMI converter is a passive device.  It literally only remaps the pins.  There is no altering of data.  In fact, here's the pin mapouts
```
_DVI single link_                            _HDMI type A_
TMDS Data 2-              Pin 1            TMDS Data2+  
TMDS Data 2+              Pin 2            TMDS Data2 Shield  
TMDS Shield               Pin 3            TMDS Data2–  
*dual link only*          Pin 4            TMDS Data1+  
*dual link only           Pin 5            TMDS Data1 Shield  
DDC Clock                 Pin 6            TMDS Data1–  
DDC Data                  Pin 7            TMDS Data0+  
Analog VSync              Pin 8            TMDS Data0 Shield  
TMDS Data 1+              Pin 9            TMDS Data0–  
TMDS Data 1-              Pin 10           TMDS Clock+  
TMDS shield               Pin 11           TMDS Clock Shield  
*dual link only*          Pin 12           TMDS Clock–  
*dual link only*          Pin 13           CEC  
+5 V                      Pin 14           Reserved (N.C. on device)  
Ground                    Pin 15           DDC Data  
Hot Plug Detect           Pin 16           DDC Clock
TMDS Data 0-              Pin 17           DDC/CEC Ground  
TMDS Data 0+              Pin 18           +5 V Power  
TMDS Shield               Pin 19           Hot Plug Detect
*dual link only*          Pin 20
*dual link only*          Pin 21
TMDS shield               Pin 22
TMDS clock+               Pin 23
TMDS clock-               Pin 24
```
You can literally take a soldering iron and make your own adapter, there's no magic to the converter.  So what's more likely, you have a driver issue or ASUS used a cheap Chinese converter that doesn't map the pins correctly?  Even if I'm wrong, you (Asus owners) owe it to yourselves to stick to K.I.S.S. and eliminate the easy possibilities first.  Buy a new converter dongle.  In fact, I'll ship one to the first person who can prove they have the motherboard and has the DVI issue, free of charge.  Second, compile a list of monitors that people are using to find what works and what doesn't.  When cross referenced with spec sheets, I'm certain you'll find a trend.  You'll need to do this anyways in order to write a driver, how else would you know how to tell the driver what to do?

---

### Post by brundles on 2008-01-09
Doesn't that pin mapping you've printed indicate that a dual-link DVI cable would be a requirement? Several of the pins missing from a single-link DVI cable have a purpose on that DVI-HDMI mapping.

To the un-HDMI-educated layman (i.e. someone like me!), that pin mapping you've posted indicates that HDMI is definitely not compatible with a single-link DVI cable.

At this stage, if I used a single-link DVI cable with the supplied HDMI-DVI convertor, I get the following behaviour:
   System Post:  Everything appears clearly.
   Ubuntu Boot:  Display is shown along with the usplash display as it boots with the progress bar - although there is a rather nasty bright purple line down the left hand side of the screen and a certain amount of noise at the bottom.

Once Ubuntu has finished booting however and it goes past the usplash screen (i.e. the time the resolution gets shifted to 720p and probably when the Intel driver finally kicks in) the signal drops completely. Interestingly, the TV doesn't indicate that it's not getting a signal it just doesn't show anything on the screen - perhaps because it's getting something but can't make sense of it.

---

### Post by theacoustician on 2008-01-09
> **brundles said:**
> Doesn't that pin mapping you've printed indicate that a dual-link DVI cable would be a requirement? Several of the pins missing from a single-link DVI cable have a purpose on that DVI-HDMI mapping.

To the un-HDMI-educated layman (i.e. someone like me!), that pin mapping you've posted indicates that HDMI is definitely not compatible with a single-link DVI cable.

At this stage, if I used a single-link DVI cable with the supplied HDMI-DVI convertor, I get the following behaviour:
   System Post:  Everything appears clearly.
   Ubuntu Boot:  Display is shown along with the usplash display as it boots with the progress bar - although there is a rather nasty bright purple line down the left hand side of the screen and a certain amount of noise at the bottom.

Once Ubuntu has finished booting however and it goes past the usplash screen (i.e. the time the resolution gets shifted to 720p and probably when the Intel driver finally kicks in) the signal drops completely. Interestingly, the TV doesn't indicate that it's not getting a signal it just doesn't show anything on the screen - perhaps because it's getting something but can't make sense of it.Draw a line from every pin on the HDMI connector to its corresponding pin on the DVI connector.  You'll find every pin is mapped 1 to 1. Remember, single link DVI has missing pins in the center of the connector, hence the sections that state *dual link only*.   Here's a picture of DVI standard connectors [http://www.lyberty.com/encyc/articles/tech/img/all-DVI-types.jpg](http://www.lyberty.com/encyc/articles/tech/img/all-DVI-types.jpg) (you want to look at DVI-D single link), here's how you count pins on DVI [http://www.jenving.se/image/dvid_pin.jpg](http://www.jenving.se/image/dvid_pin.jpg) and here's a pic of an HDMI connector with pin numbers [http://content.answers.com/main/content/wp/en-commons/thumb/8/8a/310px-HDMI_Connector_Pinout.svg.png](http://content.answers.com/main/content/wp/en-commons/thumb/8/8a/310px-HDMI_Connector_Pinout.svg.png)

Let me be more clear.  _You can't call a port HDMI or use the HDMI logo unless you have conformed to the HDMI spec_.  From hdmi.org (the HDMI licensing body)
> Q. Is HDMI backward compatible with DVI (Digital Visual Interface)?
Yes, HDMI is fully backward compatible with DVI compliant devices. HDMI DTVs will display video received from existing DVI-equipped products, and DVI-equipped TVs will display video from HDMI sources. However, some older PCs with DVI are designed only to support computer monitors, not televisions. Consumers buying a PC with DVI should make sure that it specifically includes support for television formats and not just computer monitors. 

Also, consumers may want to confirm that the DVI interface supports High-bandwidth Digital Content Protection (HDCP), as content that requires HDCP copy protection will require that both the HDMI and DVI devices support HDCP to properly view the video content.
Note the second paragraph?

---

### Post by herodiade on 2008-01-09
As far as I understand, a driver still can check for the presence of an full fledged HDMI port and monitor, but forget to check for a possible "simplier" DVI connection, no ?

And, anyway, if it would be just a connector or an HDCP problem, I still can't understand why the DVI output works with Xorg using the VESA driver but not with the Intel driver.

**Edit** : Also note this comment on [https://bugs.freedesktop.org/show_bug.cgi?id=13968](https://bugs.freedesktop.org/show_bug.cgi?id=13968) : "This same DVI cable and monitor were working fine on an Asus MiniPC with an i915 chipset".

---

### Post by herodiade on 2008-01-10
Finally, someone took time to report a bug about this issue in Xorg bugtracker (named "[G35 HDMI] HDMI->DVI no display in X"). You can participate to the discussion here :  [https://bugs.freedesktop.org/show_bug.cgi?id=13968](https://bugs.freedesktop.org/show_bug.cgi?id=13968)

Also of interest, the "video tearing" bug : [http://bugs.freedesktop.org/show_bug.cgi?id=11311](http://bugs.freedesktop.org/show_bug.cgi?id=11311)

Beware, the intel xorg driver 2.2.1 release (the one which will probably included in Hardy) is coming soon (so maybe without fixes for the two G35 bugs), the number of 2.2.1 release blockers bugs is very low by now [http://bugs.freedesktop.org/show_bug.cgi?id=13493](http://bugs.freedesktop.org/show_bug.cgi?id=13493)

---

### Post by theacoustician on 2008-01-10
This may be blantently dumb, but has anyone tried emailing Asus with these issues?  They have a custom Linux network driver available on their website.  Between that and the eee, at least they can't give you some line about not having enough resources to support Linux.

---

### Post by brundles on 2008-01-10
I'll have to try and find the links, but when looking at the site before I bought the board, the general train of support was Asus saying Intel provider the drivers with a link - which takes you to the Intel page saying  Linux drivers are provided by the OSS community and a link to the Intel Linux Graphics website.

---

### Post by theacoustician on 2008-01-10
> **brundles said:**
> I'll have to try and find the links, but when looking at the site before I bought the board, the general train of support was Asus saying Intel provider the drivers with a link - which takes you to the Intel page saying  Linux drivers are provided by the OSS community and a link to the Intel Linux Graphics website.Ok, but regardless if they'll give you support or not, shouldn't someone at least try contacting Asus and letting them know what you've found?  Don't mention drivers, just tell them that there's a problem using the DVI converter and see what they say.  Also, does the network driver they offer clear up the problems mentioned earlier?  How does the audio driver they offer fare vs. whatever default driver people have been using stack up?

Back to the graphics issues, has anyone attempted to build the driver from scratch?

---

### Post by jaset on 2008-01-14
Hi all,

Well I just bought a P5E-VM HDMI on the weekend and promptly built my shiny new HTPC. Thereafter installed Kubuntu for the first time ever (I'm a long-time Fedora user). Install went without a hitch - liking the distro so far :)

I'm attempting to run both video and audio over HDMI to my Samsung plasma. Since I have a set of 5.1 Logitech speakers connected to the TV (via optical S/PDIF) it would be nice to switch both video & audio sources at once.

Firstly, on the audio front - I followed [Temüjin's instructions]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60") to install OSS. The 3.5mm analog output seems to work fine, but for some reason I'm only getting output from the left channel over HDMI through the TV to my speakers. I've tried messing with ossxmix settings, and the right channel doesn't seem to be muted in any way I can see. I also tried osstest which only outputs on the left channel as well - the right channel test is completely silent. Can anyone running OSS audio over HDMI confirm both channels are working?

On to video. I'm also getting the video tearing problem with 2.1.1 drivers :(
(at least I think it's 2.1.1, [FONT="Courier New"]dpkg -l|grep intel[/FONT] reports [FONT="Courier New"]xserver-xorg-video-intel 2:2.1.1-0ubuntu9[/FONT] so I assume so).

> **theacoustician said:**
> Back to the graphics issues, has anyone attempted to build the driver from scratch?

I just pulled down the latest sources and followed the [install guide on the intel site]("http://intellinuxgraphics.org/install.html"), but unfortunately I'm still getting the tearing problem. I had a quick look through the git source repository history for any checkins related to fixing this issue, but didn't find anything (makes sense I guess, since it still doesn't work..).

Well that's all I have for now. I haven't tried DVI yet so nothing to report there. Aside from these issues, the board itself it seems to be running nicely so far..

---

### Post by herodiade on 2008-01-14
I finally received my Asus P5E-VM HDMI (and loaded it with an Intel Core 2 Quad Q6600 revision G0 CPU, 4 Go of PC6400 DDR2, and 100% SATA-II & NCQ compliant disks). I did a full Ubuntu Gutsy install from scratch (didn't used a previously installed system), then upgraded to (in development) Hardy Heron, and :

* I confirm the "undetected DVI-out" problem with intel xorg driver (and I confirm that vesa xorg driver works fine through the same DVI plug). Btw, my old monitor (Belinea 101920 LCD) has no support for HDCP and has no HDMI plug, only VGA and DVI.

* By the way, the HDMI (and DVI) transmiter chipset is a SILC (Silicon Image) SiI1392 . See [http://plusd.itmedia.co.jp/pcuser/articles/0711/30/news070.html](http://plusd.itmedia.co.jp/pcuser/articles/0711/30/news070.html) and [http://www.siliconimage.com/products/product.aspx?id=106](http://www.siliconimage.com/products/product.aspx?id=106)

* Also : here, the Gutsy's intel xorg driver didn't supported or didn't detected  the graphic driver correctly, and defaulted to vesa. I upgraded to Hardy Heron anyway, where intel driver works (except for the DVI output, and except the EXA activation by default (see below)). 

* The intel xorg driver default (autodetected) conf has a problem with Hardy as of now : it fails to display the fonts (because compiz got activated by default, with EXA accel). Adding Option "AccelMethod" "XAA" in xorg.conf fixed this problem. 

* In Hardy, Compiz works out of the box (except we need to switch manually from EXA to XAA). We don't need the SKIP_CHECKS tweak anymore.

* As of now, Hardy xserver-xorg-video-intel version is 2.2.0+git20080107-1ubuntu1, xserver-xorg-core is 1.4.1~git20080105-1ubuntu1, mesa is 7.0.2-3ubuntu1, linux kernel is 2.6.24-3. Subject to changes before Hardy release, indeed. So the aforementioned graphic problems are still here with very recent developments versions of the drivers.

* I can't test sound over HDMI (since I've no HDMI compliant monitor), and didn't tested Ubuntu in 64 bit mode. Didn't tested the Attansic TSO patch yet (but will do it soon). I didn't tested the ICH9R semi-hardware raid support. I've only 10/100 switches, so I didn't tested the NIC at gigabit speed.

* I can't confirm the network (Attansic driver) problem someone had with the Ubuntu Gutsy install CD : here, using the standard Ubuntu Gutsy i386 desktop CD (ubuntu-7.10-desktop-i386.iso), the network worked immediately (at 100 Mbps full duplex), out of the box, even using the livecd and during install. Did your problem occurred with this CD or with the alternate gutsy install CD ? Or did you used a gigabit switch ?

* The motherboard chipset tends to overheat slightly, averaging at 49 degrees Celsius in a large ATX case (btw, you have to load the w83627ehf and coretemp lm-sensors kernel modules to get temp and fan sensors)

* Block devices performances are impressive (as is responsiveness under I/O load), using the 2.6.24 (Hardy kernel) AHCI libata driver and NCQ capable devices. I didn't tried disks hotplug (it should work, it's supported by libata when using ahci, cf. [http://linux-ata.org/driver-status.html](http://linux-ata.org/driver-status.html) ). I also tested the block layer with the less capable ata_piix driver, and it works too.

* The BIOS doesn't hide the interesting capabilities (as some BIOS do sometime), even the useful but incompatibles with WinXP settings : virtualisation support is here (and works well with KVM), AHCI is here (but not activated by default), configurable suspend to ram settings, HPET high resolution timer is activated, speedstep support, NX bit support, ...

* Suspend to ram and virtualisation works very well

* I didn't experienced the reported video tearing problems so far, and the network is quite stable.

* I didn't upgraded the BIOS yet (still using the default 0202-10/24/2007version, while asus is at 0405-01/02/2008 now).

All in all, the motherboard is nice and well working, fully supported out of the box (it only needs F/OSS drivers integrated in standard upstreams kernel/xorg/alsa/lm-sensors), well featured, but for me it works better with the next, in development, Ubuntu version (Hardy Heron) than the current one (Gutsy Gibbons). The only smalls problems I had under Hardy is the "DVI output not detected by intel xorg driver" one (no know workaround except using vesa driver), and the driver activating EXA (which doesn't work) instead of XAA by default (but the workaround is easy). 

Those minor glitches where to be expect with such a very new hardware chipset (that's the first Intel G35 motherboard on the market, and it was available only two month before Gutsy release). Hopefully that's probably just a driver problem, therefore, will be fixed ; I just hope everything will be fixed on time for Hardy Heron release, since G35 (GMA X3500) and G45 (GMA X4500) based motherboards will become common during Hardy LTS lifetime, and the workarounds needed to circumvent the problems aren't at reach for linux newcomers.

---

### Post by brundles on 2008-01-14
Wow, someone has been busy :)

During the install I ran the text based alternate install CD but that was mainly because that's the one I had at the time. I guess it's possible the setup path is different because of that. The cable itself is only connected to a 10/100 switch.

The main thing I've been arguing with recently was the memory in my system. I got some OCZ 6400 memory but only found later that the P5E-VM downgrades it from 800 to 667 as the bus speed depending on the latency - which when done automatically left it with some serious stability issues. At the moment I'm runng with the BIOS manually forcing the speed to 667 and it's nice and stable. Something I did notice was that after that, the tearing seemed much less. I'm curious as to whether that could actually be a factor in those who are seeing tearing vs those that aren't. Also, what type of things dod you try to get the tearing?

I'm a bit disappointed that the latest 2.2.1 drivers didn't resolve it - I'd read something about xv performance improvements and hoped that might be enough. Nevermind, I'm sure it'll get resolved soon enough.

---

### Post by herodiade on 2008-01-15
> **brundles said:**
> 
During the install I ran the text based alternate install CD but that was mainly because that's the one I had at the time. I guess it's possible the setup path is different because of that. The cable itself is only connected to a 10/100 switch.


Ah, that should be it. The two bugs reports I found in launchpad about Attansic L1 driver missing on a Gutsy install CD are about the "alternate install CD" and the 64 bit one. Both bug reporters states that they don't have this problem with the main i386/32bits Gutsy desktop livecd. See :
[https://bugs.launchpad.net/efficientpc/+bug/159561](https://bugs.launchpad.net/efficientpc/+bug/159561)
[https://bugs.launchpad.net/ubuntu/+bug/147557](https://bugs.launchpad.net/ubuntu/+bug/147557)
So I bet if you boot ubuntu-7.10-desktop-i386.iso livecd, you'll have the network back. That would help to write a more precise bug report.

> **brundles said:**
> 
The main thing I've been arguing with recently was the memory in my system. I got some OCZ 6400 memory but only found later that the P5E-VM downgrades it from 800 to 667 as the bus speed depending on the latency - which when done automatically left it with some serious stability issues. At the moment I'm runng with the BIOS manually forcing the speed to 667 and it's nice and stable. Something I did notice was that after that, the tearing seemed much less. I'm curious as to whether that could actually be a factor in those who are seeing tearing vs those that aren't. Also, what type of things dod you try to get the tearing?


I use 4 x 1 Go of DDR2 PC6400 (800Mhz) G.Skill Dual Channel, with a CL4 cas (CL4-4-4-12) (ref. F2-6400CL4D-2GBPK), and did let the motherboard choose the frequency (automatically detected, I didn't tweak that manually), and it's stable. How can I know the chosen frequency (ie. whether it is 667 or 800) ? Another potential difference: I switched X11 acceleration method from EXA (default for intel driver) to XAA (by adding `Option "AccelMethod" "XAA"` in xorg.conf): did you tried that ?

What I tried to get tearings : I played several videos samples (divx/avi, theora/ogg and h264/mkv), seeking to, and watching carefully for scenes with fast action/movement. I used mplayer (-vo xv). I also watched a full action film (divx/avi), and TV streams (mpeg2-ts, interlaced) with vlc. Finally, I watched the famous "dolby-city.vob" short test video using mplayer with "-vo x11", "-vo xv", "-vo gl" and "-vo gl2". Well, all tests with Hardy. No tearing at all.

> **brundles said:**
> 
I'm a bit disappointed that the latest 2.2.1 drivers didn't resolve it - I'd read something about xv performance improvements and hoped that might be enough. Nevermind, I'm sure it'll get resolved soon enough.

Wel I only said that 2.2.1 (or at least, last week xserver-intel git HEAD) does not solve the DVI-out problem. Since I've no tearing problem at all, and didn't tested previous driver versions, it may have solved that one. I just can't say. Or did you mean you tried yourself the 2.2.1 and still experienced tearing ?

---

### Post by brundles on 2008-01-15
I haven't tried build the 2.2.1 drivers - although jaset did say they hadn't had any success resolving the tearing earlier.

The tearing seems to manifest itself more when the shot pans round rather than on rapidly changing sequences which it seems perfectly happy with. I've updated the xorg.conf file already but can't try the playback until I actually get home.

In terms of the memory, if you're not sure of the speed I would suggest manually setting the DRAM speed to 800 and leaving everything else at auto. There was something on the OCZ support forum on the P5E-VM and their 6400 Platinum Rev DDR2 which I found also resolved it at the higher speeds - setting the DRAM Voltage to 2.1V (recommended by OCZ support) or 2.0V (tried by the guy who raised the issue).

---

### Post by herodiade on 2008-01-15
**I have DVI working, right now.** :)

The only change I can think of, since my last non working DVI-out test is that I upgraded the Asus motherboard BIOS (from revision 202 to revision 405).

If this BIOS update is the cause of the resolution, that should be an hardware state change visible to kernel (and that may be workarounded from kernel or xorg space, to get retrocompatibility with older BIOSes). 

So please, someone that still have the problem: could you please run (as root, and *before your try to upgrade the BIOS* !)  "sudo lspci -vvvxxxx", and post a "diff -u" with my present lscpi (which is attached to this bug : [http://bugs.freedesktop.org/show_bug.cgi?id=13968](http://bugs.freedesktop.org/show_bug.cgi?id=13968) ) ? No need to run the lspci with a DVI attached monitor (or any monitor at all, for that matter), that shouldn't change anything.

Also, an other test to do before trying a BIOS upgrade: please, test if DVI out work after temporarily disabling HDA audio in the BIOS.

Thanks.

About the tearing: Ok, fast moving sequences weren't a good test, but I didn't have the problem while watching a full length movie and while watching TV, either.

---

### Post by brundles on 2008-01-15
The XAA change has made a slight improvement - the tearing is now pretty miuch at the stage where I have to look for it. I'm wondering if that is something else that might get cleared up by the BIOS upgrade though as it obviously (judging by the details on the bug report) triggers different behaviour in the driver.

I haven't the lspci as that's already in the bug report, but I can confirm that disabling the audio chip doesn't make any difference.

I'll upgrade the BIOS later on (hopefully) and let you know whether that makes a difference on the tearing side of things.

*Edit:* The BIOS is now running 0405 and the tearing is still there - and the HDMI-DVI is still not working :(. At this stage, given there is nothing sticking out in the diff between the lspci outputs that's probably down to the difference between Gutsy and Hardy though. There may also be something in there clearing up the tearing problem too.

---

### Post by bric on 2008-01-16
> **brundles said:**
> 
The main thing I've been arguing with recently was the memory in my system. I got some OCZ 6400 memory but only found later that the P5E-VM downgrades it from 800 to 667 as the bus speed depending on the latency - which when done automatically left it with some serious stability issues.

I just got a p5e-vm hdmi also with OCZ RAM (plat rev 2 pc6400-ddr800) and discovered the same thing as you.  However, I achieved stability by leaving everything on 'auto' except for modifying the RAM voltage to 2.0.  I have yet to go back and run memtest for more than 5 hours but all other stress tests are fine and my other stability issues went away.

-edit: whoops, I see that you already found this out.  Guess we're frequenting the same forums.

---

### Post by brundles on 2008-01-17
> **bric said:**
> I just got a p5e-vm hdmi also with OCZ RAM (plat rev 2 pc6400-ddr800) and discovered the same thing as you.  However, I achieved stability by leaving everything on 'auto' except for modifying the RAM voltage to 2.0.  I have yet to go back and run memtest for more than 5 hours but all other stress tests are fine and my other stability issues went away.

-edit: whoops, I see that you already found this out.  Guess we're frequenting the same forums.

It was probably your support post with OCZ I was reading to get the answer :D

---

### Post by brjhaverkamp on 2008-01-20
Hello All, 

I found this thread when searching the I'net for info on the Shuttle SG33G5 box for HTPC. It too has an intel GM3100 graphic chip and an HDMI connector.
What I did not find in this thread, (or possibly overlooked) but would like to get confirmation on is the following:

1) Can this chipset do Full-HD (1080p) under linux?
2) If so, is this with hardware exceleration( XVMC) or with raw processing power. In both cases, what processor do I minimally need for this?

I hope someone can answer these two questions from personal experience;-)  It would be great to have a mythbox connected to my new shiny full-hd LCD tv soon.

Regards,

Bert

---

### Post by theacoustician on 2008-01-20
> **brjhaverkamp said:**
> Hello All, 

I found this thread when searching the I'net for info on the Shuttle SG33G5 box for HTPC. It too has an intel GM3100 graphic chip and an HDMI connector.
What I did not find in this thread, (or possibly overlooked) but would like to get confirmation on is the following:

1) Can this chipset do Full-HD (1080p) under linux?
2) If so, is this with hardware exceleration( XVMC) or with raw processing power. In both cases, what processor do I minimally need for this?

I hope someone can answer these two questions from personal experience;-)  It would be great to have a mythbox connected to my new shiny full-hd LCD tv soon.

Regards,

Bert

1. Full HD is kind of a marketing term.  There's no spec or standard that outlines Full HD.  Which 1080p would you consider "full"?  1080p23.98, 1080p24, 1080p25, 1080p29.97, 1080p30, 1080p50, 1080p50M, 1080p59.94, 1080p60, 1080sf/23.98, 1080sf/24, 1080sf/25, 1080sf/29.97, 1080sf/30?  It seems as if no one is having issues with 1920x1080 @ 60 Hz on the display side other than the tearing that's mentioned in this thread.

2. There's no H.264 or VC-1 acceleration in Linux at all.  I'm not entirely sure if hardware acceration works for HD MPEG2 encoded material.  If anyone knows, please post that here.  I use the general rule of 2.4 GHz on a C2D is the minumum you'd want for 1080 material decoding.  I arrived at this by averaging the specs for several software players out there and comparing it people's posting of real life experience.  There's no real way to say for certain, because a video can use different encoding methods and that alters CPU requirement.  For instance, using lots of b-frames and pyramiding b-frames requires a whole lot more processing power than say an all i-frame encoded video.  The easiest answer here is until hardware decoding arrives, get the best CPU you can afford.

---

### Post by brundles on 2008-01-21
Something else to remember when playing things like x264s is to check the software state. Taking mplayer as an example, while the Ubuntu package works out of the box for pretty much everything it's not the quickest build. Rebuilding it for yourself will give a noticeable improvement - I can also highly recommend the CoreAVC patch for MPlayer in this case. 

To give you an indication of the performance gains, we saw a drop from 50% (ish) to 40% (ish) on a dual core CPU just by doing the rebuild and a similar drop patching in CoreAVC.

---

### Post by jpeeters on 2008-01-21
> **brundles said:**
> Rebuilding it for yourself will give a noticeable improvement - I can also highly recommend the CoreAVC patch for MPlayer in this case.


Do you have any information about the CoreAVC patch? I am particulary interested in this one, as my current setup is just a bit slow during playback.

Or we might start with a new repository for these special packages?

---

### Post by brundles on 2008-01-21
These are the links I was given a while back when trying to get x264s to play back on my old (cache-crippled) Celeron:
[http://code.google.com/p/coreavc-for-linux/](http://code.google.com/p/coreavc-for-linux/)
[http://code.google.com/p/coreavc-for...erInstallation](http://code.google.com/p/coreavc-for...erInstallation)
[http://comments.gmane.org/gmane.comp...er.cygwin/2228](http://comments.gmane.org/gmane.comp...er.cygwin/2228)
[http://mythtv.org/pipermail/mythtv-d...ead.html#47052](http://mythtv.org/pipermail/mythtv-d...ead.html#47052)
[http://ubuntuforums.org/archive/index.php/t-433403.html](http://ubuntuforums.org/archive/index.php/t-433403.html)

I'd suggest starting off with just rebuilding MPlayer on the machine and seeing how you get on.

---

### Post by J33pG33k on 2008-01-22
> **theacoustician said:**
> 
2. There's no H.264 or VC-1 acceleration in Linux at all.  I'm not entirely sure if hardware acceration works for HD MPEG2 encoded material.  If anyone knows, please post that here.  I use the general rule of 2.4 GHz on a C2D is the minumum you'd want for 1080 material decoding.  I arrived at this by averaging the specs for several software players out there and comparing it people's posting of real life experience.  There's no real way to say for certain, because a video can use different encoding methods and that alters CPU requirement.  For instance, using lots of b-frames and pyramiding b-frames requires a whole lot more processing power than say an all i-frame encoded video.  The easiest answer here is until hardware decoding arrives, get the best CPU you can afford.

I've been doing a good deal of research lately into the current state of hardware acceleration in the latest xf86-video-intel driver.  The current main-tree intel driver does not support any type of hardware acceleration for any chipsets other than the i810 and i815, which are relatively old.  Work is being done on an 'intel-xvmc' branch that is aiming to fix this.  Right now, there should be experimental XvMC support for the 945 chipset, but I don't believe that it is working for anything newer.  See: [http://lists.freedesktop.org/archives/xorg/2008-January/031910.html]("http://lists.freedesktop.org/archives/xorg/2008-January/031910.html")

Hope this helps a little.

---

### Post by theacoustician on 2008-01-23
> **brundles said:**
> Something else to remember when playing things like x264s is to check the software state. Taking mplayer as an example, while the Ubuntu package works out of the box for pretty much everything it's not the quickest build. Rebuilding it for yourself will give a noticeable improvement - I can also highly recommend the CoreAVC patch for MPlayer in this case. 

To give you an indication of the performance gains, we saw a drop from 50% (ish) to 40% (ish) on a dual core CPU just by doing the rebuild and a similar drop patching in CoreAVC.
Good point.  Also, I've found running 64bit over 32bit gives about a 10-20% improvement on the encoding side.  I forget what I got on the decoding side.  It was an improvement, but not as noticable as the encoding improvement.

> **jpeeters said:**
> Do you have any information about the CoreAVC patch? I am particulary interested in this one, as my current setup is just a bit slow during playback.

Or we might start with a new repository for these special packages?
Might be a little tough considering CoreAVC is pay software, but if someone knows how to do this so the file can be just plugged in, I'd be willing to help out.

> **J33pG33k said:**
> I've been doing a good deal of research lately into the current state of hardware acceleration in the latest xf86-video-intel driver.  The current main-tree intel driver does not support any type of hardware acceleration for any chipsets other than the i810 and i815, which are relatively old.  Work is being done on an 'intel-xvmc' branch that is aiming to fix this.  Right now, there should be experimental XvMC support for the 945 chipset, but I don't believe that it is working for anything newer.  See: [http://lists.freedesktop.org/archives/xorg/2008-January/031910.html]("http://lists.freedesktop.org/archives/xorg/2008-January/031910.html")

Hope this helps a little.Whoa.  I read all that and it was a little vague.  Are they talking about the newer XvMC API that will handle H.263/H.264/VC-1?  I thought that was purely in the planning stages right now and that they were concentrating on wider support of chipsets before they tackled newer codecs and features.  Man, that's really exciting if they are getting that close to supporting newer codecs.

---

### Post by brundles on 2008-01-23
> **theacoustician said:**
> Might be a little tough considering CoreAVC is pay software, but if someone knows how to do this so the file can be just plugged in, I'd be willing to help out.
That's a good point about the repository side of things - the process to get CoreAVC running under Linux also involves "registering" the codec library - which requires the Windows registration key as well as the CoreAVC key. Can't see MS being too happy at having a Windows registration key included in a Linux app repository!

---

### Post by J33pG33k on 2008-01-24
> **theacoustician said:**
> 
Are they talking about the newer XvMC API that will handle H.263/H.264/VC-1?

I don't think so, but I don't want to say for sure.  I've been looking around for a new board for some MythTV front-ends and would like to stay purely open source (the Via boards are in a similar situation - excellent hardware without drivers to fully support them).  ATM, the only thing that I have had confirmed is that XvMC doesn't work on any chipset other than i810 and i815.

> **theacoustician said:**
> I thought that was purely in the planning stages right now and that they were concentrating on wider support of chipsets before they tackled newer codecs and features.  Man, that's really exciting if they are getting that close to supporting newer codecs.

I think you are correct when talking about the main branch of the intel driver, but again, I don't want to step too far out of my knowledge zone.  The xvmc work that I commented on is being done on a completely separate branch.  I for one am trying to build everything necessary to test the intel-xvmc driver because I also can't wait until these highly capable chipsets are fully supported.  The board that this topic started with would make a real nice combo frontend/backend.

---

### Post by glaxo on 2008-01-25
Anyone got an update on the DVI out of this board?

---

### Post by brundles on 2008-01-26
Nothing else on the DVI yet I'm afraid.

On another subject, has anyone tried Wake-on-LAN with this board? It's not agreeing at the moment much to my irritation.

So far:
  - Wake from PCI and PCI-E enabled in the BIOS.
  - "ethtool -s eth0 wol g" included in the shutdown scripts
  - Altered the /etc/init.d/halt script to remove the -i as I've seen that cause problems before.

No joy so far :(

*Edit:* Nevermind - it seems there is a [bug in the kernel atl1 driver that comes with Gutsy](http://ubuntuforums.org/showthread.php?t=603620&highlight=wake+lan) and building the supplied drivers resolves it. 

I'm happy again :)

---

### Post by bwaskiew on 2008-01-26
Hello,

I am somewhat new to Ubuntu, and I just built a new pc that I am going to dual boot Vista & Ubuntu on.

I found this thread while googling for any issues with my motherboard on linux. I have this motherboard, and I would like to lend my help in any way that I can, in addition to asking a couple questions about my immediate future in using it.

First off, I will say as a standard user (not using it as a HTPC), everything works right off the bat, even with my widescreen Samsung 226BW on 1680x1050 resolution.

Ubuntu defaulted to 'intel - Experimental modesetting driver for l...' and I can't read the rest :o

I cannot get compiz-fuzion to work. I have only tried to enable it the standard way (System>Preferences>Appearance>Visual Effects) and to add 'SKIP_CHECKS=yes' to the compiz configuration. The first failed, and the second said the directory didn't exist (I don't have any compiz plugins installed other than the default). Is it not working because I haven't set something up, or changed a config file? Or is it just not going to work with the motherboards integrated graphics card because it is so new (or at least until the driver gets updated)?

As to the monitor, I am using it via the DVI>HDMI converter, and it does work with the driver I specified. It also does work on Windows Vista Home Premium (32 bit). My only problem with the monitor, is that I can't seem to get a dual monitor setup running. I am not sure if this is only because of the newness of the motherboard (and driver), or if it a generally tough process in Linux. If anyone has any advice about that, please don't hesitate to shout out. I don't absolutely *need* a dual monitor setup, but I would love it.

If anyone wants to ask me to do something either on Ubuntu, or on Vista, let me know and I'll help any way I can.

Thanks!
Brandon

---

### Post by herodiade on 2008-01-28
> **bwaskiew said:**
> 
I cannot get compiz-fuzion to work. I have only tried to enable it the standard way (System>Preferences>Appearance>Visual Effects) and to add 'SKIP_CHECKS=yes' to the compiz configuration. The first failed, and the second said the directory didn't exist (I don't have any compiz plugins installed other than the default). Is it not working because I haven't set something up, or changed a config file? Or is it just not going to work with the motherboards integrated graphics card because it is so new (or at least until the driver gets updated)?


Yes if the config directory does not exists, the config won't be written. I think you can do that (I can't test since I use Hardy, and this check doesn't apply there):
mkdir -p ~/.config/compiz/
echo SKIP_CHECKS=yes > ~/.config/compiz/compiz-manager 
Then restart X11 (or reboot), and try re-enabling "visual effects" as you did (System>Preferences>Appearance>Visual Effects).

It could expose some display bugs (if so, you'd have to switch to XAA).

> **bwaskiew said:**
> 
As to the monitor, I am using it via the DVI>HDMI converter, and it does work with the driver I specified. It also does work on Windows Vista Home Premium (32 bit). 


Glad to see I'm not the only one to have DVI working with the Asus P5E-VM HDMI. :) Now, we have to figure why it works for us...

> **bwaskiew said:**
> 
My only problem with the monitor, is that I can't seem to get a dual monitor setup running. I am not sure if this is only because of the newness of the motherboard (and driver), or if it a generally tough process in Linux. If anyone has any advice about that, please don't hesitate to shout out. I don't absolutely *need* a dual monitor setup, but I would love it.


There's something about this on Intel website's documentation. See:
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

> **bwaskiew said:**
> 
If anyone wants to ask me to do something either on Ubuntu, or on Vista, let me know and I'll help any way I can.


Thanks for the proposal. It would be interesting if you could tell if this bug affects you too :  [http://bugs.freedesktop.org/show_bug.cgi?id=14249](http://bugs.freedesktop.org/show_bug.cgi?id=14249)
The test is simple : 
- just verify that your virtuals terminals are working (switch to the first one with ctrl-alt-f1, you should see some text, then switch back to X11 with ctrl-alt-f7)
- then suspend-to-ram
- then look again on ctrl-alt-f1 : is the console prompt still there or is the screen totally black ? (again, ctrl-alt-f7 to get your X11 session back).

---

### Post by bwaskiew on 2008-01-28
The compiz config worked perfectly, thank you very much!

The Intel site looks very promising also, I will give that a try tomorrow when I get home from work.

As for the virtual terminals, I tried that out and did indeed get a black screen (in addition to a message popping up in the lower right hand corner of my desktop that said 'Your computer failed to suspend properly.' When I tried going back into the virtual terminal, it was a black screen. So the bug definitely exists on my machine also.

Thank you again for the help!

I will continue monitoring this thread in case anyone else needs some testers for this motherboard.

-Brandon

---

### Post by Aryding on 2008-01-29
I have the same motherboard and I'm running HDMI to the monitor.  The screen is kind of blurry, especially around letters, not matter which font or where.  Anybody else having this problem?

---

### Post by bwaskiew on 2008-01-29
Hello again,

I have tried to do the dual monitor setup, and received some success and some failure :O

Apparently I can't have both compiz-fusion AND a dual monitor setup. When googling, it seems that it is a restriction on the hardware of 945 chipsets and earlier, but this chipset is far ahead of the 945. I checked the system settings, and I think Ubuntu is seeing it as a 965, which isn't right, but should be good enough so that this problem doesn't affect me. I have seen compiz fusion work with a dual monitor setup on many other pcs, so I know it must be possible with this intel chip since it is pretty new. I'm just not sure how to get around the 2048x2048 limitation (my virtual screen ends up being 2960x1050).

Secondly, my taskbar and top bar are both on the wrong screen (the VGA port, or analog monitor, which I'm using as my secondary). Following a tutorial on xrandr ([http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")) it says that there doesn't seem to be a way around this. That seems hard to believe, as normally I would think you can set which monitor is the primary monitor, and have all of the important menu bars on that one. Does anyone know of a way around this issue?

Thanks for the help! Hopefully this thread can help any future new Ubuntu/Linux users out there who use this motherboard and are trying to set up the displays.

-Brandon

---

### Post by theacoustician on 2008-01-31
> **bwaskiew said:**
> Hello again,

I have tried to do the dual monitor setup, and received some success and some failure :O

Apparently I can't have both compiz-fusion AND a dual monitor setup. When googling, it seems that it is a restriction on the hardware of 945 chipsets and earlier, but this chipset is far ahead of the 945. I checked the system settings, and I think Ubuntu is seeing it as a 965, which isn't right, but should be good enough so that this problem doesn't affect me. I have seen compiz fusion work with a dual monitor setup on many other pcs, so I know it must be possible with this intel chip since it is pretty new. I'm just not sure how to get around the 2048x2048 limitation (my virtual screen ends up being 2960x1050).

Secondly, my taskbar and top bar are both on the wrong screen (the VGA port, or analog monitor, which I'm using as my secondary). Following a tutorial on xrandr ([http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")) it says that there doesn't seem to be a way around this. That seems hard to believe, as normally I would think you can set which monitor is the primary monitor, and have all of the important menu bars on that one. Does anyone know of a way around this issue?

Thanks for the help! Hopefully this thread can help any future new Ubuntu/Linux users out there who use this motherboard and are trying to set up the displays.

-BrandonDual monitors for a Myth box?:confused:

---

### Post by bwaskiew on 2008-01-31
> **theacoustician said:**
> Dual monitors for a Myth box?:confused:

Sorry, I didn't quote anything or leave any reference :O

I had a post in the page before this one about this motherboard, but not about MythTV. Just about the functionality of the integrated graphics card and the outputs, but being used in a workstation setting instead of media entertainment.

I kept my discussion in this thread since my problems are closely related to the components of the hardware, and not just general issues with having multiple desktops or desktop effects. This thread is the best I've found on the net so far of people who use this motherboard and are dealing with its issues :)

If you have any other places to recommend I would gladly receive any other forums or sites :)

---

### Post by theacoustician on 2008-01-31
> **bwaskiew said:**
> Sorry, I didn't quote anything or leave any reference :O

I had a post in the page before this one about this motherboard, but not about MythTV. Just about the functionality of the integrated graphics card and the outputs, but being used in a workstation setting instead of media entertainment.

I kept my discussion in this thread since my problems are closely related to the components of the hardware, and not just general issues with having multiple desktops or desktop effects. This thread is the best I've found on the net so far of people who use this motherboard and are dealing with its issues :)

If you have any other places to recommend I would gladly receive any other forums or sites :)Ok, I was just trying to wrap my head around what one would do with a dual head Myth box.

You might want to make a thread in the Multimedia and Video forum simply because the display gurus are more likely to see your question and offer assistance.  In fact, you might want to generalize it more and just mention the chipset and not the motherboard.  Someone else with the same chip but different board might find an answer you could apply to your case.  Not saying it'll go anywhere, but it will certainly get more eyes on the problem.

---

### Post by bwaskiew on 2008-01-31
Will do. Thanks for the advice.

---

### Post by brundles on 2008-02-01
Some good news for the G35 driver front today :)

[http://www.phoronix.com/scan.php?page=article&item=984&num=1](http://www.phoronix.com/scan.php?page=article&item=984&num=1)

In short - Intel have made over 1,700 pages of programming docs for the chipset freely available to anyone that fancies a crack at writing the drivers.

---

### Post by theacoustician on 2008-02-01
> **brundles said:**
> Some good news for the G35 driver front today :)

[http://www.phoronix.com/scan.php?page=article&item=984&num=1](http://www.phoronix.com/scan.php?page=article&item=984&num=1)

In short - Intel have made over 1,700 pages of programming docs for the chipset freely available to anyone that fancies a crack at writing the drivers.
Ha!  I just came here to post that, except here's the direct link to the Intel site with the documentation : [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)

As for the question on dual heads, take a look at this : [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)  It would seem 2048 x 2048 is the max. the chip can produce.  The only way to get around that limit is to get a dedicated video card.

---

### Post by bwaskiew on 2008-02-01
> **theacoustician said:**
> As for the question on dual heads, take a look at this : [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)  It would seem 2048 x 2048 is the max. the chip can produce.  The only way to get around that limit is to get a dedicated video card.

I almost came to that conclusion too, except that in that link you supplied (which is the exact link that got me dual screen in the first place, coincidentally), it says:

There is a known issue that DRI doesn't work on pre-965 if maximum is larger than 2048x2048.

I guess one of my misunderstandings is exactly what 'pre-965' means. Is it the driver version? In which case I am using the only intel driver I know of, and not using the xorg i9xx drivers. If it is the hardware, I'm still not sure what it is in relation to the GMA X3500. Even so, if any of Intel's documentation says 'pre' anything, I would think the GMA X3500 is after that, since it is (I think) the 2nd newest chipset they have.

Thanks for the help though. I actually just e-mailed Intel last night for a (hopefully) definitive answer. If that doesn't pan out, I'm going to have to choose between single monitor and DRI, or dual head with no DRI. Since Linux is so much better at multiple desktops than Windows anyways, I'm leaning towards single monitor with DRI.

---

### Post by theacoustician on 2008-02-01
> **bwaskiew said:**
> I almost came to that conclusion too, except that in that link you supplied (which is the exact link that got me dual screen in the first place, coincidentally), it says:

There is a known issue that DRI doesn't work on pre-965 if maximum is larger than 2048x2048.

I guess one of my misunderstandings is exactly what 'pre-965' means. Is it the driver version? In which case I am using the only intel driver I know of, and not using the xorg i9xx drivers. If it is the hardware, I'm still not sure what it is in relation to the GMA X3500. Even so, if any of Intel's documentation says 'pre' anything, I would think the GMA X3500 is after that, since it is (I think) the 2nd newest chipset they have.

Thanks for the help though. I actually just e-mailed Intel last night for a (hopefully) definitive answer. If that doesn't pan out, I'm going to have to choose between single monitor and DRI, or dual head with no DRI. Since Linux is so much better at multiple desktops than Windows anyways, I'm leaning towards single monitor with DRI.

Yep, its a little screwy and I see what you're saying.  If it makes you feel any better, once you start using the keyboard shortcuts, swapping desktops is almost a reflex.

---

### Post by iramhernandez on 2008-02-01
For folks talking about about hdmi to dvi conversion... I got it to work by using dpkg-reconfigure xserver-xorg  to set up X to boot with the vesa drivers, rebooting and using the "Screen and Graphics" program to select a plug and play monitor, rebooting again into a broken x session, and taking bits and pieces of all the xorg.conf files generated  to produce the xorg.conf below.  And just to make things more complicated (not because I'm sadistic but because I didn't have a straight hdmi-hdmi cable handy).  I went from hdmi output of  pc -  to hdmi/dvi converter - to hdmi/dvi cable - to hdmi input of tv.

I'm still hacking away at the xorg.conf but in case this is handy to anybody, here goes mine.

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	720
		Modes		"1280x720@60"	"1280x720@50"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by brundles on 2008-02-02
> **iramhernandez said:**
> For folks talking about about hdmi to dvi conversion... I got it to work by using dpkg-reconfigure xserver-xorg  to set up X to boot with the vesa drivers, rebooting and using the "Screen and Graphics" program to select a plug and play monitor, rebooting again into a broken x session, and taking bits and pieces of all the xorg.conf files generated  to produce the xorg.conf below.  And just to make things more complicated (not because I'm sadistic but because I didn't have a straight hdmi-hdmi cable handy).  I went from hdmi output of  pc -  to hdmi/dvi converter - to hdmi/dvi cable - to hdmi input of tv.

I'm still hacking away at the xorg.conf but in case this is handy to anybody, here goes mine.
...


Interesting trick - the main thing looks like you've used the VESA drivers to get the modelines then fed them back through the Intel drivers - unless I've missed something. I'm sure I saw something on another thread/link about EDID problems - that would work as a way around it. Might be worth a try when I get access to the TV.

---

### Post by herodiade on 2008-02-03
Here DVI out does work without the need to explicitly set modelines. I've `Option "DMPS"` in the "Monitor" section though. The whole xorg.conf was automatically generated by Hardy tools, and is quite simple (I've only manually removed unused wacom input devices definitions) :

```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "oss"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Carte vidéo générique"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "B_101920"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Carte vidéo générique"
        Monitor         "B_101920"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "800x600" 
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

The resulting DVI display works but is slightly blurry, esp. fonts (maybe because my monitor is an old and cheap beast) so I still prefer the VGA connection.

---

### Post by brundles on 2008-02-03
Could someone who has the HDMI-DVI adapter working post the following either on the thread or pm to me?

sudo get-edid | parse-edid

It has a moan about my TV providing invalid EDID data and I'm curious  as to whether that could be contributing towards the problem.

Also, does anybody know of an option to force the Intel driver to ignore the EDID settings? The IgnoreEDID option that I've seen referenced for other drivers isn't supported :(.

*Edit:* Including Option "DDC" "false"  under the device section seemed to do the trick - as a one time only deal anyway. It brought the screen up on nearly the right resolution (1280x769 instead of 1280x720) but then proceeded to log me out and log me back in as another user - ever since then it's not worked again on the HDMI-DVI port.

---

### Post by iramhernandez on 2008-02-03
> **brundles said:**
> Could someone who has the HDMI-DVI adapter working post the following either on the thread or pm to me?

sudo get-edid | parse-edid



I don't think that command is available under gutsy but xrandr --prop gave the following:

```
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 1280 x 720
VGA disconnected (normal left inverted right)
TMDS-1 connected 1280x720+0+0 (normal left inverted right) 640mm x 360mm
        EDID_DATA:
                00ffffffffffff00410c08d001010101
                08100103804024780a3eb8a755459d25
                14484c21080001010101010101010101
                010101010101011d8018711c1620582c
                250080682100009e011d007251d01e20
                6e28550080682100001e000000fc004d
                41472033374d46787878440a000000fd
                00303e0f3209000a2020202020200193
   1280x720       60.0* 
   800x600        60.3  
   640x480        60.0  
```

---

### Post by iramhernandez on 2008-02-13
A quick update to a previous posting with my hacked up xorg.conf.  I've been able to get my graphics working by simply adding a "Virtual" setting in the "Display" section of and a virgin xorg.conf. See chunk of code below.

SubSection "Display"
	Depth	24
	Virtual	1280	720
	Modes		"1280x720@60"	"1280x720@50"
EndSubSection

The nearest I can tell is that this is forcing xrandr to ignore resolutions higher that 1280 720 which for some reason don't work.  My problem was that my system was trying to do 1920 x 540.  My HDTV actually does 1920 x 1080 Interlaced.  I  still havent been able to get it to work at that resolution.  Also, I have a very annoying problem with overscan still.  I haven't figured out what to do about that yet.  Anybody familiar with overscan + intel chipsets?

---

### Post by theacoustician on 2008-02-14
> **iramhernandez said:**
> A quick update to a previous posting with my hacked up xorg.conf.  I've been able to get my graphics working by simply adding a "Virtual" setting in the "Display" section of and a virgin xorg.conf. See chunk of code below.

SubSection "Display"
	Depth	24
	Virtual	1280	720
	Modes		"1280x720@60"	"1280x720@50"
EndSubSection

The nearest I can tell is that this is forcing xrandr to ignore resolutions higher that 1280 720 which for some reason don't work.  My problem was that my system was trying to do 1920 x 540.  My HDTV actually does 1920 x 1080 Interlaced.  I  still havent been able to get it to work at that resolution.  Also, I have a very annoying problem with overscan still.  I haven't figured out what to do about that yet.  Anybody familiar with overscan + intel chipsets?
Try reading this : [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7667/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7667/README.txt)

However, that actually may be the correct output.  It depends on how your TV interprets interlacing.  If you think about it, when you have your output at 1920x540 @ 60Hz, you're sending the same amount of data as 1920x1080 @ 30 Hz (ok 29.97Hz, but what's a little rounding between friends?).  If your TV knows that it needs to take 1 frame from the 60Hz stream and parse it into a field and so on and so forth, that can work.  That's not standard, but I have actually seen that.

You can also try doing what this guy did [http://www.nvnews.net/vbulletin/showthread.php?t=102563](http://www.nvnews.net/vbulletin/showthread.php?t=102563)

---

### Post by brundles on 2008-02-21
> **iramhernandez said:**
> A quick update to a previous posting with my hacked up xorg.conf.  I've been able to get my graphics working by simply adding a "Virtual" setting in the "Display" section of and a virgin xorg.conf. See chunk of code below.

SubSection "Display"
	Depth	24
	Virtual	1280	720
	Modes		"1280x720@60"	"1280x720@50"
EndSubSection

The nearest I can tell is that this is forcing xrandr to ignore resolutions higher that 1280 720 which for some reason don't work.  My problem was that my system was trying to do 1920 x 540.  My HDTV actually does 1920 x 1080 Interlaced.  I  still havent been able to get it to work at that resolution.  Also, I have a very annoying problem with overscan still.  I haven't figured out what to do about that yet.  Anybody familiar with overscan + intel chipsets?

Only just had a chance to try this - it enables the DVI cable nicely but comes back with an 800x600 screen and no options to change the screen resolution. Both the resolutoin and refresh rate data is empty when checking the Screen Resolution options. Any thoughts?

*Edit: * The plot thickens - when using the VGA cable, it's responsive to xrandr (i.e. I can change resolutions) yet while using the HDMI and DVI adapter, xrandr lists 3 modes available (1280x720, 800x600 and 640x480) but doesn't actually do anything in response to any commands. It thinks it has done (or at least it doesn't give any errors, and using the --verbose option doesn't give any additional output.

---

### Post by dustobub on 2008-02-26
Any update on HDMI audio, heard it was patched in 1.0.16? I want 8 channel lpcm over HDMI.

---

### Post by dustobub on 2008-02-26
Just read through the bug report. Apparently 2 channel LCPM is working over HDMI, however, there is absolutely no support for > 2 channel LPCM audio in Alsa because SPDIF was never able to handle more than 2 channels. Hopefully this gets some attention soon as it is a very important feature to many HTPC users.

One extremely interesting thing to note is the fact that we might see bitstream passthrough of DTS-MA and Dolby TrueHD in linux before windows. Manufacturers won't be allowing bitstream transporting in windows until HDMI is provides a fully protected path (not soon). In Linux we won't have that restriction, all that should be required is a chipset that can do HDMI audio, and then getting some dev support to get the passthrough working (which I wouldn't think is too hard, especially as decoding support for TrueHD/E-AC3 is essentially ready) . As for DTS-MA/DTS-HD, they each have an embedded lossy DTS track on them, so at least for now, we could just decode the lossy part, and then hopefully down the line Libcda might be able to decode the lossless parts of track.

---

### Post by wjlonien on 2008-02-27
> **dustobub said:**
> Apparently 2 channel LCPM is working over HDMI, however, there is absolutely no support for > 2 channel LPCM audio in Alsa because SPDIF was never able to handle more than 2 channels.

Hm. That means that if someone really wants to use this - or any other mb - as a HTPC, we have to connect to the receivers through (possibly humming) analog audio outputs?

Has someone actually tested this, and got 7.1 (or 5.1) working?

TIA,
Wolfgang

---

### Post by jcmiguel on 2008-03-03
> **theacoustician said:**
> Dual monitors for a Myth box?:confused:

I am on the market for a mythtv compatible mobo and I need dual head. The reason is that I usualy have a 22in monitor attached for tv and a projector for eventual movies:popcorn:. Tv has higher resolution than monitor and dual head is the answer. I currently have to endure vista on a gigabyte 965P rig with a x1650 ATI because I cannot put a dual head to work properly. If this board can do the trick I will buy it

---

### Post by laga on 2008-03-03
> **jcmiguel said:**
> The reason is that I usualy have a 22in monitor attached for tv and a projector for eventual movies:popcorn:. Tv has higher resolution than monitor and dual head is the answer

Same problem here: I've got a 22" TFT for working and my old CRT TV for TV. 

Do you want to use both displays simultaneously, eg work on your monitor and watch a movie on the projector at the same time? When I tried to do that with my Nvidia card, it'd never work well because I never got two independent displays working, they were always coupled together in some way (eg using nvidia's twinview) which resulted in a few problems for me:

* focus issues: pop-up menus in MythTV don't work properly if another window is focussed.
* aspect ratio problems: my TFT is 16:9 and my TV is 4:3. When you tried to use zoom modes in MythTV, the resulting aspect ratio would be very weird.

I solved the problem by adding a second VGA card and configuring a multiseat setup (-> google).

IIRC, (some) ATI cards can do truly independent X servers on their heads, but one of the X servers won't have hardware acceleration. I'm not sure how the radeonhd driver handles this or if it has changed in the ati driver.

Of course, if you just use one display at a time you likely you won't have such problems, especially if you switch off one of them (eg using xrandr).

Just my 0.02€,

Michael

---

### Post by brundles on 2008-03-08
For those like me waiting on the tearing bug, it looks like there might now be a [fix available](http://bugs.freedesktop.org/show_bug.cgi?id=11311).

I'm looking at trying this today and will post back when it's up and running.

*Edit:* Well first impressions look promising :). I'll be interested to hear back from other people who have tried it too.

---

### Post by brundles on 2008-03-13
According to the two bug reports included in this thread by herodiade, both the Xv tearing and DVI output are now fixed.

I've got the Xv tearing fixed now and mplayer plays lovely hi-def x264s without any tearing. However the driver still doesn't play with the HDMI-DVI convertor.

Has anybody had any success with the new driver build and HDMI?

---

### Post by brundles on 2008-03-13
At the risk of being accussed of excessive thread bumping, [article on Phoronix](http://www.phoronix.com/scan.php?page=news_item&px=NjM4OQ) looks interesting for the better EXA support :)

---

### Post by niceguyeddie on 2008-03-29
If I understand correctly the video tearing fix for intel's G35 chipset is to use the overlay video port as opposed to the textured video port.  It possible to use the overlay video port for streaming video while running mythtv or can this only be done with mplayer?

Thanks!

---

### Post by brjhaverkamp on 2008-03-31
Hello all,

I 'm looking for this MB to be the heart of my next (HDTV) HTPC. 
It is HDTV capable and well supported under linux.
The only catch is, I can't seem to find a good case to go with it.

I need 2 slots in the back to fit a DVB-C card and the CAM module.
Hifi width (42 cm) and black is a nice bonus.

The Silverstone LC04 looked perfect, but then I discovered that the PCI slot in this Mainboard is not in the right position for the LC04.

Does any of the readers here have a good alternative( in terms of case or MB)

Much appreciated,

Bert

---

### Post by RWN on 2008-03-31
Hello,

have a look her.

[http://www.nmediapc.com/]("http://www.nmediapc.com/")

---

### Post by niceguyeddie on 2008-03-31
> **niceguyeddie said:**
> If I understand correctly the video tearing fix for intel's G35 chipset is to use the overlay video port as opposed to the textured video port.  It possible to use the overlay video port for streaming video while running mythtv or can this only be done with mplayer?

Thanks!

Why yes, yes there is.  Try this patch for the myth source that some guy named Tino came up with:

```
wget http://tikei.de/50_skip_intel_textured_video.dpatch
```

Apply patch like so

```
cd mythtv
patch -p1 < {path to patch}/50_skip_intel_textured_video.dpatch
```

I tried it on the latest svn and it works!
Thank you Tino!

---

### Post by brundles on 2008-04-26
Has anybody tried rebuilding the LAN drivers [previously posted](http://ubuntuforums.org/showpost.php?p=4212499&postcount=57) on Hardy?

There seems to be something in Hardy that causes several things to fail building with errors along the lines of:
```
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/opt/htpc/src/l1-linux-v1.2.40.2/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/opt/htpc/src/l1-linux-v1.2.40.2/src/Makefile". Fix it to use EXTRA_CFLAGS. Stop.

```

Rooting around on here there seems to be something Hardy related rather than specific to these drivers, but I wondered if anyone had had any success building the drivers to get WOL working?

---

### Post by superFerra on 2008-05-02
Hello,
anybody using an ASUS P5e-vm HDMI (G35 / Intel X3500) with Hardy 8.04??
Is it working for you? I'm having trouble with xorg. The system hangs when logging out or randmoly when starting GDM...
Any idea?
I bought this mobo the build my own HTPC but i'm having problems of system reliability ...
Any suggestion appreciated

---

### Post by brundles on 2008-05-02
> **superFerra said:**
> Hello,
anybody using an ASUS P5e-vm HDMI (G35 / Intel X3500) with Hardy 8.04??
Is it working for you? I'm having trouble with xorg. The system hangs when logging out or randmoly when starting GDM...
Any idea?
I bought this mobo the build my own HTPC but i'm having problems of system reliability ...
Any suggestion appreciated

I'm using this with Hardy (and now have WOL working again after changing the driver code) and I know some of the other posters were also using it during the beta development without any issues.

Have you checked some of the other hardware you've got through these forums to make sure it's all OK?

---

### Post by superFerra on 2008-05-02
Thanks for your reply,

My hardware is quite simple:
-Asus P5E-VM HDMI (bios 0503)
-Intel Core 2 Duo E8200
-Western Digital SATA2 Hdd
-IDE DVD-Writer by LG
-Dign 15e case (with VFD attached via internal USB connector)
- Technotrend 3200 DVB-S2 card (not recognized because i've not installed multiproto drivers yet).
It's hooked via VGA to an Epson HD-Ready projector.

I've tried 64 and 32 bit without success since beta release. The only thing that i'm not changing every re-installation is the /home partition (could be the problem?)

I think it's a bios configuration issue. Can you tell me your BIOS settings please?

Thanks again

---

### Post by brundles on 2008-05-02
> **superFerra said:**
> Thanks for your reply,

My hardware is quite simple:
-Asus P5E-VM HDMI (bios 0503)
-Intel Core 2 Duo E8200
-Western Digital SATA2 Hdd
-IDE DVD-Writer by LG
-Dign 15e case (with VFD attached via internal USB connector)
- Technotrend 3200 DVB-S2 card (not recognized because i've not installed multiproto drivers yet).
It's hooked via VGA to an Epson HD-Ready projector.

I've tried 64 and 32 bit without success since beta release. The only thing that i'm not changing every re-installation is the /home partition (could be the problem?)

I think it's a bios configuration issue. Can you tell me your BIOS settings please?

Thanks again

What memory are you using?

I had to tweak the BIOS voltage settings on the OCZ memory I have - I can dig out what it need to be set to but you might want to check that for your specific brand of memory.

---

### Post by superglide on 2008-05-03
> **superFerra said:**
> Thanks for your reply,

My hardware is quite simple:
-Asus P5E-VM HDMI (bios 0503)
-Intel Core 2 Duo E8200
-Western Digital SATA2 Hdd
-IDE DVD-Writer by LG
-Dign 15e case (with VFD attached via internal USB connector)
- Technotrend 3200 DVB-S2 card (not recognized because i've not installed multiproto drivers yet).
It's hooked via VGA to an Epson HD-Ready projector.

I've tried 64 and 32 bit without success since beta release. The only thing that i'm not changing every re-installation is the /home partition (could be the problem?)

I think it's a bios configuration issue. Can you tell me your BIOS settings please?

Thanks again


I am seeing the same problem with log off.
-Asus P5E-VM HDMI (bios 0405)
-Intel Core 2 Duo E8400
-4GB RAM (2x2)
-Seagat SATA2 Hdd
-DVI monitor

The machine runs for days with no problems.  I can transcode with both CPUs at 100% for hours.  However, trying to log off results in a hung machine most of the time.  It is really dead, not just X -  I can't ssh in from another machine.  

Also, virtual consoles are broken.  I get just a blank black screen, but I can return to X OK.

My workaround is don't log off, shut down is reliable.

---

### Post by superFerra on 2008-05-03
@superglide:
I read that the bios you're running is buggy. Now tht 505 release is out, you should update it.
I'm using OCZ ram too:
OCZ OCZ2T8002GK 2048Mb. (Kit 2x1Gb) DDR2 800 PC6400 Titanium EPP Ready 4-4-4-15 1T
Could be a RAM issue??

---

### Post by snow00 on 2008-05-04
Hey guys...I'm a linux noob and had some questions about the P5E-VM HDMI.

I have 8.04 installed and everything is rockin...but i get some nasty overscan and I'm not sure which route to fix it. driver? settings? When i messed with the display settings I lost 1920x1080 but fixed the over scan. I am currently downloading the Asus linux drivers and hopefully that will fix it, but if anyone has any suggestions that would be greatly appreciated! thanks!

specs:
P5E-Vm HDMI
GSkill 4GB F2-6400CL5D-4GBPQ
C2D 6550


Samsung HLT5687SX DLP

thanks alot guys!

---

### Post by superFerra on 2008-05-04
It could be a projector setting to be adjusted. For example DVI-level or output-scaling.
These settings are on my projector that is an epson but i think that your DLP isn't much different ...
good luck

PS: Are you using the correct modeline? Is your native resolution perperly hoocked?

---

### Post by superglide on 2008-05-04
> **superFerra said:**
> @superglide:
I read that the bios you're running is buggy. Now tht 505 release is out, you should update it.
I'm using OCZ ram too:
OCZ OCZ2T8002GK 2048Mb. (Kit 2x1Gb) DDR2 800 PC6400 Titanium EPP Ready 4-4-4-15 1T
Could be a RAM issue??

You may have a RAM issue, but it seems unlikely that it would only cause a problem when logging out.  Since logging out restarts gdm, I suspect the problem is in the restarting X somehow.

I've been running the processor/memory pretty hard for days at a time.  Both transcoding large amounts of audio, and compiling with gcc.  Building a linux kernel is one of the best memory tests there is, because the compiler uses pointers for everything, and a bad pointer is likely to point to memory that isn't mapped.  A signal 11 results in that case.

For RAM I'm using 
Crucial 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory - Retail 
part # CT2KIT25664AA80E 

Asus seems to be having a problem today.  I can download BIOS 503, but not 505.  Since you are having similar problems with 503, I'm going to wait until I can get 505 to try it.

I'm going to try the VGA connector instead of HDMI just to see if it matters.

---

### Post by superglide on 2008-05-06
VGA is no different than HDMI.  Both have the same problem.  Booting numerous times revealed that sometimes X doesn't start with VGA or with HDMI.

BIOS 505 made no difference.

There are some differences in Xorg.0.log.

---

### Post by vincentroberge on 2008-05-08
I have the same problem.  Upon boot up, after the scroll bar, I get a black screen.  Something weird I notice is that if I do Alt+F1 during the boot up to see the outputs instead of the scroll bar, the X will start correctly.  I have a the following hardware:
Asus P5E-VM HDMI
4 Gb A-data RAM
4 Sata Hdd
Intel E8400

I also noted that my xorg.conf file contains the following which is odd.

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by niQo on 2008-05-11
> **superFerra said:**
> Hello,
anybody using an ASUS P5e-vm HDMI (G35 / Intel X3500) with Hardy 8.04??
Is it working for you? I'm having trouble with xorg. The system hangs when logging out or randmoly when starting GDM...
Any idea?
I bought this mobo the build my own HTPC but i'm having problems of system reliability ...
Any suggestion appreciated

I have exactly the same problem with a fresh install of hardy. I have no problem with Archlinux.
My hardware :
Asus P5E-VM HDMI
4 Gb G-Skill F2-6400CL5D-4GBPQ (CL5-5-5-15) (2x2Gb)
1 Sata Samsung HDD
C2D Intel E8400
RGB monitor (DVI don't work)

Edit :
I upgraded to bios 505 and the problem seems to be resolved : my system no more hangs on shutdown or reboot.

---

### Post by Trollslayer on 2008-05-11
> **theacoustician said:**
> [http://usa.asus.com/products.aspx?l1=3&l2=11&l3=584](http://usa.asus.com/products.aspx?l1=3&l2=11&l3=584)

It has HDMI out onboard and promises "Full HD 1080p Multimedia Home-Theater Entertainment".  My question is does anyone have any experience with the board?  Are there proper drivers available?  I'd love to hear from any owners as I'm seriously considering nabbing this for a Myth client.

Depending on how complex the content is, codec, frame rate etc. there can be problems.
50Hz is easier then 120Hz and a sollid red screen is simpler than wildlife footage.

---

### Post by kevinl on 2008-05-11
The motherboard looks good but the real test will be whether there are Linux drivers available to take advantage of the abilities of the hardware, particularly the display adaptor.  I have now successfully put MythBuntu onto a number of PCs, a Dell desktop being one of them with an AMD dual core 45Watt chip.  The board looks to be a micro-ATX.  I mention this because we have been playing with VIA ITX boards and so far have had no luck with them because of driver problems.  There isn't a Chrome driver that allows us to take full advantage of the capabilities of the hardware in terms of on-board, in chip, decompression of the digital stream.
Our reasons for looking at an ITX type board is that the cases in which the ATX generally fit, although being very suitable for a desk in the study, are too big to go into the lounge room.

---

### Post by trouble1313 on 2008-05-11
As of right now, I don't think I can recommend this motherboard for a Linux based HTPC. While it runs perfectly under Vista (I was amazed at how easy it was to get the thing installed and playing blueray with all the horror stories out there!), video issues are driving me crazy. When it works, it's fine...the unfortunate thing is that 50% of the time, it just doesn't display anything once X kicks in (sometimes hanging the machine altogether) or it gives a strange flickery display. Sometimes rebooting helps. Sometimes, rebooting hangs the machine altogether, sometimes it comes back up with the exact same flicker. I don't see anything in the Xorg log saying that anything is wrong. I also can't tie it down to being a warm reset issue...it commonly screws up after a complete unplugged reboot. I'm torn whether to throw an NVidia card that I have in or do a complete compile of the latest intel driver. It seems Hardy is 1 driver rev back? I can't seem to figure out what the latest actually is since the intellinuxgraphics.org page just talks about checking out the latest in the tree but I guess it's 2.22? Hardy has 2.2.1. My xorg.conf seems to be completely ignored and it does whatever it wants to do. Anyone have things working consistently with HDMI?
-Trouble

---

### Post by xiouxin on 2008-05-13
I've solved this problem by manually compiling & installing
20080422-announced intel driver:
[http://lists.freedesktop.org/archives/xorg/2008-April/034864.html]("http://lists.freedesktop.org/archives/xorg/2008-April/034864.html")

This new driver gives good quality & runs stable on my machine,
no dead-hang any more. I'm testing to run mplayer with new libIntelXvMC.so
now.

Here's my environment for your reference:
BIOS version: 0505
CPU: Intel E8200
RAM: Transcend 2G
Distribution: Slackware 12.1

[updated info]
XvMC is not supported on G35 chipset.

---

### Post by trouble1313 on 2008-05-13
Xiouxin,
    Did you just compile that one driver or did you do the whole kit with gart,drm,kernel driver etc?

Thanks for the heads up!
-Trouble

---

### Post by xiouxin on 2008-05-13
Trouble1313,
I just removepkg original xf86-video-intel-2.2.1 that Slackware 12.1 installed,
then `configure/make/make install' the new driver, startx and close X as many times
as I like, no more dead-hang!

Here's my configure options:
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
            --infodir=/usr/info --mandir=/usr/man --disable-static --with-pic
(as you can see, nothing special)

This new driver installs /usr/lib/libIntelXvMC.*
I've tried this in my /etc/X11/xorg.conf:
        Option    "XvMC"    "true"
(this is new option, see `man 4 intel')

/var/log/Xorg.0.log show XvMC-related:
(**) intel(0): Intel XvMC decoder enabled
(**) intel(0): Failed to probe XvMC driver
(so, we're not lucky here with G35)

My another box equiped with G33 show this:
(**) intel(0): Intel XvMC decoder enabled
(II) intel(0): [XvMC] i915_xvmc driver initialized.
(later I will do entensive tests to see what intel has enhanced with XvMC?)

---

### Post by trouble1313 on 2008-05-13
Awesome, Thanks greatly Xiouxin! I will give it a try in a bit.

-Trouble

---

### Post by xiouxin on 2008-05-14
[test report]

1. set "AccelMethod" to "EXA" led to backtrace with "extmod" when playing
   some files. change to "XAA" solve this problem.

2. with driver 2.3.0, output via HDMI to my fullHD 37" TV still shift the
   screen rightward about 1.5 cm.
   This problem also exists in my another G33 box with my BenQ SH3741 TV,
   too bad to our linux camp! (M$ Windows display correctly with HDMI)

   According to this:
  [http://intellinuxgraphics.org/community_testing.html]("http://intellinuxgraphics.org/community_testing.html")
   in "Known driver issues" part, SDVO HDMI is not well supported yet.

3. about XvMC, this driver only support mpeg2 decoding off-load, 
   with more and more files encoded with new codecs, there's little 
   meaning to use this feature. besides, I test one DVD with this:
   (a) mplayer -vo xvmc -vc ffmpeg12mc dvd://2
   (b) mplayer -vo xv dvd://2
   guess what? the CPU usage stable at 13% with (a), and
   stable at 9% with (b)!

As of right now, I agree with Trouble1313, I would not recommend this board.

---

### Post by trouble1313 on 2008-05-14
Well I went ahead and compiled the 2.3.0 and found the following:

System doesn't hang when restarting GDM anymore (yay!)

I still don't get virtual consoles (with alt+F2 for example) and if I try to use one, display is gone until reboot.

Still comes up commonly with no display at all though it's trying to do something...Display shows the input attempting to sync over and over...never gets anywhere.

I do not have a case where the display is shifted.

I am indeed getting complaints about SDVO:

(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): SDVO device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.

<Edit> Ugh...still get the flicker problem too. Man oh man.
Also finding that it doesn't output 1920x1080 every time! One this boot, it's at 1920x1045. Last boot (with flicker) it was 1920x1079. Where the hell is it coming up with this and the bigger question, why isn't it consistent?!

<Edit2> Ok, making a little more sense now. After looking at the bug reports, it seems that indeed, the thing sets up the screen off by a seemingly random number of pixels. I am guessing that depending on just how many pixels it's off, my projector does different things. If it's within a small number of pixels, it flickers. If it's off by more than that, it never is able to sync at all and remains blank or keeps trying to lock on. Of course 1-4 tries or so, it comes up correctly at 1080P. Indeed does not seem to be a fix for it at this time.

So I guess it's not worse :)
But it's not really 'fixed' :(

For the record, output is via HDMI to a 1080P front projector.

-Trouble

---

### Post by erod20 on 2008-05-16
trouble1313

Can you post the steps you did to compile the new intel drivers?

---

### Post by trouble1313 on 2008-05-16
All I did was what Xiouxin said to do:


Download the source, uncompress it and cd into the directory and do:

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
--infodir=/usr/info --mandir=/usr/man --disable-static --with-pic


You will need several prerequisite packages, primarily '-dev' packages for Xorg and supporting libraries. When you run configure it will tell you what is missing. You can go into Synaptic and find the packages listed. Again, you'll need the '-dev' versions of the packages. 

Once you have all the needed dev packages and configure finishes, just run 'make'
After it compiles, remove xf86-video-intel-2.2.1 and then do a make install and restart gdm or reboot.

That's it.

---

### Post by xiouxin on 2008-05-19
Two news:
1. BIOS 0506 is out.
2. xf86-video-intel-2.3.1 was released 7 days ago, see this:
   [http://lists.freedesktop.org/archives/xorg/2008-May/035318.html]("http://lists.freedesktop.org/archives/xorg/2008-May/035318.html")

Here's my test result:
"dead-hang" come back again!

Since I upgraded the above two new stuff altogether, I'm not 100% sure
which one is to blamed. I did this:

(1). downgrade BIOS to 0505, and gave xf86-video-intel-2.3.1 a try.
     bad luck! X dead-hang randomly.
(2). uninstall $INTEL-2.3.1; back to $INTEL-2.3.0; reboot, upgrade BIOS
     to 0506, now X can start/restart/log-off without problem.

So, it's obvious new driver cracked my system/environment.
There's new option "LVDSFixedMode" in $INTEL-2.3.1, unfortunately
I got no chance to try it.

---

### Post by trouble1313 on 2008-05-19
Well, I'm not messing with it quite yet I think. I've moaned about NVidia and their whacked inital-release drivers in the past, but these Intel ones are really pretty bad. This is not a new chipset anymore and these drivers are still terrible. Vista is getting much more screen time on my HTPC these days because I'm tired of restarting X five times before it comes up right.

-Trouble

---

### Post by BorisBas on 2008-06-04
Anyone tried what this patch does?

[http://lists.freedesktop.org/archives/xorg/2008-June/035883.html](http://lists.freedesktop.org/archives/xorg/2008-June/035883.html)

---

### Post by niQo on 2008-06-05
Hi, I don't have tried this patch, but I have compiled intel drivers from git source today and HDMI is working now ! (It never works before with previous drivers and ASUS P5E-VM) 
I think hdmi problem was related to this bug : [http://bugs.freedesktop.org/show_bug.cgi?id=15766](http://bugs.freedesktop.org/show_bug.cgi?id=15766)

---

### Post by brundles on 2008-06-07
> **niQo said:**
> Hi, I don't have tried this patch, but I have compiled intel drivers from git source today and HDMI is working now ! (It never works before with previous drivers and ASUS P5E-VM) 
I think hdmi problem was related to this bug : [http://bugs.freedesktop.org/show_bug.cgi?id=15766](http://bugs.freedesktop.org/show_bug.cgi?id=15766)

Just downloaded the current git source and built it - and HDMI still doesn't work. That said, given the behaviour I saw with the VESA driver and previous differences in resolutions when trying a flat panel monitor instead of the TV that the PC is hooked up to I'm more inclined to blame the TV at this stage for my particular setup.

---

### Post by BorisBas on 2008-06-13
I just noticed that if you disable the sound card in Bios (Current, 0405), the motherboard hangs doing "Checking NVRAM..." forever. At least mine does... slightly annoying.

---

### Post by jakeofspades on 2008-06-17
Hmmm :/ I've been reading this thread in the hope that a solid intel driver will be released - the hanging startups is really bugging me after a while. I'm just gonna buy a graphics card...

---

### Post by brundles on 2008-06-17
> **jakeofspades said:**
> Hmmm :/ I've been reading this thread in the hope that a solid intel driver will be released - the hanging startups is really bugging me after a while. I'm just gonna buy a graphics card...

What sort of hanging are you seeing and when?

The drivers that shipped with Hardy seemed better with the board than those shipping previously, but I've also not had any issues with the svn/git (can't remember which they use) build on Hardy either.

HDMI to DVI still doesn't work for me but I'm pretty sure that's the TV rather than the driver as HDMI to HDMI works flawlessly.

---

### Post by BorisBas on 2008-06-17
Did an install last weekend. 

VGA out would somtimes work flawlessly for many hours. Then, other times, the screen would go black after a few minutes - but could be restored for another few minutes by switching to a console, and then switching back to X. Third behaviour was that the driver would just lock up the computer completly when starting X at boot.

I switched to HDMI on Saturday, and had a descent picture that would jump slightly every 4 seconds. 

Then some time later that Saturday or on Sunday a new version of the intel driver was released that fixed the jumpy behaviour. Except for a small purple line at the bottom that shows up only sometimes I have not had a single problem since.

---

### Post by jakeofspades on 2008-06-17
Well - The video isn't bad, I shouldn't complain really it's pretty well supported. However I find the system hangs after the Ubuntu loading bar, before the login. This happens fairly frequently (Using Asus P5e-vm HDMI just to clarify)

My monitor's connected via VGA and everything appears to work at first. However - GIMP struggles if I do something graphics-hefty and 3D games don't work too well. Under normal circumstances I'd be happy with the performance - I watch TV on it fine. Buuut - this is a new computer build and it's pretty powerful so I don't really want these bugs.

---

### Post by jpeeters on 2008-06-17
> **jakeofspades said:**
> ...l so I don't really want these bugs.

Did you try the latest git sources? Those are working fine on my machine (no more flickering)!

---

### Post by jakeofspades on 2008-06-17
Is that essentially adding these sources?
```

$ git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
$ git-clone git://anongit.freedesktop.org/git/mesa/drm
$ git-clone git://anongit.freedesktop.org/git/mesa/mesa

```

---

### Post by niQo on 2008-06-21
jakeofspades :
If you don't want to build latest driver from source, you can try the 'ubuntu intrepid package', I'm using version 2.3.2 and it works fine. (no more hangs)

for amd64
[http://packages.ubuntu.com/intrepid/amd64/xserver-xorg-video-intel/download](http://packages.ubuntu.com/intrepid/amd64/xserver-xorg-video-intel/download)

for i386
[http://packages.ubuntu.com/intrepid/i386/xserver-xorg-video-intel/download](http://packages.ubuntu.com/intrepid/i386/xserver-xorg-video-intel/download)

---

### Post by craiga on 2008-07-16
Would you guys reccomend this board now? with the new driveres and bios updates?

Looks perfect and I have been having trouble with my cheap option of Inno3d 7100/630i over HDMI.

Craig

---

### Post by alain_sat on 2008-07-17
I still don't know if it's the perfect motherboard buat at least It seems to do all that's necessary.
i was able to play without any trouble 1080p under Ubuntu 8.04.
I noticed that changing from monitor did change a lot.
i use a Samsung T200HD at 1680 x 1050.
I ahve a small trouble with the HDMI output as the screen is not perfectly centerd, but that was before so don't know what i changed.
The convertor from HDMI to DVI does absolutely work because it's just a mechanical piece it's not possible not to work but it's too have and you need to place something under it.
So if it doesn't work for you, check your cable and your screen.

My strugle now is to get my dvb s2 technotrend TT S3650 CI work under Ubuntu because that's what this HTPC is meant to; replace sat receiver.

---

### Post by BorisBas on 2008-07-21
Sound over HDMI is still not fully working, though. Stereo audio in results in only left channel out according to the bug reports at ALSA. Hopefully that is being worked on.

Do not know what happens if you shove an ac3 stream over HDMI.

---

### Post by froghunter on 2008-07-23
A slight bump, since I am two steps from getting this board. So to confirm, no luck on decent audio over the HDMI (still has SPDIF), even in Hardy, and it appears to be a an ALSA issue? I appreciate any input from all of you guys who have been running on this board since January (or later).

---

### Post by rkstech on 2008-07-24
> **jpeeters said:**
> I am running 1920 x 1080 on a sony kdl-40w3000 (1080p capable). Everything went fine with the standard ubuntu install (except sound output).


I also had the same problem with the sound thro' HDMI. After some R&D figured out the following. 

1. Do what is needed to enable ALSA
2. If using HDMI for audio - then enable the ICxxxx in volume control switches.
1. System->Pref->Sessions->Startup Programs - Disable the pulseaudio related process.
2. System->Pref->Sessions->Startup Programs - add a new one with command "killall pulseaudio"
4. Had to choose a default sound from System->Preferences->Default Sound.
   Select HDMI.
   This generates a file under a hidden dir (forgot the path/name)
5. System->Pref->Sound choose the audio over HDMI.

Now at this point u will not still hear the audio with the test button.
Might be because of this bug. The file I had mentioned generated un the hidden folder for default sound has the device id incorrect. In my case the the HDMI audio device number was #3 (alsa -l). So I had to manually fix this.

Once I did this the sound test works and all the sound is now directed thro HDMI.

May be this is a bug or may be I am not doing it correctly. But it works for me.

---

### Post by rkstech on 2008-07-24
The file to modify with the device id is ~/.asound.asound.conf

The line I changed for HDMI audio to work is 

defaults.pcm.device 3

It was 1 when saved GUI saves this file.

---

### Post by froghunter on 2008-07-25
rkstech, I appreciate the fix. when i get the board in, I will see how I can get Ubuntu up and running, but I am thinking just sticking XP on it (one laying around) and then doing a VM for a linux server I want on it too. Also, this way I may even get a little Blu-Ray action in the future (and XBMC runs equally well on either OS). Seriously though, thanks for the help, and if I do get it working, or ALSA gets fixes for this, I will stick with a Linux distro.

---

### Post by brundles on 2008-07-25
> **BorisBas said:**
> Sound over HDMI is still not fully working, though. Stereo audio in results in only left channel out according to the bug reports at ALSA. Hopefully that is being worked on.
I hope so too - having finally got audio working over HDMI (thanks to rkstech) it's a shame to only get half of the result :(

Do you have a bug id to link to?

---

### Post by craiga on 2008-08-02
Hi folks,

I noticed some of you had a similar problem to me, that is I can get 1080p easy enough using a modeline specified in xorg.conf, however the image is about 1" too high on my Panasonic 42PZ70.

How did you guys sort this?

Craig

---

### Post by rgsteele on 2008-08-02
> **craiga said:**
> Hi folks,

I noticed some of you had a similar problem to me, that is I can get 1080p easy enough using a modeline specified in xorg.conf, however the image is about 1" too high on my Panasonic 42PZ70.

How did you guys sort this?

Craig

Have you mad sure the "overscan" option on your TV is turned off?

---

### Post by brundles on 2008-08-02
Not had a chance to try it yet, but in the event that your TV doesn't have any overscan options (like mine) [this](http://ubuntuforums.org/showthread.php?t=796776&highlight=intel+overscan) might work - although it was originally for TV out rather than HDMI.

---

### Post by craiga on 2008-08-03
> **rgsteele said:**
> Have you mad sure the "overscan" option on your TV is turned off?

Over scan is off and aspect is set to 16:9, so the tv would appear to be setup right.

Has anyone else had to use the margin thing? or am i missing something in my xorg.conf?

Craig

EDIT:

Fixed!  It was the modeline...incase anyone is using this board on a Panasonic here is my xorg.conf.  Dont think they keyboard and mouse this is 100% yet, but it does display perfect 1080p with direct rendering lovelyness

```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        RgbPath      "/usr/share/X11/rgb"
        ModulePath   "/usr/lib64/xorg/modules"
        FontPath     "/usr/share/fonts/misc/"
        FontPath     "/usr/share/fonts/TTF/"
        FontPath     "/usr/share/fonts/OTF"
        FontPath     "/usr/share/fonts/Type1/"
        FontPath     "/usr/share/fonts/100dpi/"
        FontPath     "/usr/share/fonts/75dpi/"
EndSection

Section "Module"
        Load  "xtrap"
        Load  "extmod"
        Load  "glx"
        Load  "dri"
        Load  "dbe"
        Load  "record"
        Load  "type1"
        Load  "freetype"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "uk"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier  "dummy"
    Option      "Ignore" "True"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "MEI"
        ModelName    "PANASONIC-TV"
 ### Comment all HorizSync and VertRefresh values to use DDC:
        HorizSync    15.0 - 68.0
        VertRefresh  23.0 - 61.0
        Modeline   "1920x1080_50" 148.500 1920 2448 2492 2640 1080 1082 1088 11$
#       Modeline   "1920x1080_30" 74.250 1920 2008 2052 2200 1080 1084 1094 112$
        Option       "PreferredMode" "1920x1080_50"
        Option       "DPMS" "True"
        Option       "enable" "True"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI" "TRUE"                # [<bool>]
        Option     "NoDDC"                      # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces" "7"          # <i>
        #Option     "PageFlip" "True"           # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "965 G1 Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
        Option      "monitor-VGA" "dummy"
        Option      "monitor-TMDS-1" "Monitor0"
        Option      "RenderAccel" "TRUE"
        Option      "AccelMethod" "XAA" ##"EXA" #"XAA"
        Option "XAANoOffscreenPixmaps" "true"
        #Option "MigrationHeuristic" "greedy"
        #Option "UseFBDev"   "True"
        Option          "PageFlip" "True"
        Option          "TripleBuffer"  "True"
        Option          "FramebufferCompression"  "false"
        #Option          "LinearAlloc"             "16384"
        #Option          "Cachelines"              "2048"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Modes "1080p"
                Virtual 1920 1080
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "DRI"
        Group 0
        Mode 0666
EndSection

```

---

### Post by onesojourner on 2008-08-07
check this board out. it does not get any more perfect than this.

[http://www.popcornhour.com/onlinestore/index.php?pluginoption=catalog&task=info&item_id=7&main_id=0&category_id=](http://www.popcornhour.com/onlinestore/index.php?pluginoption=catalog&task=info&item_id=7&main_id=0&category_id=)
[IMG]http://www.popcornhour.com/userhome/onlinestore/b-110-b.jpg[/IMG]

Specification :

Connectivity

    * Bonjour
    * UPnP SSDP
    * DLNA
    * Windows Media Connect
    * Windows Media Player NSS
    * SMB
    * NFS
    * HTTP servers: myiHome, WizD, SwissCenter, MSP Portal, Llink, GB-PVR
    * BitTorrent P2P
    * NAS access : SMB, NFS, FTP

Web services

    * Video : YouTube, Veoh, Videocast, DLTV, Cranky Geeks, Bliptv, PodfinderUK, Vuze, Break Podcast, Revision 3, CNN The Larry King Podcast, CNN Anderson Cooper 360, The CNN Daily, CNN In Case You Missed It , NBC Meet The Press, NBC Today, CBS Face the Nation, NBC Nightly News, Mevio
    * Audio : Live365 Radio, iPodcast, Radiobox, ABC News, BBC Podcast, CNN News , Indiefeed, Jamendo
    * Photo : Flickr, Picasaweb
    * RSS feed : Bloglines, Yahoo! Weather, Yahoo Traffic Alerts, Traffic Condition, Cinecast, Yahoo! News, MSNBC News
    * Peer-to-peer TV : SayaTV
    * Internet Radio : Shoutcast

Media files supported

    * Video containers:
          o MPEG1/2/4 Elementary (M1V, M2V, M4V)
          o MPEG1/2 PS (M2P, MPG)
          o MPEG2 Transport Stream (TS, TP, TRP, M2T, M2TS, MTS)
          o VOB
          o AVI, ASF, WMV
          o Matroska (MKV)
          o MOV (H.264), MP4, RMP4
    * Video codecs:
          o XVID SD/HD
          o MPEG-1
          o MPEG-2
                + MP@HL
          o MPEG-4.2
                + ASP@L5, 720p, 1-point GMC
          o WMV9
                + MP@HL
          o H.264
                + BP@L3
                + MP@L4.0
                + HP@L4.0
                + HP@L4.1
          o VC-1
                + MP@HL
                + AP@L3
    * Audio containers:
          o AAC, M4A
          o MPEG audio (MP1, MP2, MP3, MPA)
          o WAV
          o WMA
    * Audio codecs:
          o AC3
          o DTS
          o WMA, WMA Pro
          o AAC
          o MP1, MP2, MP3
          o LPCM
          o FLAC
          o Vorbis
    * Audio pass through : DTS, AC3, DTS-HD MA, DTS-HD HR, Dolby True HD, Dolby Digital Plus
    * Photo formats : JPEG, BMP, PNG, GIF
    * Other formats:  ISO, IFO
    * Subtitle formats : SRT, SMI, SUB, SSA

DRM

    * Cardea DRM (WMDRM-ND)

Chipset

    * Sigma Designs SMP8635

Memory

    * 256MB DDR SDRAM, 32MB Flash

Audio/Video outputs

    * HDMI v1.3a (up to 1080p)
    * Component Video (up to 1080p)
    * S-Video
    * Composite Video
    * Analog Stereo Audio
    * S/PDIF Optical + Coaxial Digital Audio

Interface

    * 4x USB 2.0 host
    * 2x SATA
    * 1x IDE
    * Mini PCI slot for WiFi

Others

    * Mini ITX form factor
    * Real time clock
    * External IR receiver

Network

    * Ethernet 10/100

Package Content

    * Popcorn Hour B-110 Baseline (Motherboard)
    * 1.5M length HDMI cable
    * Remote Control with 2 "AAA" batteries
    * External IR receiver
    * 2x SATA cable
    * 1x IDE cable
    * Back panel (166.25mm x 51.7mm x 0.4mm)
    * Quick start guide

---

### Post by rgsteele on 2008-08-07
> **onesojourner said:**
> check this board out. it does not get any more perfect than this.


Well, that's interesting, but as it appears to run its own proprietary OS, it's a bit off-topic for this thread...

---

### Post by BorisBas on 2008-08-08
These are the left-channel-only ALSA bug reports.

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3754](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3754)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2765](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2765)

---

### Post by BorisBas on 2008-08-09
> **BorisBas said:**
> These are the left-channel-only ALSA bug reports.

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3754](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3754)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2765](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2765)

It also appears those issues may require some cooperation with the x.org team, requiring kernel additions (to be able to establish when/what HDMI bandwidth is available for audio), although I have not read anything from the ALSA side confirming this state of affairs.

[http://lists.freedesktop.org/archives/xorg/2008-March/034122.html](http://lists.freedesktop.org/archives/xorg/2008-March/034122.html)

---

### Post by superFerra on 2008-08-14
> **niQo said:**
> jakeofspades :
If you don't want to build latest driver from source, you can try the 'ubuntu intrepid package', I'm using version 2.3.2 and it works fine. (no more hangs)

for amd64
[http://packages.ubuntu.com/intrepid/amd64/xserver-xorg-video-intel/download](http://packages.ubuntu.com/intrepid/amd64/xserver-xorg-video-intel/download)

for i386
[http://packages.ubuntu.com/intrepid/i386/xserver-xorg-video-intel/download](http://packages.ubuntu.com/intrepid/i386/xserver-xorg-video-intel/download)

Is there a way to install them flawlessy??
i've downloaded
xserver-xorg-video-intel_2.4.0-1ubuntu1_amd64.deb
but it complains about missing dependencies.. (libpciaccess0) even if it's installed. 
Where can i get 2.3.2 both i386 and amd64 versions of that driver??
Any help appreciated

---

### Post by BorisBas on 2008-08-14
> **superFerra said:**
> 
Where can i get 2.3.2 both i386 and amd64 versions of that driver??
Any help appreciated

[http://ftp.iasi.roedu.net/mirrors/ubuntulinux.org/ubuntu/pool/main/x/xserver-xorg-video-intel/](http://ftp.iasi.roedu.net/mirrors/ubuntulinux.org/ubuntu/pool/main/x/xserver-xorg-video-intel/)

Google is your penpal. =)

---

### Post by superFerra on 2008-08-22
Thanks mate but still doesn't works! It keeps on hanging!
Yesterday i've installed it from scratch (i kept only home partition)
After first reboot it hanged before login screen
rebooted into recovery mode and upgraded
second reboot hanged.
third worked and managed to install xserver-xorg-driver-intel-2.3.1 (removing xserver-xorg-driver-video-all and i810)
but nothing changed. If i logout it hangs at login screen.
when it hangs keyboard stops working and need hard reset.
I'm using the 64-bit on a P5E-VM HDMI Intel Core 2 Duo E8200 2Gb ram
I'm trying memtest but don't think it's the problem 7.10 works nicely.

Please help me

---

### Post by superFerra on 2008-08-24
ok seems to be solved.

i had to:

```

sudo apt-get remove xserver-xorg-video-all xserver-xorg-video-i810

```

then i had to download these packages (debian lenny):
xserver-xorg-video-intel: [http://packages.debian.org/lenny/xserver-xorg-video-intel](http://packages.debian.org/lenny/xserver-xorg-video-intel)

libdrm2: [http://packages.debian.org/lenny/libdrm2](http://packages.debian.org/lenny/libdrm2)

(choose you architecture)

finally
```

dpkg -i libdrm2.deb
dpkg -i xserver-xorg-video-intel.deb

```

and reboot. Tried few logout and it no more hangs ... seems very cool!!!

---

### Post by tuomi on 2008-09-22
I wanna start out with a big thanks to all who's been involved in this thread and other forums for making this work. After nearly tearing my hair out I found a solution working for me. My problem was not getting any sound out of the coax. After installing the realtek / ALSA package contained in the "Support Linux Drivers.zip" from Asus support site: [http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5E-V%20HDMI](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5E-V%20HDMI) it worked like a charm.

Now the reason I chose to not run the sound through HDMI was since vista I wasn't able to run the sound through HDMI when my projector wasn't running and just the monitor connected via the onboard VGA. I guess there isn't any change to this?

---

### Post by lyndonwhaite on 2008-10-12
Hi

I have very similar hardware and exactly the same problems as SuperFerra. SuperFerra i am wondering if you could tell me the current state of things for you?. I tried those new versions of libdrm and the intel driver that worked for you and it fixes the boot hanging issue and logout, however it creates another one where anything involving graphics is really slow like graphics acceleration is off.

Lyndon

---

### Post by superFerra on 2008-10-13
Try:
 
```

glxinfo | grep direct

```

and post the code

---

### Post by lyndonwhaite on 2008-10-13
Thanks SuperFerra your assistance is much appreciated.

```

$ glxinfo | grep direct
direct rendering: Yes

```

So currently if i install the 2.3 video driver it doesn't hang on start, but acceleration appears not to work. If i revert to the driver in the repository (2.2) i fix the acceleration and get the hangs again.

I can keep the newer libdrm package installed and it makes no difference.

Does any one know what changes where made between the 2.2 driver in the hardy repository and the one SuperFerra posted?

---

### Post by lyndonwhaite on 2008-10-13
Ok. So more trawling of google and now i realise its compiz. When i turn off compiz all sweet i can run full hd video with minimal cpu usage. When it is on even at the most minimal, everything else is crippled. Compiz obviously doesn't like my card.

---

### Post by BorisBas on 2008-11-10
Things may be moving again with regard to x/alsa and sound over hdmi:

[http://www.phoronix.com/scan.php?page=news_item&px=NjgzNg](http://www.phoronix.com/scan.php?page=news_item&px=NjgzNg)

---

### Post by superFerra on 2008-11-11
Does anybody tried 2.4 intel drivers?

---

### Post by qwerdy on 2009-01-24
Anyone got any new tips on a perfect HTPC motherboard?

---

### Post by froghunter on 2009-01-24
I don't vote for the Asus P5E-VM HDMI, or at least not with linux. The great things about the board won't work or a bit difficult to setup in most linux distros. I would decide what OS you want to use, and then work backwards from there with hardware compatability. Hell, the P5E-VM HDMI works better with OSx86 than linux, and of course works like a champ with windows.

Would be interested if someone came up with something though.

---

### Post by BorisBas on 2009-01-24
> **froghunter said:**
> I don't vote for the Asus P5E-VM HDMI, or at least not with linux. The great things about the board won't work or a bit difficult to setup in most linux distros. I would decide what OS you want to use, and then work backwards from there with hardware compatability. Hell, the P5E-VM HDMI works better with OSx86 than linux, and of course works like a champ with windows.

Would be interested if someone came up with something though.

Well, it takes a while, that is true. Graphics over HDMI seem to be working fine now. Sound is not quite there yet, but that was probably because it required kernel feature additions, not just a chip driver. However it seems 2.6.29 may fix that too.

However, I would like to check if anyone else has been getting syslog errors like these:

cmd 61/90:48:0f:aa:86/00:00:00:00:00/40 tag 9 ncq 73728 out
res 40/00:4c:0f:aa:86/00:00:00:00:00/40 Emask 0x10 (ATA bus error)

...that appears to be issues with the mainboard model itself? 

(having tested different psu:s, sata cables and ports, disks, kernels, 64/32 bits, ahci/ide mode, acpi=off, other ich9r mainboards, bios updates)

---

### Post by superFerra on 2009-02-26
Does anyone been able to use the motherboards graphics card to play smooth HD contents within mythtv?which driver are you using? I tried 2.5.1 but seemed to me slower than 2.4.2?
Any particula xorg.conf settings?
TIA

---

### Post by BorisBas on 2009-02-27
> **superFerra said:**
> Does anyone been able to use the motherboards graphics card to play smooth HD contents within mythtv?which driver are you using? I tried 2.5.1 but seemed to me slower than 2.4.2?
Any particula xorg.conf settings?
TIA

Currently running 2.4.1. Have never had as much as a hickup playing HD stuff over HDMI on this motherboard using an Intel E8400 in mythtv (mythbuntu). Mostly 720p but also a few 1080p. No particular xorg.conf settings.

---

### Post by limanoit on 2009-04-15
hi guyts i am using intel 2.6 on ubuntu 9.04 and can not get audio out over hdmi .. anyone was able to do that?

---

### Post by BorisBas on 2009-04-16
> **limanoit said:**
> hi guyts i am using intel 2.6 on ubuntu 9.04 and can not get audio out over hdmi .. anyone was able to do that?

That thing has been kind of haywire for quite some time, and has been looking up a bit only recently. Are you running the latest 2.6.29? That is the first kernel that is supposed to properly support sound of hdmi on G35.. I will try this myself in a couple of weeks, so I am interested in your findings.

---

### Post by franzb on 2010-11-08
Having had to search a while for a solution and having seen some questions about this issue in this thread, here is how I got HDMI audio output working on my Asus P5E-V HDMI (the problem is, that the IEC958 device is not showing in the standard audio mixer, so it has to be set on the command line):

(1)amixer --card 0 |grep 958


Then unmute the devices (in my case "'IEC958',1" was sufficient:
(2)amixer --card 0 sset 'IEC958',0 unmute
(3)amixer --card 0 sset 'IEC958',1 unmute
(4)amixer --card 0 sset 'IEC958 Default PCM',0 unmute

---

