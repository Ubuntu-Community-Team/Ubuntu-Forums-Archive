---
title: "Patch available for mythfrontend deadlock"
date: 2008-01-13
forum: Mythbuntu
---

### Post by faginbagin on 2008-01-13
I am attaching a patch that fixes a deadlock in mythfrontend. In my case, the deadlock occured when I was watching imported videos that were recorded on a Panasonic DVD recorder. I would fast forward over commecials, then back up when I went too far. That's when it tended to deadlock. The only way to recover was to kill mythfronend and restart it.

I think the deadlock is related to the fact that I have the display of NTSC closed captions enabled by default. Looking at the code, I suspect the deadlock might occur when playing imported video with embedded PAL teletext, too. The code I changed is executed when you have an nvidia GPU, the propritary nvidia driver, and have set "Preferred MPEG2 Decoder" to "Standard XvMC" in mythfrontend's TV Settings -> Playback.

Details about my mythtv setup:
ECS RS482-M754 motherboard
AMD Sempron 3100+ 32 bit CPU
1GB RAM
Hauppauge WinTV-PVR-150 model 1045 with IR blaster & receiver
Biostar graphics card with an nVidia Geforce 7300 LE GPU
Two HDDs, 80GB & 500GB
500W PSU
IDE CD burner
SATA DVD-RAM burner
Ubuntu gutsy 7.10
mythbuntu control centre 0.10-0ubuntu1.1

I had already installed ubuntu when I discovered mythbuntu, so I followed the instructions here:
[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)
to complete my setup, which took care of the remote control configuration, proprietary nvidia driver, etc.

To use this patch, you first need to download and build the source package for mythtv using apt-get and dpkg-buildpackage. That way, you'll have the souce code and build environment that produces the same binaries provided by the mythtv packages from mythbuntu. There are many sites that describe how to build source packages, so I won't repeat it here.

Then apply this patch, configure (e.g. to specify an alternate install directory, a good idea), compile and install. If you used configure to specify a different install directory, you'll need to build and install the mythplugins source package, too.

If you're comfortable building source packages, using gdb, and want to confirm that your deadlock might be fixed by my patch, please post a reply and I'll describe what to look for in your stack backtraces.

If this patch solves a problem for you, please post a reply.

Hope it helps someone other than just me.

---

### Post by superm1 on 2008-01-13
> **faginbagin said:**
> I am attaching a patch that fixes a deadlock in mythfrontend. In my case, the deadlock occured when I was watching imported videos that were recorded on a Panasonic DVD recorder. I would fast forward over commecials, then back up when I went too far. That's when it tended to deadlock. The only way to recover was to kill mythfronend and restart it.

I think the deadlock is related to the fact that I have the display of NTSC closed captions enabled by default. Looking at the code, I suspect the deadlock might occur when playing imported video with embedded PAL teletext, too.

To use this patch, you first need to download and build the source package for mythtv using apt-get and dpkg-buildpackage. That way, you'll have the souce code and build environment that produces the same binaries provided by the mythtv packages from mythbuntu. There are many sites that describe how to build source packages, so I won't repeat it here.

Then apply this patch, configure (e.g. to specify an alternate install directory, a good idea), compile and install. If you used configure to specify a different install directory, you'll need to build and install the mythplugins source package, too.

If you're comfortable building source packages, using gdb, and want to confirm that your deadlock might be fixed by my patch, please post a reply and I'll describe what to look for in your stack backtraces.

If this patch solves a problem for you, please post a reply.

Hope it helps someone other than just me.
Have you already submitted this upstream?
We'll be glad to add this changeset to our weekly builds should upstream be willing to accept it.

---

### Post by faginbagin on 2008-01-13
Well, I attached the patch to an existing ticket that describes a similar problem, #4341. But since I haven't verified the deadlock exists in trunk and that this patch fixes it, I doubt they'll accept it. So, I thought I'd at least make it available to mythbuntu users, since it was the mythbuntu version of 0.20.2 that I used.

I did look at the trunk source, and I suspect it might be vulnerable to the same deadlock, because the code I touched hasn't changed from 0.20.2 to trunk.

I might try to set up a trunk environment. But it will be tricky since I don't have another machine I could use. So I'd like to see if I can at least find users of 0.20.2 who are suffering from this deadlock and want to try my patch. Perhaps that will give you the confidence to add it to your weekly builds. What version are you building weekly?

---

### Post by Nimda1000 on 2008-01-13
I have the same symptoms, hang/lockup during rewind, fast forward is  okay, But.  I don't have the closed captioning on.

I have as single primary Front/Backend unit attached to my TV configured with:

Mythbuntu 7.10 (Configured using the PVR-350 How-To and The X on the TV-Out How to found on this site, (PS, Thanks Superm1 :) )

Intel C2D Dual-Core 1.8Ghz Processor
Decent Asus Server Board SATA/PCIex etc. (3 PCI)
1 Gig DDR2 PC 5400 Ram
80GB SATA HDD - Just to start with  ;)
No Video Card at all, Onboard Video Disabled
Using Onboard standard HI-DEF Audio
Single Hauppauge PVR-350 MPEG2 Encoder/Decoder/TV-tuner/TV-Out
- I use only the PVR's TV-Out connected to my TV, it is excellent!
- Using the PVR's Cable TV Tuner as TV Source

Is there something else that is known to cause this with the funky PVR-350 Setup I am using.  (buffer settings?)

I am more than willing to provide input on this issue, it is the only issue that I am having since the install (which is really great considering what we are doing with the 350's.)

should I try the same fix above or wait and see?

Nim
Lemme know, guinea pig #1 i iz here.

---

### Post by superm1 on 2008-01-13
We build both fixes and trunk weekly for those that are interested.

You might consider popping in #mythtv to have someone look at your patch if it  doesn't get any attention on the bug tracker.

However, as you said if some other folks give it a shot without any breakage, i'll be glad to add it to the weekly builds.

---

### Post by faginbagin on 2008-01-13
Hi Nim,

After seeing your post, I realized I had neglected to provide detals about my setup. I just edited my original post to fix that.

There are a couple of possibly important differences from your setup. I've got a PVR-150 and a nVidia GeForce 7300 LE GPU. So I'm using the nvidia proprietary driver and I've set set "Preferred MPEG2 Decoder" to "Standard XvMC" in mythfrontend's TV Settings -> Playback.

I'm not familiar with the PVR-350. Does it's driver support XvMC? If not, then my patch probably won't help you, because I believe the code I changed is only executed when XvMC is enabled.

However, if you know how to use gdb to examine a core file, I can tell you how to generate a core file and what to look for. Who knows, maybe you are executing the same bit of code my patch fixes?

---

### Post by faginbagin on 2008-01-13
Hi superm1,

> **superm1 said:**
> We build both fixes and trunk weekly for those that are interested.

You might consider popping in #mythtv to have someone look at your patch if it  doesn't get any attention on the bug tracker.

However, as you said if some other folks give it a shot without any breakage, i'll be glad to add it to the weekly builds.

Thanks for the info. I assume fixes means 0.20.2 plus fixes. I did get an almost immediate response from a mythtv developer when I first added a comment to the ticket, but before I attached the patch. And the gist was as I mentioned, they're really only interested if the deadlock can be reproduced in trunk and if the patch fixes it. As a developer I totally understand that position.

I'll give it a day, and see if anyone checks the patch I attached to the ticket. If not, then I'll pop into #mythtv as you suggest.

---

### Post by jwbrown77 on 2008-01-25
I'm also having this issue and hope that you've found a way for them to accept your patches as it's quite annoying.

Hopefully it will work correctly in 0.21.

---

