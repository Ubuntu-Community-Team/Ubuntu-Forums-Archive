---
title: "My Specs for myth tv. Should I wait to install mythbuntu or change some hardware?"
date: 2009-02-05
forum: Mythbuntu
---

### Post by Hackit on 2009-02-05
First let me say Hi everyone.

He are my specs.

Thermaltake TMG SL1 80mm Dual Slot Fan Case Cooler.

Corsair XMS2 TWIN2X2048-6400C4DHX Matched Pairs 2GB Kit. 
	
Thermaltake CL-P0369 Max Orb CPU Cooler.
	
Antec LifeStyle Fusion Desktop mATX Case 430W ATX12V Black VFD Volume Control.
	
Seagate Barracuda (ST3500320NS) ES.2 SATA 3.0Gb/s 500GB Hard Drive
	
Asus P5E-VM HDMI Socket 775 Intel G35 + ICH9R Chipset Dual-Channel DDR2 /800/667/533Mhz Intergrated Intel GMA X3500 with HDMI Support 8-Channel High Definition Audio Gigabit Lan Firewire 6x SATA 3.0Gb/s PCI-Express x16 Support Micro ATX.

Intel Core 2 Duo Socket LGA775, 2.2 GHz.
	
ASUS DRW-2014L1T SATA LightScribe Black 20X DVD-Writer 20xDVD+R/-R.	

I'm not using the built in video and have upgraded the video to ATI sapphire 4650 - 512 mb.

Tuner is a WinTV-HVR-1800.

Ok I bought all of this a year ago and was not succsefull at installing mythbuntu, so I decided to play with some other windows options. They are ok but I really want to run mythbuntu as this is why I built this system.

When I install I have a hard time getting my WinTV-HVR-1800 card working, does anyone know if it has support yet, I have spent countless hours searching and looks like some people might have it working.

Also the ati card can support audio through the video card and it was hard to get this working in windows.

Has anyone used this card? did it work with sound?

I know this is alot to ask and I'm sure i have forgot some info.

I'm just in need of a good HTPC.

Thanks

Kev

---

### Post by klc5555 on 2009-02-06
> **Hackit said:**
> First let me say Hi everyone.

He are my specs.

Thermaltake TMG SL1 80mm Dual Slot Fan Case Cooler.

Corsair XMS2 TWIN2X2048-6400C4DHX Matched Pairs 2GB Kit. 
	
Thermaltake CL-P0369 Max Orb CPU Cooler.
	
Antec LifeStyle Fusion Desktop mATX Case 430W ATX12V Black VFD Volume Control.
	
Seagate Barracuda (ST3500320NS) ES.2 SATA 3.0Gb/s 500GB Hard Drive
	
Asus P5E-VM HDMI Socket 775 Intel G35 + ICH9R Chipset Dual-Channel DDR2 /800/667/533Mhz Intergrated Intel GMA X3500 with HDMI Support 8-Channel High Definition Audio Gigabit Lan Firewire 6x SATA 3.0Gb/s PCI-Express x16 Support Micro ATX.

Intel Core 2 Duo Socket LGA775, 2.2 GHz.
	
ASUS DRW-2014L1T SATA LightScribe Black 20X DVD-Writer 20xDVD+R/-R.	

I'm not using the built in video and have upgraded the video to ATI sapphire 4650 - 512 mb.

Tuner is a WinTV-HVR-1800.

Ok I bought all of this a year ago and was not succsefull at installing mythbuntu, so I decided to play with some other windows options. They are ok but I really want to run mythbuntu as this is why I built this system.

When I install I have a hard time getting my WinTV-HVR-1800 card working, does anyone know if it has support yet, I have spent countless hours searching and looks like some people might have it working.

Also the ati card can support audio through the video card and it was hard to get this working in windows.

Has anyone used this card? did it work with sound?

I know this is alot to ask and I'm sure i have forgot some info.

I'm just in need of a good HTPC.

Thanks

Kev

A couple of thoughts:

The Mythtv wiki says the HVR-1800 currently works only on digital/QAM, not analog, if that's an issue.

ATI cards tend in general to be less well driver-supported than NVidia in Linux; your mileage may vary.

The remainder of the hardware seems OK --HDTV is CPU intensive, so this might become an issue for a 2.2 Gig processor, especially since XvMC support for assisting the CPU in video rendering is listed as not yet supported in any ATI drivers. So the CPU will be on its own in grinding out the HD video. If CPU speed becomes an issue, Socket 775 processors at 3.0-3.2 Gigs are pretty cheap and one can be dropped in as necessary.

In the long run, I predict you'll be happier if you keep the OS, swap, and all related files on one hard-disk, say 120-320 Gigs, and keep all recordings on other, big, SATA drives (along with frequent database backups). Additional SATA storage can be added as necessary. This division will allow you to blow away and reinstall the OS when necessary at a moment's notice with no inconvenience and no loss of data. Multiple partitions in the same hard disk can have the same net effect, of course, but you'll be amazed at how quickly HD recording (at a minimum of 6 Gigs an hour) can fill up the <400 Gigs of space you'll have for recordings after an OS install/configuration.

Just my $.02

But go ahead and install. Like they say in the lottery, if you don't play you can't win.

Cheers! :)

---

### Post by newlinux on 2009-02-06
The core 2 duo will be plenty for mpeg-2 HD (which is what your HD recordings will be) without XvMC, but might struggle with 1080i/p h.264. But rather than upgrade your proc, I'd recommend getting a nvidia VDPAU supported video card if you have problems with h.264 playback. Heck, I recommend a nvidia anyway as opposed to dealing with an ATI card. Hit or miss, as the previous poster said.

VDPAU It will be supported internally by myth in .22, but there are already ubuntu .21-fixes packages available that support VDPAU and mplayer can easily already be patched to support VDPAU as well. VDPAU will offload a ton of CPU processing to the GPU.

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by Hackit on 2009-02-08
> **klc5555 said:**
> A couple of thoughts:

The Mythtv wiki says the HVR-1800 currently works only on digital/QAM, not analog, if that's an issue.

ATI cards tend in general to be less well driver-supported than NVidia in Linux; your mileage may vary.

The remainder of the hardware seems OK --HDTV is CPU intensive, so this might become an issue for a 2.2 Gig processor, especially since XvMC support for assisting the CPU in video rendering is listed as not yet supported in any ATI drivers. So the CPU will be on its own in grinding out the HD video. If CPU speed becomes an issue, Socket 775 processors at 3.0-3.2 Gigs are pretty cheap and one can be dropped in as necessary.

In the long run, I predict you'll be happier if you keep the OS, swap, and all related files on one hard-disk, say 120-320 Gigs, and keep all recordings on other, big, SATA drives (along with frequent database backups). Additional SATA storage can be added as necessary. This division will allow you to blow away and reinstall the OS when necessary at a moment's notice with no inconvenience and no loss of data. Multiple partitions in the same hard disk can have the same net effect, of course, but you'll be amazed at how quickly HD recording (at a minimum of 6 Gigs an hour) can fill up the <400 Gigs of space you'll have for recordings after an OS install/configuration.

Just my $.02

But go ahead and install. Like they say in the lottery, if you don't play you can't win.

Cheers! :)

Ok as far a drive space i have 3 seagate Drives for a total 1.5 terabytes, ok for now.

As far as my ati card, I went with ati as my board has ati built in and just thought it would be more stable to use an ati pci card.

Was I wrong in thinking that since the board is setup for ati that it's better to stick woth ati, or would an nvidia card be ok?


Thanks for your input, Looks like I'll be installing mythbuntu this week, i was thinking of going to the Mythbuntu 9.04 Alpha 3 Release ?

Would you try this?

or install intrepid?

Thanks Again.

---

### Post by newlinux on 2009-02-09
a nvidia card still would have been fine, and preferred. Get a one with VDPAU support if you can return the ATI card - Oh I guess you said you bought this stuff a year ago. The onboard GPU doesn't have to match add on GPUs.

I like my myth systems to be fairly stable, so I would recommend Intrepid or Hardy, but the Jaunty alpha me be okay. It all depends on what you want to deal with.

---

### Post by klc5555 on 2009-02-09
> **newlinux said:**
> a nvidia card still would have been fine, and preferred. Get a one with VDPAU support if you can return the ATI card - Oh I guess you said you bought this stuff a year ago. The onboard GPU doesn't have to match add on GPUs.

I like my myth systems to be fairly stable, so I would recommend Intrepid or Hardy, but the Jaunty alpha me be okay. It all depends on what you want to deal with.

I also normally prefer stable, but here I'd say to go with 8.10 or 9.0x rather than 8.04. Been lots of changes in dvb driver support since the 2.6.25 and earlier kernels, and I think support for the 1800 is in enough of a state of flux that the more up-to-the-second the kernel & modules are, the less the chance will be of finding the configuration of the 1800 to be ... unpleasant.

Also if you get an NVidia card, I'd also say be sure to get one with an onboard cooling fan rather than the varieties with large onboard heat sinks. My experience with the heat-sink varieties has tended to be one long series of thermal-related lockups, even in reasonably well-ventilated cases.

Cheers! :)

---

### Post by newlinux on 2009-02-09
> **klc5555 said:**
> I also normally prefer stable, but here I'd say to go with 8.10 or 9.0x rather than 8.04. Been lots of changes in dvb driver support since the 2.6.25 and earlier kernels, and I think support for the 1800 is in enough of a state of flux that the more up-to-the-second the kernel & modules are, the less the chance will be of finding the configuration of the 1800 to be ... unpleasant.

Also if you get an NVidia card, I'd also say be sure to get one with an onboard cooling fan rather than the varieties with large onboard heat sinks. My experience with the heat-sink varieties has tended to be one long series of thermal-related lockups, even in reasonably well-ventilated cases.

Cheers! :)

Very good points. I'm so used to using older hardware I forget about the usefulness of updated kernels for tuners. So yes make sure to go no older than the kernel that best supports your hardware!

On the flipside, I use only fanless GPUs and have never had a problem, but I rarely use GPU hardware acceleration. IF/When I get a card that supports VDPAU I'll have to rethink this.

---

### Post by Hackit on 2009-02-09
Thanks again guys.

One more question I have 2 of the drives filled with movies, music and pictures.

Like i said before I just wanted to use my hardware and was running vista MCE : -(, and some other programs (sage tv, GBVR ECT............)

So all my drives are ntfs, i'm not worried about the first drive i can erase and format windows ok, but as far as the other drives I'm sure they should not be in ntfs.

If I need to change the format of the 2 other drives thats going to take some juggling data on my part and i'm not looking forward to that :-(.

So I guess i will need to format the drives if i'm going back to linux?

---

### Post by newlinux on 2009-02-09
If you've already backed up your data you can format your drive(s) as part of the install process. 

Also Linux can handle NTFS, so I guess technically you'd only need to put the root partition on ext3 (or other Linux system)but really you should use a better filesystem. What I do is for the root partition I use ext3, and for recordings I use XFS, which seems faster and handles larg files better, especially deleting them.

---

### Post by Hackit on 2009-02-19
> **newlinux said:**
> a nvidia card still would have been fine, and preferred. 

Ok, I forgot My desktop had a Nvidia 8600gts 512 card.

So I swapped both cards and now my desktop has ATI and the Myth box is equipped with the Nvidia card, Yeahhhhhhhhhhhh....

Just writing down a note for me, and if anyone knows of some tricks feel free to reply.

1. Setup my antec fusion lcd.
2. setup Lirc with my logitech 720 remote.
3. setup Hauppaige hvr-1800, :-(.
4. see if I can get sound from the Nvidia hdmi cable (might have to use optical out).
5. setup? I'm sure i forget something, I hope the rest is detected while installing.

---

### Post by newlinux on 2009-02-19
I think there are threads here that will help you with most of these. I actually have a few harmony remotes (including the 720) that I use with LIRC. I usually set them up as MCE remote and then configure myth and LIRC as if I was using a an MCE remote...

---

### Post by Hackit on 2009-02-19
> **newlinux said:**
> I think there are threads here that will help you with most of these. I actually have a few harmony remotes (including the 720) that I use with LIRC. I usually set them up as MCE remote and then configure myth and LIRC as if I was using a an MCE remote...

Hi newlinux, I have a question?

I have always used the default partion linux says to use, well this time I used manual config,

I have changed the main drive to ext3 journaled and xfs on the 2 other drives.

What do i set for map points?

I know I need a root ( / ), should i put the home and var on the same drive? what kind of map points do i use for the 2 drives for my media?

Thanks

---

### Post by newlinux on 2009-02-19
It's really up to how you want to do things, but the choices you do will affect what locations you put in myth for storage. In that configuration, I'd just do / on the ext3 and possibly create a separate partition on that same drive to put /home on. Then map the other two drives to something else like /storage or /videos or /recordings. If you do it this way, you will want to change the default mythvideo, mythmusic, mythgallery locations... as they will be looking under /var.... by default. Alternatively you could make /var one of the other drives.

---

### Post by Hackit on 2009-02-20
I now remember why i stopped messing with mythbuntu.

I setup the partitioning fine, I did not install ubuntu desktop (probably should have).

I spent 5 hours last night trying to get the lcd and lirc to work with no luck, I followed this guide;
[http://codeka.com/forums/viewtopic.php?f=3&t=23&start=50#p452](http://codeka.com/forums/viewtopic.php?f=3&t=23&start=50#p452)

and this guide;

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=907256](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=907256) (looks like this is for hardy).

My problem now is I don't remember what the errors we're, that's the problem when you are tired and it's 4 in the morning.

I did find a post that was for Intrepid but can't seem to find it now.

I'm doing another fresh install and will try again tonight. I have the same imon as the guides are for and I know it should work.

I almost forgot to ask, when i first run myth it ask's if I have a remote and I choose the sound mon option. Is that the right choice? Should I maybe leave this blank and set it up later?

Thanks for all the help.

---

