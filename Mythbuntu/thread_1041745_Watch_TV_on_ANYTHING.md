---
title: "Watch TV on ANYTHING"
date: 2009-01-16
forum: Mythbuntu
---

### Post by cartisdm on 2009-01-16
I have another post [here]("http://ubuntuforums.org/showthread.php?t=1041639&highlight=tuner") about trying to get my Mythbuntu installation running but it doesn't seem to be something anyone can solve easily.

I use that computer as my TV and until I'm able to figure out my Mythbuntu installation I don't have a simple solution to watching TV, Movies, and videos.  I removed my Windows XP MCE because it was pirated and I don't have a legit code to reinstall it.  What are my options?

Apparently my HVR-1600 tuner card isn't an easy out-of-the-box install with MythTV.  Are there other softwares out there to get the same effect as MCE/MythTV?  Is there an add-on to Windows XP at all?  My desktop doesn't seem to want to install my Vista, I already tried that route....

---

### Post by insanity54 on 2009-01-28
I feel your pain man. Last week, I bought a computer to use as a media center, and I'm using the Hauppauge 1600 and the Hauppage 1250. Mythtv will occasionally see the 1600 tuner, but half the time it cannot probe the device. I've never been able to "Watch TV" on Mythtv. It's quite depressing, really.

Mythtv doesn't even see the 1250, but that's a separate story.

I'm actively working on this media center project PC, I'll be trying some more things the next few days and I'll get back to you if I find anything out.

---

### Post by klc5555 on 2009-01-28
> **insanity54 said:**
> I feel your pain man. Last week, I bought a computer to use as a media center, and I'm using the Hauppauge 1600 and the Hauppage 1250. Mythtv will occasionally see the 1600 tuner, but half the time it cannot probe the device. I've never been able to "Watch TV" on Mythtv. It's quite depressing, really.




In the first machine I put my 1600 on, I found the machine couldn't boot at all unless the card was in the 1st PCI slot. Corrected this, then the cx18 spawn-of-satan driver module would not load correctly at bootup, ever, though it would appear to have done so. Myth couldn't probe the card. I came to realize that after every bootup I had to unload and reload the module before it would properly initialize. sudo rmmod cx18;sudo modprobe cx18  Then it would work. Finally I just made a two-line bootup script to automate it.

On another machine, the same card would fail loading the module maybe only one boot out of twenty. Works great on analog; sucks on digital. I'll never buy another one.

---

### Post by sniperbob on 2009-01-30
Hm.. I have a Hauppauge 1600 card, running on 8.04 Hardy and MythTV just fine.

One big gotcha I found, that needed fixing:

The mythtv daemon user that runs the mythtv backend needed to be added to the video group (which owns video0, hence why I couldnt watch video)

And obviously, the cx18 driver. I didnt seem to have problems with it, following the guide (dont have link handy)

---

### Post by klc5555 on 2009-01-30
> **sniperbob said:**
> Hm.. I have a Hauppauge 1600 card, running on 8.04 Hardy and MythTV just fine.

One big gotcha I found, that needed fixing:

The mythtv daemon user that runs the mythtv backend needed to be added to the video group (which owns video0, hence why I couldnt watch video)

And obviously, the cx18 driver. I didnt seem to have problems with it, following the guide (dont have link handy)

There are at least two relevant guides that I'm aware of. One is the very cursory page on the cx18 driver at ivtv.org

[http://www.ivtvdriver.org/index.php/Cx18](http://www.ivtvdriver.org/index.php/Cx18)

The second is devoted to the 1600 card itself on the Myth wiki:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Both of these are in need of expansion and rewrite. The 1600 guide, at least, has been recently updated to show that the mmio= parameter has evidently been obsoleted in recent versions of the cx18, but does not really indicate whether a solution exists for anyone still suffering from I2C bus glitches (which still persist), other than finding an old version of the driver. 

Nor does the guide reference the very common problem that users have getting the cx18 working with the proprietary Nvidia drivers, even though the solution with vmalloc at boot is quite straightforward. 

I like the 1600 card OK for analog. Once I make sure to get that first post-boot capture done check that the cx18 has loaded properly. Never could get the 1600's QAM tuner to find more than 7 of the 21 QAM stations that the pcHDTV5500 sitting in the next PCI slot over could find. So I just began to use my 1600 as an analog replacement for the terrible analog support in the 5500. In that respect the two cards complement each other fairly well.

Cheers! :)

---

### Post by newlinux on 2009-01-30
> **klc5555 said:**
> ...

I like the 1600 card OK for analog. Once I make sure to get that first post-boot capture done check that the cx18 has loaded properly. Never could get the 1600's QAM tuner to find more than 7 of the 21 QAM stations that the pcHDTV5500 sitting in the next PCI slot over could find. So I just began to use my 1600 as an analog replacement for the terrible analog support in the 5500. In that respect the two cards complement each other fairly well.

Cheers! :)

This is a small point, and you probably have already tried this, but is it that the 1600 just can't scan and find all your QAM stations? Have you tested if it can tune the ones it couldn't find in a scan? If so since you can get them all with your pchdtv 5500 you could just have them use the same QAM video source your pchdtv 5500 does.

---

### Post by klc5555 on 2009-01-30
> **newlinux said:**
> This is a small point, and you probably have already tried this, but is it that the 1600 just can't scan and find all your QAM stations? Have you tested if it can tune the ones it couldn't find in a scan? If so since you can get them all with your pchdtv 5500 you could just have them use the same QAM video source your pchdtv 5500 does.

Thanks for the suggestion. I've already tried some things that were similar. But it seems that the digital half of my 1600 is almost deaf.

The digital tuner will not tune or lock to anything without scanning. Scanning in Mythtv produces signal strength readings of close to 0% "no signal" (though the signal strength "thermometer" does bump a bit as the scan progresses. The neighboring 5500 registers most signals at 92-98% (as does the analog half of the 1600). dvb-apps scan gave me a channels.conf for the 1600 card consisting of 2 (out of 21) QAM stations.

Since the digital tuner appeared to be a bit deaf, I put a hearing aid on it --a little motorola line-amp. dvb-apps now gave me 7 QAM stations, all of which can be tuned into from time to time. Apparently the best I can do. I configured a separate input for the digital 1600, so that myth wouldn't try to assign it to record a channel it can't hear, and left it at that.  

If I owned a Windows machine I could stick the card into, I'd check to determine whether the problem is hardware or the beta cx18 driver. But until I throw together such a machine, I guess I'll continue to use the card as (mostly) an analog-only card.

All the best! :)

---

### Post by issih on 2009-01-30
As the OP asked if there was anything he could use under win XP I thought I'd mention a couple I used to play with prior to seeing the linux light:

[http://www.gbpvr.com/](http://www.gbpvr.com/)

[http://www.team-mediaportal.com/](http://www.team-mediaportal.com/)

of the two I settled on mediaportal, as its rettier, and I'm a tart

---

