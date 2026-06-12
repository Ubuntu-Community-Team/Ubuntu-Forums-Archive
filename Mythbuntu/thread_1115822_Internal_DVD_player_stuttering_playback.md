---
title: "Internal DVD player stuttering playback"
date: 2009-04-04
forum: Mythbuntu
---

### Post by am4c130d on 2009-04-04
Hi,

I am running Ubuntu 8.04.1 AMD64 with MythBuntu 0.21-fixes weekly updates.  Since the base install, build 16838 - which works fine but menu support is lousy, and stability is questionable, DVD playback has suffered from stuttering or jerky playback - basically the DVD appears to pause/skip every few seconds.  This is reproducible, if I roll back to 16838, DVD playback is fine, if I use hardy backports  18207, or any of the Mythbuntu weekly builds, the DVD skips/pauses.  By contrast using the internal player to play .VOBs is fine.

The amount of stuttering is DVD and build related.  The newer the build, the worse the problem.  Some DVDs, Animusic in particular are unwatchable, others skip only on high bandwidth moments i.e. screen pans in detailed scenes etc.  However there are some twists.  If I play the DVD at .9x or 1.1x speed, playback is perfect.  If I rewind/skip, playback is perfect on the scenes already shown, until the point I skipped back, whereupon the jerkiness/stuttering returns.

To address this problem I have tried pure Mythbuntu 8.10 386 and AMD64, the problem is consistent across all three variants.

I have tried with and without deinterlacing (I typically use Bob2x), the issue is consistent.

TV playback is fine - no problems at all.

I have a separate frontend/backend - and the two are linked over GigE network.  My FE HW is Asus M2NPV-VM, with 3800+ x2, 65W CPU.  DVD is a Liteon SATA drive and 1 Gb DRAM.  I am using the onboard nVidia 6150, using S-Video to a standard CRT.  I have tried using DVI to an LCD panel at 1440x900, the only difference was CPU utilization rose from ~20% to ~50% due to the higher resolution, DVD playback was still jerky, and Live TV etc. was fine.  Currently I am using a RT kernel and have RT threads enabled - but of course this is irrelevant or Mythvideo - surprisingly doesn't use real-time threads.

Its not definitively HW related, as Xine playback is perfect, however I'd prefer to use Myth's player - I have inconsistent exit issues with Xine
and I prefer the Myth OSD.

Attached are two logs (using older Mythbuntu weekly build) that may shed some light - one with Bobx2 and one with no deinterlacing. 

Any ideas?  I've been at this on and off for months and am fresh out ideas personally - any help would be appreciated.  

Thanks

Alan

---

### Post by teetniin on 2009-04-04
Hi

 I was having same problem(when using internal player).
What i noticed, problem occures when i enabled media monitor(to automatically launch dvd, usb drive etc.).
Check if you are having this option enabled(it is located under general settings).

---

### Post by am4c130d on 2009-04-04
Thanks, a great idea as that was definitely enabled, due to the WAF. However disabling it didn't help.  I also disabled the auto-start capability in the Music Settings and Video Settings with no improvement.

Thanks for the suggestion.

---

### Post by teetniin on 2009-04-05
Did you restart frontend before trying new settings?

---

### Post by am4c130d on 2009-04-06
Yes. On the Ubuntu 8.04.1 AMD64 install it made little discernible difference.  

However, I also tried it on 32 bit Mythbuntu 8.10 install) same HW, swapped HDD, kept the same system name) - and it fixed that problem.  I did note with Bob2x and with GreedHighMotion2x the occasional stutter happened on Animusic - but these were insignificant.  Other DVDs I tried seemed fine (Anmiusic really exposes these problems).

I'll test Mythbuntu AMD64 8.10 tonight and see how that behaves.

Thanks again for the tip - and for making me retest, after 12+ months with this issue, we're making progress!

---

### Post by utar on 2009-04-06
Do you get the same problem when playing back the DVDs as an iso?

---

### Post by am4c130d on 2009-04-06
No. I ripped Animusic this evening and that played perfectly on MythVideo on Ubuntu Hardy - which has been the worst combination.  It was also played over NFS - just to complete the picture. 

If I was reading this I'd conclude that I had DVD subsytem performance problems, i.e. DMA not enabled, but this is a SATA DVD player...  Also, DVD playback is smooth at 1.1x speeds - so not a case of pure DVD speeds.  Any more ideas - this seems to be on a path indicating some issues getting data off the DVD.

Again, thanks for a good tip.

Thanks

Alan

---

### Post by am4c130d on 2009-04-07
here is the output from hdparm

 sudo hdparm -I /dev/scd0

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       LITE-ON DVDRW LH-20A1L                  
	Serial Number:      
	Firmware Revision:  BL06    
Standards:
	Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
	Supported: CD-ROM ATAPI-2 
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	PACKET command feature set
	   *	DEVICE_RESET command
	   *	Mandatory FLUSH_CACHE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	Device-initiated interface power management
	    	Asynchronous notification (eg. media change)
	   *	Software settings preservation

So it looks like the DVD system is not the issue - and of course Xine plays everything without issue.

My next thoughts are around the data fetching in MythVideo.  When I allowed mythtv to read recordings via NFS, and not via the streaming protocol, I used to get the occassional jerk/stutter - and addressed this by telling Mythtv to always stream from the backend.  I have seen numerous posts on the mythtv forums complaining of poor NFS performance with Mythvideo, and it all appears to stem from the fact that Mythvideo doesn't prefetch much data (nor does Mythtv, Mythtv relies on the streaming protocol - or so it appears).

The logs I posted earlier all have 

 Video is 3.66493 frames behind audio (too slow), dropping frame to catch up.

and 

NVP: Video is 3.74995 frames ahead of audio,doubling video frame interval to slow down.

these statements which are clearly caused by buffering issues - either overclocking or underclocking - though in the vast majority of cases they are video is behind audio.  In both cases I wonder if the reality is not enough data in video buffers, because delays in fetching the video cause the video to lag behind.  Clearly the problem is not endemic to Mythvideo per se, as it is not experienced when using ISO files of the same DVD.  So there is some interdependency with the DVD player, but if each request for data is small, and the DVD access is a little slow (seek time, not throughput), then this could cause buffer starvation - which could show as above.

Make sense?

Thanks

Alan

---

### Post by utar on 2009-04-07
I have problems with playing physical DVDs as well, so it's not just you.

Basically the internal DVD player in Myth is broken.  Although I found that if you fast forward for a few seconds when playing a DVD the DVD drive tends to speed up and this seems to keep Myth happy.

It's clearly nothing to do with the DVD drive on my system since I can play back using vlc etc with no problems.

I would suggest to work round the problem you either rip the DVD to an iso or set myth to use an external program to play DVDs.  Not ideal I know.



Utar

---

### Post by am4c130d on 2009-04-07
Misery loves company - it seems that this is a bug.  I have been using Xine instead of MythVideo - but it seems to be a miss to me given that mythdvd has come on so far in the last few years - but has gone backwards in terms of playback (not reliability, menu support etc.) in the last 12 months.

The problem is that this appears to be HW related.  I have another system that is almost underpowered and it plays DVDs fine with MythDVD/Video.  This is a Pentium 4 2.53 GHz, SIS 952 chipset and Lite-On IDE DVD drive.

What HW do you have?

Mine is as follows

Asus M2NPV-VM
AMD Athlon 64x2 3800+ (65w)
2 x 512byte Corsair memory, configured for 128 access
WD 80 Gb IDE drive
Lite-On DVDRW LH-20A1L SATA DVD
Built in 6150 GPU
Built in GigE
Samsung 16x2 LPT LCD display
Handmade IR port

I am happy to file a bug, based on your common experience it seems appropriate.  I also believe the CD monitoring is related as well, as this may be a system that is not suspended during playback and thus interferes, adding to the underrun in data.

Once filed, I'll post the bug number back to this forum so you can add your tales of woe to the bug as well.

---

### Post by utar on 2009-04-07
I'm not convinced it's anything to do with hardware since other software works fine.

Personally I think it may be the speed limiting that Myth tries to do with the DVD drive that isn't working right.  It's just a pity that you can't disable this option in Myth.

---

### Post by teetniin on 2009-04-08
I have similar HW:
Asus M2NPV-VM
AMD Athlon 64x2 4859e+ (45w)
2x1G 800+ Adata memory
32G Adata SSD drive(sata interface)
Samsung DVD-RW drive if i remember correctly(also sata interface)
Built in 6150 GPU
Built in GigE
Antec Fusion with VFD display
Handmade IR COM port + poweron IR.

I had this topic on mythtv mailinglist, there someone said it is problem of old ffmpeg, with next resync this problem will be gone.
To me it sounds strange, because without media monitor(which sucks big time) I can watch most of my DVD.s with internal player(slight stuttering sometimes).
Friend of mine uses 0.22 and it doesn't have this problem.
I really hope 0.22 comes along soon and we all can use better and usable media center system :)

---

### Post by am4c130d on 2009-04-08
Interesting Teetniin, that we share the same motherboard, but not DVD drive, and have the same problem.

My thoughts about it being HW related are not a failing or shortcoming in the HW, but more an inter-dependency between MythVideo and specific HW.  I don't use MPLayer, but seemingly you can tweak the read buffer size to reduce buffer underruns, bascially fine tune the SW to the HW - that is the sort of inter-dependency I meant.  As nothing in Myth is tweakable in this area - who knows - and as other SW works fine - it's definitely Myth that needs tweaking, not the HW.  A telling case for this is the poor performance many people experience with NFS - NFS is one of the fastest file sharing systems out there, but there is probably some latency at the start of each read that make the small reads that Myth does ineffective - by tweaking the block read size you can address this.

There was some thread I read ages ago where it was pointed out that Myth bypasses the Linux write cache to prevent issues in old HW.  By removing this code, one guy was able to keep entire shows in memory on his backend server, thus speeding up everything and not caning his RAID system.  I wonder if this sort of compromise is something thats negatively impacting people with higher end systems.

---

### Post by am4c130d on 2009-04-13
Bug 6456 added to MythTV trac.

---

### Post by am4c130d on 2009-12-06
Allegedly solved

[http://svn.mythtv.org/trac/ticket/7605](http://svn.mythtv.org/trac/ticket/7605)

I have not verified, others have.

---

### Post by srmcatee on 2010-01-25
I am a little new to patches.

How does one install this patch?

---

### Post by pilesofspam on 2010-01-25
Check out:
[http://ubuntuforums.org/showthread.php?t=1354378]("http://ubuntuforums.org/showthread.php?t=1354378")

I linked the above because it is specific to mythbuntu.  This involves installing the mythtv source, applying the patch, compiling the source and then installing what you've built.  You'll also have to add an additional repository.  It's a great learning experience and I recommend it highly if you have:

1.  High wife patience
2.  High tolerance for finding out what you missed or broke
3.  Time

Simply put:  if you've done it a few times before it'll go smoothly most of the time, and pretty quickly except for the compile time,  If this is your first time, remember everything is hard before it's easy, but it is a worthwhile skill to develop.

Me?  I've got an otherwise perfectly working system,  plenty of #2, none of #1, and very little of #3.  I've also got an external DVD player connected to the receiver so that is my non-ideal solution until we have a binary mythbuntu patch to make the fix.

---

### Post by srmcatee on 2010-01-26
> **pilesofspam said:**
> Check out:


1.  High wife patience


I am minus in #1.  Looks like I'm waiting for the patch.

thanks anyway.

---

### Post by srmcatee on 2010-01-26
What is the best way for me to tag this fix so I am alerted when it is rolled into the release?

Sorry for the really noob question

---

### Post by pilesofspam on 2010-01-27
Turns out that's a great question.  I just spent 10 minutes looking and I don't have a good answer.

Anybody else know how we can be notified when the fix for bug 7605 gets ported into a mythbuntu mythtv binary?

Without a good answer, I'll watch for a mythfrontend to show up as a recommended update.  I'd assume it'll be in whatever frontend release shows up next.

---

