---
title: "Flash not working in 10.04, 12.04"
date: 2012-05-14
forum: Multimedia Software
---

### Post by DexterF on 2012-05-14
AMD 3400+, 2GB RAM, GeForce FX5200 (AGP likely, but not 100% sure)

Kubuntu 10.04 and 12.04 32b, no fancy repos. Mozilla Firefox.

Used to run flash plugins fairly well, then all of a sudden stopped working in 12.04. Only shows a black rectangle in youtube.
My guess: either X or flash got updated and broked.
this was on 10.04, told the user to wait until 12.04 is out. So today upgraded.
Found that even while I installed nvidia-173 it won't load as nvidia is still working on getting the 173to work with the new kernel API ( I wonder tho: why is 173 then released? In an LTS?).

So right now it's nouveau.

12.04: still no flash. Tried flashplugin-installer, tried adobe-flashplugin, tried purging this and uninstalling that and copying the .so manually to moz' plugin dir - nuthin.

Cannot tell the culprit, have no idea where to look, what to try.

---

### Post by kc1di on 2012-05-14
have you installed ubuntu-restricted-addons and ubuntu-restricted-extras that should pull flash for you and works great here. 

if all else fails try firefox flash aid addon.

---

### Post by DexterF on 2012-05-22
Installed restricted packages: no go
Installed flash aid: no go either.

Should mention: running on nouveau as the 173 driver won't load.


Out of options.

---

### Post by DexterF on 2012-05-22
Got it fixed... well.. sort of.
I got an old flashplayer v10 from Adobe and copied that into the plugins dir. 
Not really the best solution but until Adobe can be arsed to make their friggin plugin work or html5 finally brings the bloody flash plugin to the death it deserves it will have to do.

I checked again: that GeForce FX5200 is indeed an AGP board on a KT600 chipset. I wouldn't be surprised if that is part of the problem in terms of video drivers.
After all, for reasons beyond me the system won't install the 173 driver and sticks to nouveau.

---

### Post by bumanie on 2012-05-22
Can't help with the nvidia driver, however to get the latest flash going on 12.04 64 bit; go [here]("http://tulsawebresults.com/solution-flash-player-broken-in-firefox-unbutu-12-04-precise-pangolin"). Worked for me, when all else failed!

---

### Post by DexterF on 2012-05-23
Well, that seems to tackle 64bit issues explicitly, doesnt it?

---

### Post by Eddie Wilson on 2012-05-24
Enjoy the temporary fix while you can. Adobe doesn't seem to believe that Linux is worth supporting any more in the future because it's too hard for their developers to deal with. That's just one of the reasons we need a good standard for web video. Not this Flash crap.

---

### Post by flavioso on 2012-08-22
Same problem here guys.

AMD Athlon(tm) XP 2800+
Nvidia FX5200
Ubuntu 12.04

---

### Post by EthanBoyle on 2013-04-06
> **DexterF said:**
> Got it fixed... well.. sort of.
I got an old flashplayer v10 from Adobe and copied that into the plugins dir. 
Not really the best solution but until Adobe can be arsed to make their friggin plugin work or html5 finally brings the bloody flash plugin to the death it deserves it will have to do.

I checked again: that GeForce FX5200 is indeed an AGP board on a KT600 chipset. I wouldn't be surprised if that is part of the problem in terms of video drivers.
After all, for reasons beyond me the system won't install the 173 driver and sticks to nouveau.

This did the trick for me! Thank you! I used (Released 2/28/2011)  [Flash Player 10.2.152.32]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_10.2.152.32_archive.zip") from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html), flash is really smoothe again.

---

### Post by arodet on 2013-04-15
The version [Flash Player 10.2.152.32]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_10.2.152.32_archive.zip") doesn't hold linux 32bits library.
I found a good version on this [wiki]("http://www.fuduntu.org/wiki/index.php/Flash_Player_%28older_32-bit_systems%29").
The version 10.3.183.11 works well with my ubuntu 10.04LTS on AMD 2400+ and GeForce FX5200.
Regards.

---

### Post by kuifje09 on 2013-04-21
I found at another forum and can confirm it is because the latest flashplayers are compiled with sse2 support.
Much of the old but still in use, mostly AMD cpu's, don't have SSE2. Thats is the problem.
Get an old flashplayer, without the need for sse2 and you go.  But beware there may be a security risk, but how big ???

to see if you have sse2 support:    cat /proc/cpuinfo | grep sse2 or without the grep to see all info.

Update, found on another forum, flashplayer ( new/latest ) wil work when you install HAL .
It is also told so at adobe.

---

