---
title: "advice on older hardware"
date: 2009-04-29
forum: Mythbuntu
---

### Post by duffrecords on 2009-04-29
I currently have a Mythbuntu backend/frontend set up on the following box:

AMD Athlon XP 2400+
PC Chips M848A (w/ 8x AGP slot)
NVIDIA GeForce 5500 FX (128 MB)
768 MB of RAM
Hauppauge HVR-1600

As a backend it's fine.  I can record HDTV with it and watch it live on the frontend in the other room (which has an AMD Phenom 9850 and NVIDIA GeForce 9600 GSO).  But as a frontend it struggles.  Sometimes I can watch pre-recorded episodes of The Simpsons because it's SD and, being a cartoon, has a lot of static imagery.

Anyway, I just got my hands on a free used server at work that has:
(2) Pentium III 1.0 GHz
Abit VP6 (w/ 4x AGP slot)
1 GB of RAM

So I was thinking of using the Pentium box as the backend and setting up the AMD box as a frontend only.  Does anyone think the AMD box will be able to hold its own as a lightweight frontend once it's been relieved of its duty as a backend?  Would it be worthwhile to swap the Athlon XP 2400+ for an XP 3200+ or a Sempron 3300+ (Socket A)?  Or upgrade the RAM?  I suppose I could save up and just buy a new CPU/board/RAM/GPU but I'm trying to save money and utilize the hardware I already have.

---

### Post by klc5555 on 2009-04-30
> **duffrecords said:**
> I currently have a Mythbuntu backend/frontend set up on the following box:

AMD Athlon XP 2400+
PC Chips M848A (w/ 8x AGP slot)
NVIDIA GeForce 5500 FX (128 MB)
768 MB of RAM
Hauppauge HVR-1600

As a backend it's fine.  I can record HDTV with it and watch it live on the frontend in the other room (which has an AMD Phenom 9850 and NVIDIA GeForce 9600 GSO).  But as a frontend it struggles.  Sometimes I can watch pre-recorded episodes of The Simpsons because it's SD and, being a cartoon, has a lot of static imagery.

Anyway, I just got my hands on a free used server at work that has:
(2) Pentium III 1.0 GHz
Abit VP6 (w/ 4x AGP slot)
1 GB of RAM

So I was thinking of using the Pentium box as the backend and setting up the AMD box as a frontend only.  Does anyone think the AMD box will be able to hold its own as a lightweight frontend once it's been relieved of its duty as a backend?  Would it be worthwhile to swap the Athlon XP 2400+ for an XP 3200+ or a Sempron 3300+ (Socket A)?  Or upgrade the RAM?  I suppose I could save up and just buy a new CPU/board/RAM/GPU but I'm trying to save money and utilize the hardware I already have.

Frontend work (especially HD) is CPU intensive. The faster the CPU, therefore, the better. The more you can reduce read-writes to the disk the better; therefore RAM at, say, the 1.5 Gig range would be ideal. Is XvMC configured and working? Are you using a lower-overhead playback profile, like "Slim" or similar? 

On a properly tweaked machine with XvMC running right, I believe I remember reading of those who can get acceptable HD with an XP 2400+ But your current RAM would seem to me to be a bottleneck, despite mythtv.org's statement that 256M of RAM should yield "adequate" performance with one encoder.

---

### Post by ian dobson on 2009-04-30
Hi,

For a frontend I recommend 512Mb ram (Mine uses about 350-400 under normal use). If you can get VDPAU backports up and running on a NVIDIA graphic card then a AMD 2400 should be enough (My frontend is a Core2Duo running at 1200MHz and watching HD 1920x1080 the cpu sits at about 15% load).

I don't know if there any AGP graphic cards that support VDPAU.

Regards
Ian Dobson

---

### Post by novellahub on 2009-04-30
> **ian dobson said:**
> Hi,

For a frontend I recommend 512Mb ram (Mine uses about 350-400 under normal use). If you can get VDPAU backports up and running on a NVIDIA graphic card then a AMD 2400 should be enough (My frontend is a Core2Duo running at 1200MHz and watching HD 1920x1080 the cpu sits at about 15% load).

I don't know if there any AGP graphic cards that support VDPAU.

Regards
Ian Dobson

There is a Sparkle Brand Nvidia 8400 GS PCI card that works well in older systems supporting VDPAU.  See this thread on the Knoppmyth Forums:

[http://knoppmyth.net/phpBB2/viewtopic.php?t=19615](http://knoppmyth.net/phpBB2/viewtopic.php?t=19615)

---

### Post by duffrecords on 2009-04-30
Yes, XvMC is enabled.  It says so in dmesg.  I'm using CPU-- but I don't see any improvement.  But I just bought one of those GeForce 8400 GS cards and some more RAM on TigerDirect, so hopefully that should make a difference.  I think the current RAM that's in there might only be PC2700 too, so I'm upgrading to 2GB of PC3200, as that's the most this board can handle.  Thanks for all of your help.  I'll post the results once I get the parts.

---

### Post by jbman on 2009-04-30
I was running a similar system to you about 6 months ago. HD playback was fine with XVMC with some tweaks like OSD fade turned off.

With some fiddling it will work, but as said if you can get a VDPAU compt card you will be laughing.

---

### Post by duffrecords on 2009-05-10
I installed the new RAM but if there's any improvement, it's so marginal I'm not sure if I'm imagining it or not.  I was going to try installing the Sparkle video card next, but I got a bad superblock in /boot first.  I'll have to wait until I get home to fix that.

---

### Post by duffrecords on 2009-05-19
Wow, what an ordeal this has been.  Having no success with the bad superblock, I decided this was as good a time as any to back up and wipe everything and start over (which I've been meaning to do with both my desktops).  So now I have a powerful quad-core Debian machine serving as a backend and my digital audio workstation, and my slightly outdated Athlon XP running a Mythbuntu frontend only.  I installed the Sparkle card and set up a VDPAU profile, which brought the CPU load from 99% down to 10-15%.  I found that HDTV plays better with the display set to its highest resolution.  I disabled the "Composite" extension in xorg.conf and I'm using Bob deinterlacing.  At this point, HDTV is *almost* watchable, but not quite.

I can think of three possible improvements but they each require investing some degree of time or money, so I'd like to determine what the biggest bottleneck is first.  I could:
[LIST]
[*]Install an amplifier at the antenna (S/N is currently about 2.3 dB)
[*]Replace xfce with fluxbox
[*]Tweak the NFS block size to minimize transfer time from backend to frontend
[/LIST]

---

### Post by duffrecords on 2009-05-20
I was near a Radio Shack this afternoon so I picked up an amplifier (part #15-2507).  It claims to boost the signal by up to 30 dB but MythTV is still reporting a 2.3 dB S/N ratio.  Then, just for the hell of it, I removed my indoor powered DTV antenna and replaced it with my old passive rabbit ears.  The ears, combined with the new amp and the amp from the powered antenna, are enough to get me a lock on a fair amount of channels.  I'm now watching HDTV with no skips on an old Athlon XP 2400+.  I'm curious to see what I'd pick up if I were allowed to stick a Channel Master or Winegard up on the roof.  But this is good enough for now.

---

