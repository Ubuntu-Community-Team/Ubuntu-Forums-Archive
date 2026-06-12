---
title: "Bless this build I pray"
date: 2008-01-29
forum: Mythbuntu
---

### Post by mythbuntuChris on 2008-01-29
Hello,

My good friend and I are taking the plunge and attempting to build our own HTPC.  His will be used for viewing/recording analog cable and OTA broadcasts and my build will be strictly for OTA (ASTC).  Overall, I think we're at the state of "paralysis through analysis" over all the options to go with.  Since we're both pretty cheap-minded fellas and we don't want to have to report to our wives that we wasted money on hardware that won't work, we'd like to run buy our builds and see if it'll do what we had in mind.

Tweedle Dee's Build:
Case: Antec NSK2480
CPU: AMD Athlon 64 X2 5000+ (Brisbane 2.6GHz)
RAM: DDR2 800 2 x 1GB
Mobo: MSI K9NGM3-FIH AM2 NVIDIA GeForce 7050 Micro ATX
Video Card: NVIDIA GeForce 7050 (onboard mobo)
Sound Card: Realtek ALC883 (onboard mobo)
HD: SAMSUNG SpinPoint T Series HD501LJ 500GB 7200 RPM SATA
Tuners: HDHomerun


Tweedle Dum's Build:
Case: Antec NSK2480
CPU: AMD Athlon 64 X2 5000+ (Brisbane 2.6GHz)
RAM: DDR2 800 2 x 1GB
Mobo: MSI K9NGM3-FIH AM2 NVIDIA GeForce 7050 Micro ATX
Video Card: NVIDIA GeForce 7050 (onboard mobo)
Sound Card: Realtek ALC883 (onboard mobo)
HD: SAMSUNG SpinPoint T Series HD501LJ 500GB 7200 RPM SATA
Tuners: Air2PC rev.02  
(want to have at least 3 but trying to figure out what to do b/c I only have 2 pci slots)
-will need to put in a wireless card as I don't plan to run ethernet cable to the box from my modem upstairs

Well as Prince Albert so stately stated, there you have it. Any suggestions/warnings would be greatly appreciated.

Have a great day!

chris

---

### Post by newlinux on 2008-01-29
which of you is tweedle dee and tweedle dum? :) Neither system seems to have a card for recording analog cable.

---

### Post by mythbuntuChris on 2008-01-29
In this instance I am Tweedle Dum and only plan to use my tv tuner card to capture OTA (esp. with Lost getting ready to get back into the swing of things).  Tweedle Dee is under the impression that the HDHomerun card will handle the recording of analog/unencrypted cable.

---

### Post by JPurdy on 2008-01-29
Dee here. :)

My entertainment sources vary from my compadre.  I have basic (analog) cable, which I get some digital (some in HD) channels, when I channel-scan w/ my HDTV [that has a ATSC/NTSC/QAM tuner].  I also have OTA, but the signal strength with an internal antennae is about 60-70.  Ideally, I'd like to have the flexibility of channeling into either source, but I believe at first, I'd like to tune into the analog cable (100% signal there) along w/ the HD content.  From my research, I believe my best option is the HDHomerun, which the MythTV(buntu) will pick up and be able to tune and record from.  The HDHomerun does OTA as well as unencrypted QAM ... *doesn't "unencrypted QAM" mean all the channels I currently receive over the analog cable (without the aid of a cable box)?*

So that said, with those video/cpu specs, can we:

[LIST=1]
[*] Tune/Record HD content
[*] Playback content in HD (720p)
[/LIST]

Thanks!

---

### Post by newlinux on 2008-01-29
the hdhomerun doesn't have an analog tuner. You'll only get unencrypted QAM or OTA ATSC, not NTSC (analog format).

---

### Post by newlinux on 2008-01-29
Oh and those specs are plenty strong enough for 720p HD content...

---

### Post by twkisner on 2008-01-29
> **mythbuntuChris said:**
> Hello,...

Tuners: Air2PC rev.02  
(want to have at least 3 but trying to figure out what to do b/c I only have 2 pci slots)
-will need to put in a wireless card as I don't plan to run ethernet cable to the box from my modem upstairs



I ever so occassionally see the external USB Air2PC up on e-bay, and it goes for fairly cheap as well, considering - not as cheap as the PCI cards mind you, (which the last PCI one I snagged for $20 including shipping).  But I think the last USB one I saw sold for around $50, which is reasonable and still cheaper than the HD Homerun per tuner.

I lived for several months with 2 Air2PC tuners for OTA HD - it was OK 90% of the time.  I finally gave in and added a 3rd one.  But you might start out with 2 and go from there looking for a cheap USB to crop up.

As far as wireless goes, I used a "game adaptor" because it was frustrating for me to find a 64 bit linux compatable wireless card.  That would also free up your PCI-E 1x slot for a 3rd  tuner if you eventually go that direction (I'm assuming this is the slot you were going to put the wireless in????).

---

### Post by mythbuntuChris on 2008-01-30
For the air2PC cards, I was thinking about either trying to find an enclosure that could house the pci card and connect via usb.  Another thought was employing a pci extension component but I don't know if linux would be happy with this setup.

For wireless, I was hoping I could just plug in a wireless card via usb (unless there's a way to get it on the mobo that I'm not thinking about).

Have a great day!

chris

---

### Post by JPurdy on 2008-01-30
So is there a PCI card out there that can tune into my analog cable and get the digital channels within and possibly do OTA stuff, too?  And is compatible w/ Mythbuntu?

Thanks!

**Update:** I keep finding [other]("http://forums.sage.tv/forums/showthread.php?t=23864") [posts]("http://www.highdefforum.com/showthread.php?t=8281&page=2") elsewhere that say I need unencrypted QAM.  Help me understand ATSC, NTSC and QAM.  According to [this thread]("http://www.avsforum.com/avs-vb/showthread.php?page=1&t=800534"), the way I understand it is:   **ATSC**: OTA Digital (HD & SD), **NTSC** - for analog cable (bonus: also OTA analog until it's shut off) and then **QAM** - for digital channels (both HD & SD).

So do I need something that does all 3?  Like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815100014")?  Anything cheaper out there?  Works w/ Mythbuntu?

**Update 2:** Found [this]("http://blogs.snapstream.com/2007/05/04/hdhomerun-and-snapstream-beyond-tv/") from SnapStream, which leads me to believe the HDHomerun will work for me ... am I wrong?

---

### Post by newlinux on 2008-01-30
The hd homerun is digital only. So unless all the channels you want to get are ATSC or unencrypted QAM, you won't be able to get them with the HDhomerun.  Generally speaking, all you can count on from unencrypted QAM are the locals. Anything else is usually a bonus. I get the HD locals, digital SD locals, a few public access channels and a few shopping networks via unencrypted QAM in my area. So if that is all you want from cable then that is all you need. In the original post it says you want analog cable, so I was just commenting that you won't get analog cable with the HDhomerun because it doesn't have an analog tuner.  So I don't know if you are wrong until you say what stations you want. If you want stations like SciFi, NAtional Geographic, CNN, you probably won't get them with a QAM tuner because they are probably encrypted over QAM (but available over analog).

Dvico Fusion 5
Kworld ATSC 110/115 [http://www.newegg.com/Product/Product.aspx?Item=N82E16815260005](http://www.newegg.com/Product/Product.aspx?Item=N82E16815260005)
pchdtv 5500

Are a few of the ones that do QAM/ATSC/NTSC. All 3 work in mythbuntu.

---

### Post by JPurdy on 2008-01-30
Awesome, thank you so much! :)  So Kworld is $60 and both the Dvico and pchdtv 5500 are $130.  So I think I will end up going w/ the Kworld.

Thanks again!

**Update:** I think I see [why the Kworld]("http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110") is cheap:
> It is important to note that the analog tuner of this card does not have a hardware MPEG2 encoder; it is an old fashioned frame grabber based tuner. Therefore, it is highly unrecommended for analog use.

---

### Post by newlinux on 2008-01-30
> **JPurdy said:**
> Awesome, thank you so much! :)  So Kworld is $60 and both the Dvico and pchdtv 5500 are $130.  So I think I will end up going w/ the Kworld.

Thanks again!

That's why I own 3 of them :)
There's no difference in the quality of the picture between the 3. There are plenty of threads here setting them up. If you have any questions or problems when you get them, don't hesitate to ask.

---

### Post by newlinux on 2008-01-30
Also, another option (more expensive) is to buy an HDhomerun and a dedicated analog tuner, like the PVR-150. It has hardware decoding and may provide a better quality analog picture than the other cards (they do software decoding for analog).

---

### Post by twkisner on 2008-01-30
> **mythbuntuChris said:**
> 

For the air2PC cards, I was thinking about either trying to find an enclosure that could house the pci card and connect via usb. Another thought was employing a pci extension component but I don't know if linux would be happy with this setup.

For wireless, I was hoping I could just plug in a wireless card via usb (unless there's a way to get it on the mobo that I'm not thinking about).



Yes, you can.  Just do your homework to find one that has a Linux compatable chipset (they are out there).

I had an extra PCI wireless card laying around that I tried to get to work for many frustrating hours with Ndiswrapper, since it wasn't linux compatable.  I gave up (my problem was no 64 bit windows driver) and wanted to run to a store buy a Linux compatable card to have a running system.  I couldn't find any on the shelf, so I ended up using a Dlink gaming adaptor (10/100 ethernet port to wireless bridge) which are always OS agnostic.

But if you plan ahead and order online something you know will work, you'll be OK.

As far as you PCI enclosure plan...I don't know about that.  I'd look for a 3 slot PCI riser board before I tried that.

---

### Post by stdPikachu on 2008-01-30
Wireless is fast enough for streaming HD now? I've found it struggles with SD DVB often enough under less-than-ideal conditions. Is anyone streaming over wireless successfully?

Yes, parent doesn't look like he's streaming anything yet but might in future.

---

### Post by twkisner on 2008-01-30
> **stdPikachu said:**
> Wireless is fast enough for streaming HD now? I've found it struggles with SD DVB often enough under less-than-ideal conditions. Is anyone streaming over wireless successfully?

Yes, parent doesn't look like he's streaming anything yet but might in future.

I don't try to stream HD over wireless (I have a combined backend/frontend).  My understanding is it is very difficult with 802.11g unless you have a really, really, really good signal.

The best alternative I've heard of working are those ethernet over power adaptors.

---

### Post by mythbuntuChris on 2008-01-30
I'm planning on using the wireless card for tying into updates and schedulesdirect (and possibly web surfing?) and not for transmitting tv signals to other devices.  For that, I plan on adding another frontend later down the road.

---

