---
title: "Nvidia card for Ubuntu Mythtv/HTPC?"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by uputer on 2007-06-24
I'm reading about video cards for HTPC and although the 8600 series seems to be the best price/performance choice for HTPCs, I read that XVMC will not be supported by Nvidia for Linux.   But, is XvMC only needed for underpowered systems?   If I get an Intel E6600 cpu or AMD X2 5000+ (or better) machine, I won't need XvMC?   I can use HD Purevideo or is this not supported in Linux?

How would one play HD in Linux using Mythtv in Ubuntu?   I did search the forums but wasn't able to answer these questions yet.  

I'll probably use SD most of the time or for now, at least, but since I am looking at getting a video card for a system I'm building I wanted to cover my bases.   My budget for a card is whatever is minimum for playing back 720p resolution or HD video (at max.).   SD will do but will the cpu and powerful system (cpu/ 2 gigs ram/etc. etc.) allow for playing divx, ati, xvid files etc.?   What if I get a HD DVD from the store?   Would it play?   I'm just curious as knowing the answers and what card allows the viewing without too much breakup/tearing/jitter will influence what I get.

Thanks.

---

### Post by newlinux on 2007-06-25
> **uputer said:**
> I'm reading about video cards for HTPC and although the 8600 series seems to be the best price/performance choice for HTPCs, I read that XVMC will not be supported by Nvidia for Linux.   But, is XvMC only needed for underpowered systems?   If I get an Intel E6600 cpu or AMD X2 5000+ (or better) machine, I won't need XvMC?   I can use HD Purevideo or is this not supported in Linux?

How would one play HD in Linux using Mythtv in Ubuntu?   I did search the forums but wasn't able to answer these questions yet.  

I'll probably use SD most of the time or for now, at least, but since I am looking at getting a video card for a system I'm building I wanted to cover my bases.   My budget for a card is whatever is minimum for playing back 720p resolution or HD video (at max.).   SD will do but will the cpu and powerful system (cpu/ 2 gigs ram/etc. etc.) allow for playing divx, ati, xvid files etc.?   What if I get a HD DVD from the store?   Would it play?   I'm just curious as knowing the answers and what card allows the viewing without too much breakup/tearing/jitter will influence what I get.

Thanks.

8600 is probably overkill an HTPC system (but if you are gaming you might want to stay with it). The 5 series and 6 series cards work great (and are better supported by myth and linux) all the way up to 1080p. No XvMC is not supported in the 8600 series but with the power processor you are talking about you don't need XvMC. HD Purevideo is not supported under Linux either. I run a P4 2.6Ghz Hyperthreading myth machine with a Geforce 440MX without XvMC and can playback 720p without a hitch. My 3800 and 4200 X2s do just fine as well, with a 6150 and 6200, using the nvidia drivers. Any dual core should handle HD with ease.

You won't have any problems playing the formats you mentioned except fo HD-DVD. Linux support for HD-DVD and Blu-ray is still coming around but your system would certainly be powerful enough to play it. For more on HD-DVD and Bluray in ubuntu check out:

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by uputer on 2007-06-25
I have a 5200 in an old Socket A computer.   Would it be worth buying a cheap 7600GT board instead or taking out the 5200? 

I suspect that the cpu would have to work that much harder if I used the 5200.   Neither card is HDCP compliant, though.   All this stuff is confusing.   I don't see how either one would work with HD-DVD.

---

### Post by newlinux on 2007-06-25
The 7600 wouldn't save you a ton of CPU cycles in Linux. In Linux the HD-DVD be decrypted before playing it so  the HDCP wouldn't  matter for your computer's output. I know people who watch HD-DVD in linux using the link I sent above with out any HDCP issues. If your 5200 has the outputs to the TV you are looking for then I'd go with that first. In Linux, HDCP isn't as much an issue (since most apps aren't going to be compliant with the encryption protocal and instead will break the encryption to decrypt), unless you are outputting HDMI to a set that doesn't take unencrypted TMDS input throuh HDMI. My HDTV sets are 2 years old but accept both HDCP and unencrypted TMDS through HDMI just fine. You might want to check in your case or not by a set that mandates all HDMI inputs must be HDCP.

---

### Post by BatPenguin on 2007-08-27
Hello there,

Did you end up getting the 8800? I'm about to upgrade my system and I'm trying to decide between different nvidia cards for upgrading my machine (HTPC). At the moment I have an Athlon XP 2800 but I'm going to be upgrading everything into (probably)  a quad core with something like 4 gigs RAM, a fast and large disk for myth storage and such. I'm going for a very fast machine mainly for the reason that my upgrades are so rare - this machine I've had since 2003. So I'm shooting for the new one to last at least until 2010 or so. I'll be using it for gaming as well (including a dual boot for now, Cedega, wine and VMWare as much as possible and hopefully more and more), so I would be interested in getting good gaming performance as well. But flawless Myth playback is really a top priority. With my current machine I've had some problems with deinterlacing so I'm hoping everything will be perfect this time.

But anyway, I'd be very interested in hearing what sort of performance people have with the various newer Nvidia cards. My choices are pretty much something quiet / fanless from the 7XXX line of cards of some very fast (but noisier) model from the 8XXX series. So far all we get on TV here is SD but hopefully we'll be getting HD soon, so it'd be good to be able to support both, naturally. The box is connected to a 37 inch LCD tv. Any suggestions? Thanks!

---

### Post by uputer on 2007-08-29
> **BatPenguin said:**
> Hello there,

Did you end up getting the 8800? I'm about to upgrade my system and I'm trying to decide between different nvidia cards for upgrading my machine (HTPC). At the moment I have an Athlon XP 2800 but I'm going to be upgrading everything into (probably)  a quad core with something like 4 gigs RAM, a fast and large disk for myth storage and such. I'm going for a very fast machine mainly for the reason that my upgrades are so rare - this machine I've had since 2003. So I'm shooting for the new one to last at least until 2010 or so. I'll be using it for gaming as well (including a dual boot for now, Cedega, wine and VMWare as much as possible and hopefully more and more), so I would be interested in getting good gaming performance as well. But flawless Myth playback is really a top priority. With my current machine I've had some problems with deinterlacing so I'm hoping everything will be perfect this time.

But anyway, I'd be very interested in hearing what sort of performance people have with the various newer Nvidia cards. My choices are pretty much something quiet / fanless from the 7XXX line of cards of some very fast (but noisier) model from the 8XXX series. So far all we get on TV here is SD but hopefully we'll be getting HD soon, so it'd be good to be able to support both, naturally. The box is connected to a 37 inch LCD tv. Any suggestions? Thanks!
I suggest going to the Phoronix website to read about the site's experiences with graphics cards under Linux.   I think the 8600 series is probably good as any although the 6600+  (meaning 6600 and up) cards should be good for Linux.  Nvidia has a section on their website for Linux drivers and the 'Envy' application is often mentioned as a source for help:
([http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I'm looking at a 8600 series card to cover me for both Windows and Linux.  The drivers might be an issue but eventually such a card should work on either system with growing pains.  But, hopefully, the respective developers can iron out the kinks and not take too long a time at doing it.

---

### Post by BatPenguin on 2007-08-31
> **uputer said:**
> I suggest going to the Phoronix website to read about the site's experiences with graphics cards under Linux.   I think the 8600 series is probably good as any although the 6600+  (meaning 6600 and up) cards should be good for Linux.

Thanks for the tip, hadn't actually seen that site before. Yes, I think I'll go for one of the high-end 8600 or 8800 cards. I guess xvmc shouldn't be that important with the type of fast CPU I'll be getting, and that way I'll get the gaming performance I want as well.

---

### Post by newlinux on 2007-08-31
> **BatPenguin said:**
> Thanks for the tip, hadn't actually seen that site before. Yes, I think I'll go for one of the high-end 8600 or 8800 cards. I guess xvmc shouldn't be that important with the type of fast CPU I'll be getting, and that way I'll get the gaming performance I want as well.

If you are thinking about a quad core you are set on the linux HTPC side of things no matter what nvidia card you get, so you are right, you definitely won't need XvMC. For gaming the card will matter, so probably a good choice.

---

### Post by uputer on 2007-09-01
> **newlinux said:**
> If you are thinking about a quad core you are set on the linux HTPC side of things no matter what nvidia card you get, so you are right, you definitely won't need XvMC. For gaming the card will matter, so probably a good choice.
One of my computers will be a Quad Core.   I wasn't planning on it being a Linux computer but I was considering an Nvidia video card so that it would be easier to use/install a Linux distro.   I'm not sure ATI/AMD will have usable Linux (video) drivers for their HD 2xxx cards soon enough.

---

