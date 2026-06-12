---
title: "Playback issues while recording"
date: 2009-07-13
forum: Mythbuntu
---

### Post by chip33az on 2009-07-13
Hello,

I need some help trying to troubleshoot a playback issue that I am having.

I setup Mythbuntu 9.04 on an Asus M3A76-CM with an AMD 4850e and a SATA 1.5Gbps drive (OS on ext3, recordings on XFS).  For video I'm using a 9500GT and the JYA (I think that is correct) updates to allow for VDPAU.  I'm using a PVR 150 as the recording device (only 1 installed in system).

Watching live TV/recordings is flawless.  Playing videos using mplayer is flawless as well (couldn't seem to get the internal working properly with VIDEO_TS folders - not the question).

My problem is when I am recording a show and watching a recording, the video playback stutters, both video and audio.  Looking at top, the CPU utilization is around 1 or 2% while recording so I don't think it is a CPU issue.  After the recording, the CPU spikes to around 50% for commflagging, but the issue occurs during recording.

My question - Where to start trying to troubleshoot this?  I would think the hardware would be good enough to handle what I'm trying to do.

Any suggestions would be appreciated.

---

### Post by klc5555 on 2009-07-13
> **chip33az said:**
> Hello,

I need some help trying to troubleshoot a playback issue that I am having.

I setup Mythbuntu 9.04 on an Asus M3A76-CM with an AMD 4850e and a SATA 1.5Gbps drive (OS on ext3, recordings on XFS).  For video I'm using a 9500GT and the JYA (I think that is correct) updates to allow for VDPAU.  I'm using a PVR 150 as the recording device (only 1 installed in system).

Watching live TV/recordings is flawless.  Playing videos using mplayer is flawless as well (couldn't seem to get the internal working properly with VIDEO_TS folders - not the question).

My problem is when I am recording a show and watching a recording, the video playback stutters, both video and audio.  Looking at top, the CPU utilization is around 1 or 2% while recording so I don't think it is a CPU issue.  After the recording, the CPU spikes to around 50% for commflagging, but the issue occurs during recording.

My question - Where to start trying to troubleshoot this?  I would think the hardware would be good enough to handle what I'm trying to do.

Any suggestions would be appreciated.

Your motherboard, CPU, and video card ought to be overkill for the little you're doing with it. Must be a bottleneck, just not the CPU.

Is memory in, say, the 1.5 Gig range? If (a lot) less, that might be the problem.

You can watch livetv and watch-while-recording; but watching a different recording has you accessing three different parts of the drive simultaneously. Do you have your SATA drive set up for full-speed access? I usually prefer to have the recordings and OS (plus swap partition) on separate drives, but with something as light on resources as a pvr 150 (which I assume is set up as a MPEG-2 card and not a V4L analog) this shouldn't make any difference on your system.

You must be using the proprietary NVIDIA drivers; do different Playback profiles (e.g. "Slim") make a difference?

You might want to check your mythfrontend log to see what is different when you watch-while-record as opposed to watching something else while a program records. Assuming you find a lot of the dreaded "prebuffering pause" messages in the log, there is a prebuffering pause troubleshooting page on the wiki here: [http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause)

---

### Post by chip33az on 2009-07-13
Thanks for the reply.

I have 4GB on the machine.  Also, I'm running the 64-bit version (forgot to mention that).

Yes, the PVR-150 is set up as a MPEG2 card.  It is actually an Avermedia 1500, but it is configured as an MPEG2 - I might change to an HVR1600.  I thought it might be the card eating up CPU cycles, but when I ran top the CPU was running around 1 or 2%.

I don't know what you mean by full speed?  The drive is a 1.5Gbps SATA.  I don't know of any tweaking to do with SATA.  The OS/swap/recordings are all on the same drive, separate partitions.  

There are a lot of Prebuffering pausing in the front end log.  I read somewhere (I believe the JYA site) state the 9500GT should use Advanced x2 for best performance, which is how I have it set up for.

---

### Post by klc5555 on 2009-07-13
> **chip33az said:**
> Thanks for the reply.

I have 4GB on the machine.  Also, I'm running the 64-bit version (forgot to mention that).

Yes, the PVR-150 is set up as a MPEG2 card.  It is actually an Avermedia 1500, but it is configured as an MPEG2 - I might change to an HVR1600.  I thought it might be the card eating up CPU cycles, but when I ran top the CPU was running around 1 or 2%.

I don't know what you mean by full speed?  The drive is a 1.5Gbps SATA.  I don't know of any tweaking to do with SATA.  The OS/swap/recordings are all on the same drive, separate partitions.  

There are a lot of Prebuffering pausing in the front end log.  I read somewhere (I believe the JYA site) state the 9500GT should use Advanced x2 for best performance, which is how I have it set up for.

Some SATA drives are factory jumpered/configured to run at close to IDE speed. This factory setting needs to be removed to get the 1.5Gbps transfer rate. Shouldn't really matter for the 2.2 Gigs/hr. that analog pumps through. Begins to matter seriously when you have the 6+ Gigs/hr. of HD.

The logical culprits for bottlenecks are your playback profile (frontend/setup/tv), your video card configuration, and your alsa/audio configuration. First step is to try the "Slim" playback profile, and see if it makes a difference. 

For a single analog tuner, and a MPEG-2 hardware decoder at that, you don't need VDPAU to watch and record simultaneously. You shouldn't even need the proprietary NVIDIA driver: this you should be able to do perfectly with the open-source "nv" driver. If you're using the Slim playback profile, without effect, you might explore backing your NVIDIA card down from its supposed "optimal" configuration to something much more plain vanilla, just as a test. Including even trying the open-source "nv" driver.

If it doesn't seem to be the playback configuration or video card configuration at all, then the next stop is the sound configuration --for this use the wiki entry referenced before.

In theory this could also be a 1500 configured without the firmware as a frame-grabber rather than as a hardware decoder, but you'd be aware of having configured the card this way. The 1500 wiki entry is here: [http://www.mythtv.org/wiki/AVerMedia_M150-D](http://www.mythtv.org/wiki/AVerMedia_M150-D)

I also see from this thread here: [http://ubuntuforums.org/showthread.php?t=992746](http://ubuntuforums.org/showthread.php?t=992746) one user whose problem in this regard was fixed by changing his recording directory from xfs to ext3, though its a mystery to me how this could be effective.

---

### Post by chip33az on 2009-07-13
Thanks!  

I hope it isn't along this line, although it would be fairly easy for me to convert it.

[http://ubuntuforums.org/showthread.php?t=992746](http://ubuntuforums.org/showthread.php?t=992746)

The summary is someone had a similar problem like mine and switching from XFS to EXT3 solved it.  I would hate to try it, but the WAF isn't doing too good right now :(

---

### Post by chip33az on 2009-07-20
Well, late last week, I backed up all of my recordings and then reformatted the drive to ext3.  So far I have had no issues with the recordings and playback at the same time.

I also think the playback of the recordings start faster than while under XFS.  

I don't know why, but it seems to have worked for me.

---

