---
title: "Are Nvidia graphics cards still preferred to ATI?"
date: 2010-04-11
forum: Multimedia Software
---

### Post by potatan on 2010-04-11
Hi,

After a PSU and motherboard failure, I'm about to spec out a new PC.  The last time I looked, Nvidia was the preferred graphics chipset as they tended to support Linux better than ATI.  Is this still the case?

Dabs.com seem to have lots of ATI cards in stock but hardly any Nvidia (despite offering a similar sized range), but I don't want to get an ATI card if it's not preferred for technological reasons (or even FOSS ethical reasons!).  

Many thanks in advance

Paul

---

### Post by Alan James on 2010-04-11
Last I checked Nvidia is still better than ATI.

---

### Post by WinterRain on 2010-04-11
Nvidia is generally better supported in linux. I've never had a problem.

---

### Post by ShadowTek on 2010-04-11
There's an ongoing discussion of nVidia vs ATI in the gaming forum.
[http://ubuntuforums.org/showthread.php?t=1388516](http://ubuntuforums.org/showthread.php?t=1388516)

---

### Post by markbuntu on 2010-04-11
ATI drivers are behind nvidia in linux but they are slowly catching up. ATI is more reliable hardware wise. A lot of vendors and OEMs have dropped Nvidia because of hardware failures that Nvidia denied and covered up for years.

---

### Post by 2hot6ft2 on 2010-04-11
All of mine are NVIDIA and if I was buying a pc or graphics card today I would be looking at the NVIDIA and ignoring the ATI cards. But that's me.

---

### Post by 3rdalbum on 2010-04-11
> **markbuntu said:**
> ATI drivers are behind nvidia in linux but they are slowly catching up. ATI is more reliable hardware wise. A lot of vendors and OEMs have dropped Nvidia because of hardware failures that Nvidia denied and covered up for years.

Citation Needed.

Nvidia is definitely preferable. If your favorite store doesn't have many Nvidia cards, then try another store. Don't buy ATI.

---

### Post by jrusso2 on 2010-04-11
If you listen to people and buy ATI I wish you lots of luck.

---

### Post by splicerr on 2010-04-11
ATI has the better hardware, Nvidia has the better Linux drivers. Choose ATI and you have excellent hardware with mediocre Linux drivers, choose Nvidia and you have better Linux drivers with mediocre hardware. Either way you're screwed ;)

---

### Post by Volcom3 on 2010-04-11
Yes on the Nvidia. I had an ATI and ran into tons of issues gettin Ubuntu and Compiz to run right. I bought a Nvidia and everything ran smooth after that

---

### Post by potatan on 2010-04-13
Well that's that settled then - Nvidia it is!  Or more specifically, a GeForce 9800GT 1GB PCI express with HDMI.  While I was at it, I ordered the following too:

```

Manufacturer : AMD
Product :  Phenom II X2 545 3.0GHz CPU S
 
Manufacturer : CORSAIR
Product : 650W TX SERIES ATX PSU
 
Manufacturer : ANTEC
Product : Three Hundred Case Black
 
Manufacturer : ASUS
Product : AM3 AMD 770 DDR2 ATX
```

Hopefully that should be me sorted for the next few years!

Just need a nice monitor to go with it all now...

Thanks for the comments.

---

### Post by gradinaruvasile on 2010-04-13
Maybe take a look at the 200 series nvidia cards too. They support full VDPAU decoding (set C) - the 9800 supports only A set and that is just isnt enough for HD movie playback.

---

### Post by ShadowTek on 2010-04-13
> **gradinaruvasile said:**
> Maybe take a look at the 200 series nvidia cards too. They support full VDPAU decoding (set C) - the 9800 supports only A set and that is just isnt enough for HD movie playback.

 I have a 9600GT 512 MB, and it plays all 720p just fine.
 
 1080s are iffy though. Some do well, while others are unwatchable.

---

### Post by gradinaruvasile on 2010-04-13
I have a 8200 integrated at home (slow 3d performance) and it plays 1080p perfectly (Athlon single core 3200+ proc, ~15% CPU usage) - it has VDPAU B.
I have a 210 at work (VDPAU C), eats 1080p for breakfast (core2duo CPU, ~5%). 
On my work laptop i have Quadro 135M (VDPAU A) - plays only some 1080p movies and not all correctly (stuttering etc).
Choosing 200 series means that you will have all VDPAU features meaning all (ok, maybe not all but very few wont work) HD movies will play. Also, being newer models, they will benefit of new technologies in their drivers. Older models will not.

---

### Post by hackb0y294 on 2010-04-13
Yeah! BY ME!!!!!! But really, ATI Makes the top graphics card for the moment, the Radeon HD 5970, although nVidia is in the R&D stage of its new architecture, which should easily top anything ATI has to offer.

---

### Post by cascade9 on 2010-04-14
> **gradinaruvasile said:**
> Maybe take a look at the 200 series nvidia cards too. They support full VDPAU decoding (set C) - the 9800 supports only A set and that is just isnt enough for HD movie playback.

For the GT 2xx, yes, they do support 'C' but the perfromance cards, GTX 2xx they only support 'A' like the 9800GT, and just as an aside, I dont know what the GTS250 (rebadged 9800GT/8800GT) does, I'm not sure but I would guess it only does 'A' as well. 

If potatan bought the 9800GT in order to get good frame rates, and/or play newer games, a GT2xx card might not be enough. If there is no gaming, then GT2xx should be fine (but then the 9800GT is pointless, at best). 

From what I know, if you have enough CPU grunt you can play any HD. I've never tried with 1080p (not much in the way of 1080p around for me) but I do know that my +4800 palys 720p fine without VDPAU. IIRC, you need about 2.5Ghz+ (dual core) or 3.5Ghz+ (single core) to get HD playback without stuttering. 

@ potatan- why does your avatar say 'LEORNA"? ;)

---

### Post by gradinaruvasile on 2010-04-14
Playing 720p is easy. 1080p is another story.
On 2.33GHz Core2Duo 1080p movies eat 100-130% (mplayer-mt with multithreading) without VDPAU and dropping frames. 720p its 30-50%. This is using xv on nvidia 210.

---

### Post by cascade9 on 2010-04-14
> **gradinaruvasile said:**
> Playing 720p is easy. 1080p is another story.
On 2.33GHz Core2Duo 1080p movies eat 100-130% (mplayer-mt with multithreading) without VDPAU and dropping frames. 720p its 30-50%. This is using xv on nvidia 210.

I didnt know that 1080p was that much nastier. Looks like I'm going to have to source a 1080p video for testing. ;)

---

