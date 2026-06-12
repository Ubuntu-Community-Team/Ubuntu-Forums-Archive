---
title: "Feedback on a complete HTPC system"
date: 2007-11-13
forum: Mythbuntu
---

### Post by Scrier on 2007-11-13
Hi, 

I'm currently intresting in setting up a HTPC system in a networked area. I have little to none knowledge from Linux before, some access through work and 2-3 installs of gentoo but thats about it. I also wan't to build these system to some of the family members if it works out well later so instead of going by a sepearate core / mythTV install, I guess a complete package would be better and easier to maintain.

First of all I wan't to start with one dedicated "storage" server that I put away in some closet somewhere where I have the majority of recorded dvd:s etc. This I should install a regular Ubuntu on I guess? or is it support already for use of another comps files in this Mythbuntu release? It's a P4 2.8 Ghz comp with 2 GB of ram, 2x120 GB disks 2x250 GB disks and what I really want in, a FireWire 800 card for external disks (I have [PCI-IOFW82AA2]("http://www.sunsway.com.hk/products/pci1394b.html") now but i'm not sure it has linux drivers). I'm guessing the specs is ok for that part. Is there drivers available for this card or do you have any other card that you recommend?

As for the HTPC requirements I wan't to playback 1080p, MKV files etc but I guess this is as in windows just different codecs. Anyway here is the specs of the HTPC and you can give feedback where I need to boost hardware a bit.

[LIST]
[*][Antec Fusion]("http://www.antec.com/ec/productDetails.php?ProdID=08738") chassi.
[*][ASRock 4Core1333-fullHD]("http://www.asrock.com/mb/overview.asp?Model=4CORE1333-FULLHD")
[*]Intel Core 2 Duo E6750 2,67GHz
[*]Kingston HyperX DDR2 PC6400/800MHz CL5 2x1GB
[*]2 x WESTERN DIGITAL CAVIAR SE16 500GB (Raid 1)
[*]PLEXTOR DVD±R/RW DL 18X PX-800A
[*]2 x [HAUPPAUGE WINTV NOVA-T 500]("http://www.hauppauge.co.uk/pages/products/data_novat500.html")
[/LIST]

Does Linux make good use of the dual core in videoplayback? I know windows has some issues on this on some mediaplayers. And I can probably find a cheaper processor if it won't make use of both cores.

Is there support for the LCD-Display on the Antec chassi or is this a goner? Do I need a special connector on the motherboard or is it standard USB it uses?

I want to have an internal soundcard to this but I'm not sure I need it / can find any that takes one of the PCI-x slots. I have a surround system and I'm not gonna buy a soundcard if the output from the motherboard is enough input to the reciever.

Will the internal Graphic card be enough to playback 1080p? 

The recommended processor for 1080p playback is 3 Ghz but what is the recommended processor if you have dual core?

I will probable have some followup questions later on but this is what I can think of now.

// Andreas

---

### Post by theacoustician on 2007-11-13
Ok, I'm actually working on figuring out the same myself, but the documentation is spotty at best it seems right now.  Here's what I've been able to piece together.

- The graphics card doesn't matter too much in this application since all decoding in Linux currently is software only.  As long as the chip can output 1920x1080@60Hz, you should be fine.  You *might* want to look at getting a lower end nVidia 8xxx series simply because they're supposed to support hardware decoding in Linux sometime in the future.  Theoretically, ATI has pledged the same, but I haven't had a whole lot of luck with their stuff in Linux, so I'm of a wait and see attitude on them.

- It would seem the rule of thumb is 2.4 GHz on a C2D for H.264 @ 1080p.  Don't take that as gospel, but from what I can piece together of people currently watching such videos, this is roughly where the min. spec. of their systems lie.  I can tell you both VLC and Mplayer make use of both cores for decoding.  Going to a 64bit OS over a 32bit one seems to reduce the processor requirement by about 20%.

-As for your server/frontend scenario for playback, look into MythTV a bit further.  Part of the standard installation package allows you to build a backend storage server for Myth, just as you described. 

That's about all I can help you with for now.  If you can figure out if its possible to stream a 1080p clip from the backend server to the frontend player over 802.11g and if so, how much space is needed for a buffer cache, I'd be mighty appriciative.

---

### Post by pasta514 on 2007-11-13
> **theacoustician said:**
> - The graphics card doesn't matter too much in this application since all decoding in Linux currently is software only.  As long as the chip can output 1920x1080@60Hz, you should be fine.  You *might* want to look at getting a lower end nVidia 8xxx series simply because they're supposed to support hardware decoding in Linux sometime in the future.  Theoretically, ATI has pledged the same, but I haven't had a whole lot of luck with their stuff in Linux, so I'm of a wait and see attitude on them.

- It would seem the rule of thumb is 2.4 GHz on a C2D for H.264 @ 1080p.  Don't take that as gospel, but from what I can piece together of people currently watching such videos, this is roughly where the min. spec. of their systems lie.  I can tell you both VLC and Mplayer make use of both cores for decoding.  Going to a 64bit OS over a 32bit one seems to reduce the processor requirement by about 20%.

I'm interested in a 720p htpc.  are there 'rules of thumb' for that, or can you give a pointer to where to find this information?

> 
-As for your server/frontend scenario for playback, look into MythTV a bit further.  Part of the standard installation package allows you to build a backend storage server for Myth, just as you described. 

mythbuntu is great. I've been working on trying to figure out the software installation before finalizing the hardware.

---

### Post by newlinux on 2007-11-13
> **pasta514 said:**
> I'm interested in a 720p htpc.  are there 'rules of thumb' for that, or can you give a pointer to where to find this information?


mythbuntu is great. I've been working on trying to figure out the software installation before finalizing the hardware.

If you are not doing h.264, the requirements are pretty low. Pretty much any dual proc will do all the way up to 1080p. I do 720p with my pentium 2.6Ghz and a geforce 440mx without using XvMC.

Stick with nvidia lower end card, for now. I nice passively cooled 6 series do nicely (I have a 6200 LE PCIe that does great in one of my frontends).

I have had spotty luck with HD over wireless g. It works sometimes, sometimes not - too many environment issues that can interfere - so not used for HD for me.

---

### Post by theacoustician on 2007-11-13
> **pasta514 said:**
> I'm interested in a 720p htpc.  are there 'rules of thumb' for that, or can you give a pointer to where to find this information?
Its an average "safe number" I arrived at by looking at Apple's and Nero's specs for 264 playback, software specs from companies like CyberDVD for HD-DVD/BluRay playback, and just googling HTPC H.264 playback and 1080p.  Mostly I was looking at forum posts from places like Doom9, Videolan.org, etc. to see what system specs people were using and getting sucessful playback.  There seems to be some wide variance on what actually works for who.  Some people can get great decodes on a single core.  Some can't seem to manage to make it work on quad cores without frame drop.  I can confirm that 64bit seems to make a difference in encode and decode requirements, particularly on encode side.

Point blank: there's no good documentation out there right now and you're just going to have to do some research.

---

### Post by theacoustician on 2007-11-13
> **newlinux said:**
> I have had spotty luck with HD over wireless g. It works sometimes, sometimes not - too many environment issues that can interfere - so not used for HD for me.

Tried wireless N?  Did it work any better?

I ask because my house isn't wired and really can't be because of how its constructed.  I'm stuck with wireless for data transfer and I'd really prefer a back end server/NAS - front end player configuration rather than having a couple of stand alone Myth boxes scattered about.

---

### Post by newlinux on 2007-11-13
Nope, didn't want to shell out the dollars for wireless N. I ended up running wire to as many places as I could. No wire to the garage, so that is still wireless, but maybe I'll try wire there or powerline. I tried some powerline adapters and they did work, but are overpriced, so maybe if I see the right deal on ebay...

---

### Post by brundles on 2007-11-13
TBH I'd never use wireless for streaming if you're looking at HD. If you don't want to use traditional wires, what about the Homeplug option? You get a decent speed without the hassle of wires.

If you want to cut down on the spec of PC you have then something that may be worth considering for x264 (not H264) is a rebuild of MPlayer on the system instead of the generic Ubuntu install. From the 2 systems I've played around with on this simply doing a rebuild on the platform itself will give a 10 to15% improvement on the decode rates with a similar level being achievable if you then include the CoreAVC codec patch. (I very nearly managed to get a 2.6 Celeron playing x264s back this way but not quite!)

I'm currently setting up an HTPC system for a friend on a more traditional Ubuntu install (Gutsy) and going through a few bits of agro.

In terms of graphics cards he's using the ATI Radeon HD2600 XT - the current drivers for it give reasonable 3D performance but not 2D so video playback is pretty choppy at the moment despite the dual core CPU :(.

---

### Post by theacoustician on 2007-11-13
> **brundles said:**
> TBH I'd never use wireless for streaming if you're looking at HD. If you don't want to use traditional wires, what about the Homeplug option? You get a decent speed without the hassle of wires.Hadn't tried it yet because I wasn't real keen on spending $ on something that may or may not work for me.  The electrical in this house is a bit squirrelly, but I may just bite the bullet and give that a go.

> **brundles said:**
> 
If you want to cut down on the spec of PC you have then something that may be worth considering for x264 (not H264) is a rebuild of MPlayer on the system instead of the generic Ubuntu install. From the 2 systems I've played around with on this simply doing a rebuild on the platform itself will give a 10 to15% improvement on the decode rates with a similar level being achievable if you then include the CoreAVC codec patch. (I very nearly managed to get a 2.6 Celeron playing x264s back this way but not quite!)
What exactly is that supposed to mean, x264 not H264?  x264 is a GNU H.264 encoder.  H.264 is the standard to which x264 encodes.  Furthermore, x264 isn't a decoder, so recompiling MPlayer for that doesn't really make sense (unless you're talking about encoding).  

Now, I can definately see how compiling MPlayer from scratch could definately win you some improvements on playback, since you can set all the relevant advantageous settings for your system.  Great idea, hadn't thought of that one yet.  Full disclosure on CoreAVC : that's not free software.  If you're going to "apply the patch", you need to purchase the codec from CoreCodec first.  It is however, the best decoding codec I've come across, so this is again another good suggestion.

---

### Post by pasta514 on 2007-11-13
> **newlinux said:**
> 

Stick with nvidia lower end card, for now. I nice passively cooled 6 series do nicely (I have a 6200 LE PCIe that does great in one of my frontends).


how about a motherboard with onboard graphics?  GeForce 7100/7150?  or AMD 690?  but sounds like ATI support for linux is poor, so I'll assume avoid the ATI/AMD options, right?

---

### Post by brundles on 2007-11-13
> **theacoustician said:**
> What exactly is that supposed to mean, x264 not H264?  x264 is a GNU H.264 encoder.  H.264 is the standard to which x264 encodes.  Furthermore, x264 isn't a decoder, so recompiling MPlayer for that doesn't really make sense (unless you're talking about encoding). 

Now, I can definately see how compiling MPlayer from scratch could definately win you some improvements on playback, since you can set all the relevant advantageous settings for your system.  Great idea, hadn't thought of that one yet.  Full disclosure on CoreAVC : that's not free software.  If you're going to "apply the patch", you need to purchase the codec from CoreCodec first.  It is however, the best decoding codec I've come across, so this is again another good suggestion.

I thought that x264 encoding actually resulted in a slightly non standard file because of some of the optimisations it made? I could be wrong though - my understanding of the two is limited. Are you saying that if you have a graphics card with onboard H264 decoding support it can handle something encoded with x264 as well?

Sorry about the slip with Core AVC - you're right, it does mean buying the Windows codec pack first (and having a Windows machine to install it on at this stage) but I'd recommend it as a way forward for more efficient playback if you can.

---

### Post by newlinux on 2007-11-13
> **pasta514 said:**
> how about a motherboard with onboard graphics?  GeForce 7100/7150?  or AMD 690?  but sounds like ATI support for linux is poor, so I'll assume avoid the ATI/AMD options, right?

Nvidia 7000/7150 should be good. I have an onboard 6150 driving  a 720p set just fine (although it did take some xorg/nvidia setting tweaks).

---

### Post by JustInterested on 2007-11-13
Newlinux - what tweaks did you need to make to xorg/nvidia settings for the onboard 6150? What were the issues you had?

I've got onboard 6150 as well (using the ASUS m2nPV-VM mobo) so I'm curious as what you needed to change.

---

### Post by theacoustician on 2007-11-13
> **brundles said:**
> I thought that x264 encoding actually resulted in a slightly non standard file because of some of the optimisations it made? I could be wrong though - my understanding of the two is limited. Are you saying that if you have a graphics card with onboard H264 decoding support it can handle something encoded with x264 as well? There was an issue with x264 making non-compliant files because it could make motion vectors with an absolute value larger than 512.  The resultant files still played in most software decoders and almost all hardware decoders, but there were a few that got tripped up by this.  It was corrected a few months back, so anyone using x264 since rev. 663 is making spec compliant files.  Make no mistake though, x264=H.264 or at least that's the goal ([http://en.wikipedia.org/wiki/X264](http://en.wikipedia.org/wiki/X264)).  I can understand where you might have gotten your notion though, since it was first uncovered by CoreAVC users trying to play back files made with x264.  CoreAVC makes most of its performance gains off being very strictly complaint with the H.264 standard and building off that.

As for what I meant about the display is this : all decoding for H.264, regardless of the encoder used to make that file, is strictly done in software under Linux.  It is purely a CPU task as there is no GPU involvement or hardware decoders to be had.  So, as long as your graphics card or onboard graphics chip can display a resolution of 1920x1080@60Hz and you have a processor fast enough to decode the file, you should be able to view the video.  Obviously, that's a bit of a simplification, but a good general rule.  An example?  The newish Mac Minis. They've got a C2D and a vanilla Intel onboard graphics chip.  There are several reports that it plays 1080p 264 content perfectly.  If there's an issue with decoding files made with x264, either re-encode the file with an updated version of x264 or find a software decoder that's a bit more lenient than CoreAVC.

---

### Post by newlinux on 2007-11-13
> **JustInterested said:**
> Newlinux - what tweaks did you need to make to xorg/nvidia settings for the onboard 6150? What were the issues you had?

I've got onboard 6150 as well (using the ASUS m2nPV-VM mobo) so I'm curious as what you needed to change.

I think my issues were specific to my set. The biggest hurdle I had was tearing, which nothing seemed to fix at the time, until I switched to using RTC timing and bumping up the frequency mythfrontend could access.

[http://www.mythtv.org/wiki/index.php/Frame_display_timing](http://www.mythtv.org/wiki/index.php/Frame_display_timing)

 Just seemed to take a while to get the picture right (get the right settings), whereas my tv connected to my 6200 pretty much worked fine out of the box. It's possible thatt if I had connected the systems up to the opposite TVs I would have had the problems with the 6200. When I had the 6150 connected to a computer monitor it pretty much just worked.

---

### Post by JustInterested on 2007-11-14
newlinux - ahh ok. Thanks for the link!:)

---

### Post by Scrier on 2007-11-14
Thanks for the feedback and the extra info about hardware suggestions. If I set up a regular comp as a "Backend & Regular Desktop" and have this as the primary backend as well. (Will only surf, torrent leech etc on this one and have some FireWire 800 disks connected to it). 
Then I set up the specified comp as a "Combined Backend Frontend" with backend slave. Will it record locally or to the backend comp? 
Can I move recorded files to the primary backend after copying a dvd for example?.

Oh and currently I have 2 External 1 TB Western Digital MyBooks running on windows with ntfs. Can I just plug these in and they work or do they need to be completely reformatted into something linux likes and then copy over the files or can I do something in between?.

edit: typos

---

### Post by newlinux on 2007-11-14
I wouldn't use NTFS, especially if you are using this drive for recordings are large video files. You can use it for read and write with a driver in Linux (by default  you can only read from NTFS filesystems in most Linux distros), but XFS is a much better filesystem for larger files and for Linux (better stability, no need to defrag). Or even ext3. You can still share these with windows just fine via SAMBA/CIFS if you connect them up to a linux box.

---

### Post by brundles on 2007-11-14
> **newlinux said:**
> I wouldn't use NTFS, especially if you are using this drive for recordings are large video files. You can use it for read and write with a driver in Linux (by default  you can only read from NTFS filesystems in most Linux distros), but XFS is a much better filesystem for larger files and for Linux (better stability, no need to defrag). Or even ext3. You can still share these with windows just fine via SAMBA/CIFS if you connect them up to a linux box.

EXT3 drives can also be read and written to directly from Windows if you use [the EXT2IFS driver](http://fs-driver.org/index.html). I tend to use EXT3 in preference to FAT32 for shared drives because of the availability of large file sizes.

---

### Post by newlinux on 2007-11-14
> **brundles said:**
> EXT3 drives can also be read and written to directly from Windows if you use [the EXT2IFS driver](http://fs-driver.org/index.html). I tend to use EXT3 in preference to FAT32 for shared drives because of the availability of large file sizes.

That's really only necessary if the drives are connected to the windows machine (most likely in a dual boot scenario). I was talking about if the drives are connected to a Linux machine. Then it is the network protocol of how the drive is shared that allows windows to access it (SAMBA/CIFS) and drivers aren't needed. When he said plug these in I assumed he was pluggin them into a Linux box, but I could be wrong. 

I would never use FAT32 - too many failings and limitations (particularly the 4GB filesize limit when it comes to HTPCs). In dual boot situation use FS-driver with ext3 or use NTFS-3G in linux for NTFS.

---

### Post by Scrier on 2007-11-15
I will use linux only so no dual boot but the disks is atm ntfs formatted. I guess I need to format one to the required xfs filesystem then copy over the content to this disk through ftp or something from the windows pc to the linux backend.

When using a backend with no tv-cards as primary backend will the frontends store recorded items locally or on the backen or is this free to configure?

---

### Post by newlinux on 2007-11-15
> **Scrier said:**
> 
When using a backend with no tv-cards as primary backend will the frontends store recorded items locally or on the backen or is this free to configure?

I'm not sure I understand your question. But if you are asking what I think, all recorded programs will be stored in whatever directory you specify in the backend setup associated with the machine that contains the tuner doing the recording. So you can have each backend store its recordings wherever you specify, which can be local to that backend machine or to a network share.

---

### Post by Heinz on 2007-11-19
Since I built my HTPC a couple of months ago I can give you some advice .

**CPU + Mainboard**

E6420 (overclocked @ 3 GHz, absolutely stable)
Gigabyte 965P-DS3

This CPU is a top overclocker and much cheaper as your suggested E6750 which might also not be sufficient for 1080p in H264. If not overclocked even some 720p scenes show dropped frames in mplayer output with my E6420.

**Graphics**

Nvidia 8500 GT (silent passive cooling)

No problems here since the CPU is mostly important. The card delivers native 1920 x 1080 to my LCD.

**Sound**

Realtek ALC883

Connected to Yamaha DD/DTS receiver via optical out. Works great and sound is fantastic. Merely some DTS tracks don't work at full bitrate (1536 kbit/s) in mplayer and result in stuttering. Xine however plays them smoothly.

**WLAN**

802.11b/g

Is ok for normal use but NOT sufficient for HD streaming due to much too low speed. I can stream TV (cable and DVB-T) without problems.

---

### Post by Scrier on 2007-11-20
Thanks alot for all information. As for the Firewire card is there anyone having experience with that brand or can recommend some similar firewire card that can manage Fire wire 800. Also how does the playback work in 1080 p when using external disks. If i'm good with USB ill use that but I think it's a little low bandwith for it.

---

### Post by Cuppa-Chino on 2007-11-21
> **Heinz said:**
> Since I built my HTPC a couple of months ago I can give you some advice .

**CPU + Mainboard**

E6420 (overclocked @ 3 GHz, absolutely stable)
Gigabyte 965P-DS3

This CPU is a top overclocker and much cheaper as your suggested E6750 which might also not be sufficient for 1080p in H264. If not overclocked even some 720p scenes show dropped frames in mplayer output with my E6420.

**Graphics**

Nvidia 8500 GT (silent passive cooling)

No problems here since the CPU is mostly important. The card delivers native 1920 x 1080 to my LCD.

**Sound**

Realtek ALC883

Connected to Yamaha DD/DTS receiver via optical out. Works great and sound is fantastic. Merely some DTS tracks don't work at full bitrate (1536 kbit/s) in mplayer and result in stuttering. Xine however plays them smoothly.

**WLAN**

802.11b/g

Is ok for normal use but NOT sufficient for HD streaming due to much too low speed. I can stream TV (cable and DVB-T) without problems.

Interesting build. 
I am also considering putting together a nice little HTPC for our living room.

now I see that your pc has an overclocked cpu so I would guess it requires some pretty decent cooling, what are you using? how loud is it?
what kind of case are you using?

also which graphics card will be able to help the cpu the most? in windows the drivers of course unload the cpu so much that any half decent last generation card (as an exmample only Radeon HD2600 which is a poor overall performer but is absolutely spot on good enough for high quality video :[review on hd and blue ray]("http://www.guru3d.com/article/Videocards/440/7/")) 

FYI I am looking at really chomping down on power consumption as to get my box as quiet as possible (heck it needs to work in a living room)

thanks for your ideas

---

### Post by Scrier on 2007-11-22
Hmm, just a quick question here. If I put the tv-cards in the backend and use PS3 frontend (feel free to link me to some site if this has been done) Won't that save me alot of work? The PS3 has the playback of HDMI possible but installing MythTV over it might cause problems. I ask because it halves the frontend I'm currently looking at in price.

---

### Post by newlinux on 2007-11-22
Yellow dog linux is what's typically put on the psIIIs, but I don't think it uses the hardware video acceleration yet, so it won't be able to playback HD with MythTV on it until that is fixed. You might want to consider appleTV I think some have gotten hd playback on that with linux, or a roku 1000 and mythroku if you can find them cheap enough...

---

### Post by dubstar on 2007-11-26
> **theacoustician said:**
> Tried wireless N?  Did it work any better?

I ask because my house isn't wired and really can't be because of how its constructed.  I'm stuck with wireless for data transfer and I'd really prefer a back end server/NAS - front end player configuration rather than having a couple of stand alone Myth boxes scattered about.



wireless G doesnt have the bandwidth for full HD streaming. draft N does however. but i havent any experience of draft N yet. either way that'll be replaced by Wi-MAX in couple of years depending on uptake. Now that would be useful! Draft N is, well, was meant to be, an intermediatery between G and Wi-MAX, but the they can't currently decide on inter-operability issues. If you're going draft N stay all with one manufacturer to be safe.

Other than that, does Gutsy support the high end Creavtive X-Fi and the likes cards, wondering about digital output to my A/V receiver ya see....?!?

---

### Post by Cuppa-Chino on 2007-11-30
> **dubstar said:**
> Other than that, does Gutsy support the high end Creavtive X-Fi and the likes cards, wondering about digital output to my A/V receiver ya see....?!?

maybe this is my lack of understanding, but why do you need an creative high powered card with a digital output?

if you are using the digital stream from the source (ie say DTS or Dolby Digital THX from the DVD) I always thought you did NOT want to process this in your dvd player / htpc but just pass it through to your a/v receiver and if all you are doing is pass through why bother going with an expensive card that does nothing (and could cause issues with lacking compatibility) 

please correct me if I misunderstood

---

### Post by Heinz on 2007-12-02
> **Cuppa-Chino said:**
> Interesting build. 
I am also considering putting together a nice little HTPC for our living room.

now I see that your pc has an overclocked cpu so I would guess it requires some pretty decent cooling, what are you using? how loud is it?
what kind of case are you using?


I'm using simple air cooling with an Arctic Freezer Pro. Temperature is never over 60 ° C under load. If you would play anything audible you cannot hear the system. Only with complete silence in the room one is capable of recognizing a very silent fan noise which however doesn't annoy me but well might others. Depends on personal taste.

---

