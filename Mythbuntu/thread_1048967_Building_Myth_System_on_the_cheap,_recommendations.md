---
title: "Building Myth System on the cheap, recommendations?"
date: 2009-01-24
forum: Mythbuntu
---

### Post by BassKozz on 2009-01-24
I am buying 2 used [Compaq D51s (small form factor)]("http://h18000.www1.hp.com/products/quickspecs/11349_na/11349_na.HTML") from a local college.  I plan on buying 2x1GB PC2100 sticks (one for each machine) from eBay. I also plan on purchasing [2x500GB WD PATA drives from newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136111").

I my house we mainly watch local channels and occasionally watch cable (non-premium, i.e. HBO, ShowTime) channels, i.e. MTV, E!, ESPN, etc...
I am planning on purchasing a HDHomeRun to pull QAM off my cable lines and for the HD local channels, it is my understanding that the HDHomeRun can NOT pull cable channels but only the HD local channels which are broadcast by the cable companies via QAM, **is that correct**? 
If so, I will purchase 1 analog Tuner card to record the cable channels on one of the boxes. Again, **Suggestions**?

Now I just need a **recommendation** for a PCI card to buy for these rigs?
Preferably one that will have VDPAU support, I think that [narrows it down to these]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000380048%201305520548%201069609642%20106791921&bop=And&Order=PRICE").  I need something that will help out processing h.264 1080i feeds from the HD HomeRun.

Since I am limited to 500GB, I planned on making both of these backends&frontends (one being the master and one slave obviously), that way they can share in the responsibilities of scheduling and transcoding, etc...
**Is that the best route to go**?

**Am I crazy, am I asking too much from these old rigs**?

---

### Post by BassKozz on 2009-01-25
:bump:

---

### Post by scary_jeff on 2009-01-25
I did start to write a reply yesterday but didn't finish it because I decided I probably wasn't the best person to ask, but since nobody else replied...

The nVidia website says that the 8400 do support high def acceleration, see _[here]("http://www.nvidia.com/page/purevideo_hd.html")_, click purevideo hd support table on the left. However, when I was building my system, I ended up getting an 8500, because I think I read somewhere on the _[nvnews linux forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14")_ that this was the cheapest card that supported full VDPAU acceleration for HD. This could have changed if they have updated it, and I can't find the post I read. Those forums are pretty good; some nVidia guys post there, so I'm sure you will be able to find out for certain if the 8400 PCI will support VDPAU for HD.

This is important because I think with your system specs, your only chance of decoding HD content is by using VDPAU. Note that this is only supported in mythtv if you build from source or find some unofficial realease that includes support for it, and that VDPAU itself is in beta. If you get it to work, I think those systems will be ok with that amount of RAM. I haven't tried it, so again it might be worth checking the nvnews (possible phronix or some other forum, but I haven;t used those), to get a feel for whether your HD programs will be wathcable with VDPAU on that system (assuming VDPAU will work with that card...).

If it were me, I would put both 500gb drives in the same machine, and use a smaller drive in the second machine, which would be slave only. In my mind this would be an easier system to set up... however, if you plan to record a couple of channels whilst watching some HD channel, you may benefit from sharing the processing load across two machines.

I don't know anything about cable tuners so that's all I've got! Hope this is some help to you.

---

### Post by newlinux on 2009-01-25
What CPU will you be using?

The HDhomerun does unencrypted QAM. The channels you can tune via unencrypted QAM will vary greatly from area to area. Check
[http://www.silicondust.com/hdhomerun/channels](http://www.silicondust.com/hdhomerun/channels). Different places encrypt different QAM channels. I would expect at least the local HD locals, but in my area I now get all the basic channels unencrypted via QAM.

If you are using myth, VDPAU will won't be integrated until .22, I believe. So you could use a patched mplayer, but not for liveTV or recordings. You'd need to compile your own myth until .22 is officially released.

More info on myth and VDPAU, including the cards that support it which include only second generation purevideo HD cards (called VP2 or Purevideo HD 2):

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by movieman on 2009-01-25
> **newlinux said:**
> What CPU will you be using?

The specs for that system say P4 and Celeron, so they're not likely to handle decoding H.264 1080 files; certainly my 3GHz P4 can't manage it without dropping frames, even with hyperthreading.

So GPU-assist is probably the way to go.

---

### Post by GCFreak on 2009-01-25
I'm sorry to say this, but those computers won't have a hope of running H.264 HD content, sorry. VDPAU support starts at the GeForce 8 series, and AFAIK they're virtually all PCI Express, while the D510s are AGP4X.

You CAN build a good MythTV system on the cheap. You just need to get clued up on these things and shop around.

---

### Post by movieman on 2009-01-25
> **GCFreak said:**
> I'm sorry to say this, but those computers won't have a hope of running HD content, sorry. VDPAU support starts at the GeForce 8 series, and AFAIK they're virtually all PCI Express, while the D510s are AGP4X.

I see PCI Geforce 8400 and 9250 cards for sale online; no idea whether they're fast enough.

---

### Post by newlinux on 2009-01-25
> **movieman said:**
> The specs for that system say P4 and Celeron, so they're not likely to handle decoding H.264 1080 files; certainly my 3GHz P4 can't manage it without dropping frames, even with hyperthreading.

So GPU-assist is probably the way to go.

Yes, I know. But depending on the CPU, GPU assist won't even help enough, so he needs to pick one good enough. Also I think the OP incorrectly assumes the  hdhomerun will output h.264? QAM is mpeg-2 which with the proper CPU wouldn't requrire any gpu assist (I have a 3ghz P4 prescott HT which does just fine with 1080i mpeg2).

---

### Post by newlinux on 2009-01-25
> **movieman said:**
> I see PCI Geforce 8400 and 9250 cards for sale online; no idea whether they're fast enough.

I doubt a PCI bus has enough bandwidth, more bandwidth was the reason for AGP and then PCIe.

---

### Post by movieman on 2009-01-25
> **newlinux said:**
> I doubt a PCI bus has enough bandwidth, more bandwidth was the reason for AGP and then PCIe.

Raw 24-bit RGB, or even YUV HD frames are probably over the bandwidth limit for PCI, but if the card is doing much of the decoding then you wouldn't have to send the full decoded frames to it.

I agree on the MPEG-2 front, my P4 has no problem playing (or editing) 1080i MPEG-2, or some other Windows codecs, but H.264 is just too complex.

---

### Post by BassKozz on 2009-01-26
Just to clear up, the proc on these machines I am planning to purchase is a 2.4Ghz P4 (**NOT** celeron).

I do realize that VDPAU won't be release until MythTV .22 is released, and the drivers are still in BETA.  I don't plan on compiling MythTV to reap the benefits of VDPAU, but I want to buy a card now with VDPAU support so that I am ready to take advantage of it when it's released (out-of-trunk) with Mythbuntu.

As for the debate about PCI bandwidth for VDPAU, according to the MythTV wiki there are several users who are using PCI cards w/ VDPAU, successfully. [User Results]("http://www.mythtv.org/wiki/VDPAU#User_results")

So with that out-of-the-way, **with VDPAU enabled will I be able to play h.264 1080p video?**
**Also if I get one of these cards will I be able to play the HDHomeRun recordings (non h.264) on these rigs (w/out VDPAU)?** Even without VDPAU the GPU should help with the playback of recordings, correct?

> **scary_jeff said:**
> If it were me, I would put both 500gb drives in the same machine, and use a smaller drive in the second machine, which would be slave only. In my mind this would be an easier system to set up... however, if you plan to record a couple of channels whilst watching some HD channel, you may benefit from sharing the processing load across two machines.

Unfortunately these machines only have space for 1 3.5" IDE HD, so I can't put 2x500GB drives in one machine.  **I am more curious to know if I setup both of these rigs as back+front/ends will they share in collecting the recordings from the HDHomeRun?  Will they be powerful enough to playback and record at the same time?**

---

### Post by newlinux on 2009-01-26
> As for the debate about PCI bandwidth for VDPAU, according to the MythTV wiki there are several users who are using PCI cards w/ VDPAU, successfully.

I wasn't really debating whether or not there was enough bandwidth with VDPAU. I'd be worried about the PCI bandwidth for HD when you are *not* using VDPAU, which for recordings and liveTV in myth you can't use if you aren't using myth .22. What will do until then for recordings? It might work, but I'm not sure - that's all I'm trying to say. Proceed at your own risk.
> 
So with that out-of-the-way, with VDPAU enabled will I be able to play h.264 1080p video?
Also if I get one of these cards will I be able to play the HDHomeRun recordings (non h.264) on these rigs (w/out VDPAU)? Even without VDPAU the GPU should help with the playback of recordings, correct?



The GPU helps very little in Linux if you aren't using VDPAU or XvMC (mpeg-2 only). A P4 2.4Ghz without any hardware assist is borderline. I used to have a P4 2.6ghz that could decode 720p and 1080i mpeg-2 without any hardware assist (keeping other processes at a minimum). With XvMC it definitely could do 720p/1080i mpeg-2.

I can't speak directly to whether or not VDPAU with a 2.4Ghz will definitely be able to decode 1080p h.264, but hopefully someone has more experience with that and will chime in.

---

### Post by BassKozz on 2009-01-26
**_Anyone know:_**
Will I be able to play non-transcoded screams (live or recorded) from a HDhomerun at the same time I am recording via the HDhomerun on these machines?
I need to make a decision on buying these machines by tomorrow, and I am on the edge trying to figure out if it's a good deal to buy these or wait and buy something more powerful (BTW, I am paying $30 per machine, $60 total for both).

---

### Post by newlinux on 2009-01-26
> **BassKozz said:**
> **_Anyone know:_**
Will I be able to play non-transcoded screams (live or recorded) from a HDhomerun at the same time I am recording via the HDhomerun on these machines?
I need to make a decision on buying these machines by tomorrow, and I am on the edge trying to figure out if it's a good deal to buy these or wait and buy something more powerful (BTW, I am paying $30 per machine, $60 total for both).

Yes, although depending on your GPU and use of XvMC your playback may struggle with HD streams (as discussed earlier), but this will have nothing to do with recording. Digital recording is just capturing a stream - no encoding involved, thus very minimal CPU utilization.

---

### Post by BassKozz on 2009-01-26
ok well, looks like I am gonna pull the trigger on these rigs, wish me luck ;-P

I'll report back with my findings on playback/recording issues once I've had time to set up Mythbuntu.

---

### Post by BassKozz on 2009-01-27
Question Moved: [Plz, Help me pick a PCI GPU (with VDPAU, for future release)]("http://ubuntuforums.org/showthread.php?t=1052130")

---

### Post by kimgkimg on 2009-02-10
BassKozz,
Please keep us updated with your progress.  I'm going to be trying a similar setup using a Dell SX280 SFF PC.  I'm thinking the use of the HDHomerun will offload much of the processing to capture video, I'm just not sure I'll be able to playback video using the built-in video card (which I think is some Intel GMA variety.)

---

### Post by BassKozz on 2009-02-16
> **kimgkimg said:**
> BassKozz,
Please keep us updated with your progress.  I'm going to be trying a similar setup using a Dell SX280 SFF PC.  I'm thinking the use of the HDHomerun will offload much of the processing to capture video, I'm just not sure I'll be able to playback video using the built-in video card (which I think is some Intel GMA variety.)


Well after alot of support from mythmaster over on the AVSforums: [http://www.avsforum.com/avs-vb/showthread.php?t=1113747](http://www.avsforum.com/avs-vb/showthread.php?t=1113747) & [http://www.avsforum.com/avs-vb/showthread.php?t=1097364](http://www.avsforum.com/avs-vb/showthread.php?t=1097364)

I purchased the [SPARKLE SFPC84GS512U2LP GeForce 8400 GS 512MB 64-bit GDDR2 PCI HDCP Ready Video Card ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187042").
I am up and running smoothly with the [latest Nvidia drivers]("http://www.nvnews.net/vbulletin/showthread.php?t=122606") (180.29) & [patched mplayer]("ftp://download.nvidia.com/XFree86/vdpau/"), and installed Mythbuntu [+fixes]("http://www.mythbuntu.org/auto-builds") [+VDPAU patch]("http://www.avenard.org/files/mythtv-vdpau/").
Live TV and recorded shows play flawlessly with ~10% CPU usage:cool:

---

