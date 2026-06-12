---
title: "32bit or 64bit"
date: 2009-12-15
forum: Mythbuntu
---

### Post by myth_cougar on 2009-12-15
I currently have a mythtv machine running Mythdora, but it has various issues and I have been quite impressed with Ubuntu 9.10 and intend to reinstall with Mythbuntu.  My machine is based on the following:

AMD Athlon 64 X2 4850e
Gigabyte GA-MA78GM-S2H 780G (onboard radeon 3200, but poor drivers)
2 Gb of ram and 1Tb of storage.
XFX GEFORCE GT220 1GB (just bought and awaiting delivery)

Is it worth going down the 64bit route or should I stick to to the 32bit version.  Hopefully most of the video decoding will be offloaded to the graphic card with VDPAU so not sure what to do.  Is there any problems with things like Flash on 64bit?

---

### Post by yonkiman on 2009-12-15
> **myth_cougar said:**
> Is it worth going down the 64bit route or should I stick to to the 32bit version. 

I've been using 64 bits for the last 2 years with only one issue (Flash).  There were slightly complex workarounds even 2 years ago, but now there's a full-fledged 64 bit Flash library, so even that's a non-issue now.

I can't tell you if anything's running faster/smoother than it would be if I'd been running 32 bit (I imagine it is, but I haven't done any benchmarks), but I can tell you it's not a handicap anymore. 

So I'd recommend you go 64...

-Fred

---

### Post by User3k on 2009-12-15
> **yonkiman said:**
> i've been using 64 bits for the last 2 years with only one issue (flash).  There were slightly complex workarounds even 2 years ago, but now there's a full-fledged 64 bit flash library, so even that's a non-issue now.

I can't tell you if anything's running faster/smoother than it would be if i'd been running 32 bit (i imagine it is, but i haven't done any benchmarks), but i can tell you it's not a handicap anymore. 

So i'd recommend you go 64...

-fred

+1

---

### Post by camporter1 on 2009-12-15
This won't hold true for everyone or every situation, but I find 32-bit installs to be more stable than 64-bit installs. I'm currently running a 64-bit install, but I don't see much of a performance improvement when running 64-bit.

I'm not sure if it's just because more testing happens with 32-bit or what, but I generally seem to be less annoyed with those installs, and they are what I recommend for people who are new to Linux.

---

### Post by NightStorm on 2009-12-16
Is there any advantage to going 64 bit if you are never going to have more than 4G of RAM?  In such a case it would seem to me that 32 bit would be a better choice for reasons of going with the tried-n-true.  Also there are some software suites where 64 bit is problematic (have not looked in a while, but boxee was one such last time I played with it).

    - Bruce

---

### Post by danbodoh on 2009-12-16
64bit vs 32 bit is mainly about how much memory can be addressed by a single process.  32 bit can address 4 GB of space.

There's no advantage for 64-bit if you don't have the memory that supports it, and because the mythtv processes aren't that memory-intensive.

In fact, 64-bit processes take a larger memory footprint than 32-bit processes, because each pointer is twice as large.  So 64 bit could actually make performance worse.

Dan

---

### Post by pootle1 on 2009-12-16
I've just finished building a new fromt end - I tried 64bit, but adobe air (at least) is still a PITA on 64 bit, so I rebuilt with 32 bit, and all is working happily.

btw I'm using a GT220 also - nice card with low power consumption, but supports HD well with VDPAU - although doesn't really cope with all the extras - I had to back off from more intensive de-interlacing to avoid it being a bit jerky.

ubuntu 9.10, myth 0.22 from the mythbuntu repo, and nvidia drivers 190.xx (defined in the mythbuntu repo, but you have to pull them in with synaptics)

---

### Post by brplut40 on 2009-12-16
I built almost the exact same machine, except a very slightly different motherboard. I cannot comment much on the 32 bit vs. 64 bit, but for the short time I have been running on this setup, the 64 bit version is doing just fine. I will warn you that you will not be able to get audio off HDMI out of that video card for a while. I guess nvidia still has to right it into the driver, so it won't be till at least 200 for audio support over hdmi. VDPAU should work just fine with the 190 and up drivers though. 

Don't know what speed RAM you got, but the thing I found out that sucked was the cpu doesn't handle RAM above 800mz very well. I got 1066mz RAM, but you have to do some tweaking to get it to run stable at that speed.

---

### Post by baddog144 on 2009-12-16
Unless you're planning to upgrade RAM soon, I'd say 32-bit is probably better supported, driver-wise etc. There's probably not much difference these days, though. I hear Flash has some issues with 64-bit still though :/

---

### Post by David Grigor on 2009-12-17
> **pootle1 said:**
> btw I'm using a GT220 also - nice card with low power consumption, but supports HD well with VDPAU - although doesn't really cope with all the extras - I had to back off from more intensive de-interlacing to avoid it being a bit jerky.


for me I had a few issues tearing issues with playback on a gt220on the highest de-interlacing. Since adding the following to the /etc/X11/xorg.conf it has worked flawlessly for about two weeks now.  

Section "Extensions"
Option "Composite" "Disable"
EndSection 

So if you haven't done so. Give it a try.

---

### Post by David Grigor on 2009-12-17
> **pootle1 said:**
> btw I'm using a GT220 also - nice card with low power consumption, but supports HD well with VDPAU - although doesn't really cope with all the extras - I had to back off from more intensive de-interlacing to avoid it being a bit jerky.


for me I had a few minor tearing issues with playback on a gt220on the highest de-interlacing ( I'm on 64bit though ). Since adding the following to the /etc/X11/xorg.conf it has worked flawlessly for about two weeks now.  

Section "Extensions"
Option "Composite" "Disable"
EndSection 

So if you haven't done so. Give it a try.

---

### Post by myth_cougar on 2009-12-17
Thanks very much to all who have commented.  Lots of good advice and opinion seems split between the two.

I think I will install the 32 bit version.  I already have the iso for that.  I don't believe there will be much of a performance gain from 64 bit particularly since I only have 2G of ram (800Mhz by the way) and I can hopefully avoid any issues, perceived or real, with 64bit.  I do actually run 64bit OpenSuSE on my main desktop, it has 6Gb so it was a no brainer, and I haven't really come across any incompatibilities with software.

I'm busy copying everything off my current myth box so I can repartition the drives and prepare for reinstalling.  Still waiting for my 220 to arrive, hopefully not to long.  I have seen the comment about disabling compositing to improve performance so I will make sure I do that.

Once again thank you all for your help.

Regards

Steve

---

