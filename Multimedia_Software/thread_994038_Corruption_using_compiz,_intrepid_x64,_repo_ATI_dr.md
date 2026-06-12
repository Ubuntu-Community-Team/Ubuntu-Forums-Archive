---
title: "Corruption using compiz, intrepid x64, repo ATI drivers"
date: 2008-11-26
forum: Multimedia Software
---

### Post by niallporter on 2008-11-26
Hi all,

I installed Intrepid x64 from the official release ISO.  I used the Hardware Drivers tool in the System/Administration menu to install the ATI drivers from the official Ubuntu repositories.  When I switch on desktop effects I get bad graphical corruption on the screen.

Under Hardy this worked fine, the ATI drivers installed without problem (they don't give any error messages on Intrepid either) but the desktop effects worked mostly OK.  Anyone seen this and got a fix?  Gfx card is a Radeon X800XL, AGP format.

Thanks in advance,
Niall

---

### Post by judasg0at on 2008-11-26
You may want to check out this [thread ]("http://ubuntuforums.org/showthread.php?t=958400")

It covers a bug that may be the very same as the one that you are describing. Running programs as root (sudo) seems to fix the problem. It seems to be some sort of permissions issue, though it is not clear where the problem lies. I got around the problem by reinstalling 8.04 Hardy on a new partition. If that also works for you it may point to some permissions issue with Intrepid and ATI drivers.

---

