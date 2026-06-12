---
title: "Internal player uses only one core."
date: 2010-06-20
forum: Mythbuntu
---

### Post by jmail524 on 2010-06-20
Hi everyone,

I am running Mythbuntu 10.04 on a dual-core Athlon X2 3.1GHz system. When I playback high bitrate video, such as that from a Blu-ray disc, the video is very jerky.  I checked my CPU usage via the "htop" command and it shows that I am using one core at 100% and the other core at about 3-4%.  Does the Internal video player (or FFMPEG) support multiple cores?  It seems to me that I have quite a lot of reserve power left and should not be seeing this issue.

I appreciate any info on this matter.

Thanks.
Brian

---

### Post by nickrout on 2010-06-20
> **jmail524 said:**
> Hi everyone,

I am running Mythbuntu 10.04 on a dual-core Athlon X2 3.1GHz system. When I playback high bitrate video, such as that from a Blu-ray disc, the video is very jerky.  I checked my CPU usage via the "htop" command and it shows that I am using one core at 100% and the other core at about 3-4%.  Does the Internal video player (or FFMPEG) support multiple cores?  It seems to me that I have quite a lot of reserve power left and should not be seeing this issue.

I appreciate any info on this matter.

Thanks.
Brian

I believe Internal uses one core only. You may be best to get a nVidia GT 210/220/240 and use VDPAU to take the load off your CPU.

---

### Post by Linuxforall on 2010-06-20
Or you can compile mplayer with Core AVC for using both your cores in case you don't wish to splurge for new video card. The instructions are on the tutorial thread.

---

### Post by jmail524 on 2010-06-21
I don't think I can add a video card to the system as it has only 1 PCI expansion slot.  I haven't found any PCI cards that support VDPAU and have an HDMI port.  (My TV has no analog audio inputs.)

Does MythTV's internal player use mplayer or will I have to tell MythTV to play my videos using an external player?  I have come to enjoy MythTV's advanced playback options available with it's internal player. (ie., bookmarks, audio track selection, aspect ratio and playback speed.)

---

### Post by nickrout on 2010-06-21
> **jmail524 said:**
> I don't think I can add a video card to the system as it has only 1 PCI expansion slot.  I haven't found any PCI cards that support VDPAU and have an HDMI port.  (My TV has no analog audio inputs.)

There are (or were) some PCI vdpau capable cards, you have to look hard to find them though. > 

Does MythTV's internal player use mplayer or will I have to tell MythTV to play my videos using an external player?  I have come to enjoy MythTV's advanced playback options available with it's internal player. (ie., bookmarks, audio track selection, aspect ratio and playback speed.)

Internal is Internal, but you can specify it to use mplayer if you so desire. It's all in mythvideo setup. 

mplayer has aspect ratio selection, audio track selection, not sure about bookmarks. You can speed it up, but the sound goes to "Alvin and the Chipmunks" mode.

Time for a new front end?

PS are you sure you have no PCI-E slot? what is the motherboard?

---

### Post by jmail524 on 2010-06-22
The frontends I'm using are an old MSI Media Lives which have served me well for years.  The thing I like most is they are less than 14 inches deep so they fit in both of stereo racks perfectly.  Most HTPC cases are 16-17" deep which was an annoying depth for even tube TV's "back in the day", they are far too deep for any rack I own.  The units do have a PCIe x16 slot, but it requires a riser card and I have been able to find one that fits.  I also liked that the MSI MEdia Live has a VFD display, integrated IR receiver with remote, optical SPDIF out and all RCA connections on the back.

I will do some more searching for a VDPAU PCI card with HDMI.  I admit that I have only looked on Newegg so far.  Do you think since a good portion of the decoding will be done on the video card that the PCI bus will have enough bandwidth to handle the task of rendering HD video?

As for mplayer, I'll give it a try.  I'm sure it's somehow possible to map remote buttons to control the playback options.  Bookmarks would be nice but not a deal breaker.

Also, maybe it is time for a new frontend.  I certainly use the system enough to warrant putting a little more money into it plus the ability to use the latest hardware would give me added benefits.  Of course this all depends on me finding a decent looking and functional case that fits into my racks.

I appreciate the suggestions.

Thanks.
Brian

---

### Post by nickrout on 2010-06-23
you really want to find the right riser card IMHO!!

---

### Post by jmail524 on 2010-06-23
I found a flexible PCIe x16 riser card/cable on eBay for about $15.  I'll order one and give it a try and hope it works.

What video chipset is recommended for VDPAU decoding. Will a GeForce 210 with 512MB is sufficient for the job of decoding 1080p content?  (Found a card on Newegg for $35.00)

Thanks.
Brian

---

### Post by nickrout on 2010-06-24
> **jmail524 said:**
> I found a flexible PCIe x16 riser card/cable on eBay for about $15.  I'll order one and give it a try and hope it works.

What video chipset is recommended for VDPAU decoding. Will a GeForce 210 with 512MB is sufficient for the job of decoding 1080p content?  (Found a card on Newegg for $35.00)

Thanks.
Brian

I believe so. May pay to  check on the mailing list.

---

### Post by jmail524 on 2010-06-25
I found an ECS GeForce 210 with 512MB for about $27.  I ordered it and the flexible PCIe riser.  Hopefully this will fix my video stutter problem.  If it does, it's a nice cheap fix for only $40.  If it doesn't, well, I've blown more that $40 on other useless things before.  I'm not expecting to get the PCIe riser for about 7-10 days as I think it's coming from somewhere in china.  I'll post back when I have tested this setup and let you know how is working.

Thank you for the suggestions and help.

Brian

---

### Post by jmail524 on 2010-07-01
I just received my PCIe riser and GeForce 210 video card.  Installed the latest nVidia drivers and setup Mythbuntu to use VDPAU.  Wow, what a difference.  The CPU maybe hits about 5% on one core when playing back HD material.

Thank you very much for all of your help with this issue.  I'm ecstatic that $40 fixed my problem and allows me to continue using the frontends that I currently have.

Thanks,
Brian

---

### Post by nickrout on 2010-07-01
> **jmail524 said:**
> I just received my PCIe riser and GeForce 210 video card.  Installed the latest nVidia drivers and setup Mythbuntu to use VDPAU.  Wow, what a difference.  The CPU maybe hits about 5% on one core when playing back HD material.

Thank you very much for all of your help with this issue.  I'm ecstatic that $40 fixed my problem and allows me to continue using the frontends that I currently have.

Thanks,
Brian

Glad you had success with that!

---

### Post by paradigm2 on 2010-07-03
> **jmail524 said:**
> I don't think I can add a video card to the system as it has only 1 PCI expansion slot.  I haven't found any PCI cards that support VDPAU and have an HDMI port.  (My TV has no analog audio inputs.)



You can get a Nvidia 8400 GS PCI (Not PCI-E) from Tiger direct (among others).  It supports VDPAU feature set B.  I believe the Nvidia 9400 is also available as a PCI (Not PCI-E) card as well although from memory I believe it only supports feature set A.

[https://secure.wikimedia.org/wikipedia/en/wiki/Nvidia_PureVideo](https://secure.wikimedia.org/wikipedia/en/wiki/Nvidia_PureVideo)

Note that the PCI Bus will be inferior to the PCI-e bus by nature and may limit bandwidth.  For playing video however I have not ran into any problems whatsoever with this configuration.


Edit: I see you already resolved the problem now. Leaving up for others who search for this issue. :)

---

### Post by jmail524 on 2010-07-14
Just an FYI for anyone else in my position:

The GeForce 210 doesn't seem to be powerful enough to de-interlace 1080i video without stuttering.  I have now bought a GeForce GT220 card (based on recommendations in multiple forums) and now playback of all material seems to be very fluid and looks good.  This problem only manifested itself only when using the "VDPAU High Quality" as the other settings don't do de-interlacing.

Everything seems to be working well and I appreciate all of the help/recommendations.

PS: If anyone is having problems getting audio over HDMI working with the 210/220 cards, there is a very useful thread (_*[http://ubuntuforums.org/showthread.php?p=9591051#post9591051](http://ubuntuforums.org/showthread.php?p=9591051#post9591051)*_) along with my solution to the problem I was having.

Thanks,
Brian

---

### Post by nickrout on 2010-07-15
> **paradigm2 said:**
> 
Note that the PCI Bus will be inferior to the PCI-e bus by nature and may limit bandwidth.  For playing video however I have not ran into any problems whatsoever with this configuration.


If you are using vdpau then the PCI bus is plenty fast enough. Just do the maths, PCI - 133MBytes/s. The most intense video you are likely to get is Bluray at 48Mbits/s.

Of course if the CPU is decoding the video and pumping it to the card (eg if you are doing hi definition xvid video which vdpau does not handle on 8xxx cards) then bets are off. Fortunately this is unlikely to be a problem because most HD video is either mpeg2 (if broadcast in some markets) or h.264 (as broadcast in some countries and as most HD media is encoded), and vdpau can do those. In other words HD in any codec that vdpau can't do is rare.

---

