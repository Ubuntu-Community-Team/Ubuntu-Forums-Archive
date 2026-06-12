---
title: "How to backup TV-movies from a HD-DVD recorder to HD of PC"
date: 2013-03-23
forum: Multimedia Software
---

### Post by Jacques van Gorp on 2013-03-23
How to backup a HD-DVD recorder for TV movies.
 
Yesterday I took the hard drive (HD) out of this recorder (MD81287) and connected this HD
to my desktop PC (P4P800 with Ubuntu 04.12, with help of an USB to IDE adapter).
On the screen appeared the name LITEONFAT and in the / media directory: 
ST3160002 2ACE.
<ls-l> indicated three empty folders, named: Temp, Audio, Picture and Video also with some empty folders.
However folder "LiveTimeShift.vob" is not empty and contains some sort of information!
The files are named "Content01,02,03” each with about 2 GB of unreadable bytes, that means the command <cat> delivers unreadable text.
 
Finally, folder HHD_VIDEO contains 90 files (MV_00001 t / m 90) with content
including the files MV_RM.BUP; MV_RM.IFO, RM 00.BUP; RM_00.IF and "Title_VOB".

My first question is:
1. what are these folders and files?
2. where is the recorded video and audio information?
3. how is this "useful information” fit to be seen with any media player?
4. which files constitute or support the control for (to manage) the recorder?
5. important question is how to backup the "useful" information to the HD of the PC?

Gparted did see 149.05 GiB (160GB Seagate HD), but as "unallocated" with a red exclamation point next to it, ie there is something wrong, but what?
Perhaps the partitioning tool Gparted did not recognize the type of the "file system", which may be FAT or FAT16?

Rpm. The HD-DVD recorder comprises a DVD burner (as the name indicates).
This means that all separate TV recordings may burned to about 50 or more DVD’s.
However, that is a big job resulting in a bunch of separate disks.

---

### Post by SeijiSensei on 2013-03-23
DVRs use proprietary formatting methods to thwart exactly what you are trying to do.  Do you think the movie studios would make it that easy for you to build an archive of their works?

---

### Post by TheFu on 2013-03-23
> **SeijiSensei said:**
> DVRs use proprietary formatting methods to thwart exactly what you are trying to do.  Do you think the movie studios would make it that easy for you to build an archive of their works?

DRM [https://en.wikipedia.org/wiki/Digital_rights_management](https://en.wikipedia.org/wiki/Digital_rights_management) is a bitch, especially when it gets in the way of people enjoying content they have a legal right to enjoy.

I am not an HD-DVD user or a Blu-Ray user for these reasons.  Before I purchase any content, I see if it has DRM, then I check to see if Linux has "solved" the DRM issue or not.  As an example, I own a TiVo Series 2 DVR.  Initially content from it was locked, but some nice person created a tool to remove the MAC (not the same as a NIC MAC) from the mpeg2 stream.  TiVo even created a way to pull recordings from the TiVo machine to windows or mac and someone figured out how to do it with Linux too.  It was slow, but it worked.  Eventually, I tired of the 480x480 resolution and when my government screwed all of us by allowing cable companies to drop analog signals, the TiVo became worthless - along with all the "Cable Ready" tuners in TVs and VCRs.

I can't remember when, but the local cable company started encrypting more and more QAM channels, which made my PC-based TV recording box less and less useful. As they encrypted more, I dropped the TV plan. Eventually, we were getting fewer channels over cable than OTA, so dropping CableTV completely was the answer.  I spent about $100 on making and buying OTA tuners.  The $20 home built one works better than the $50 monster for my area. I needed some VHF-Med channels picked up.

Anyway - DRM sucks.  There was a time when commercial HD-DVDs could be turned in for Blu-Ray discs - don't know if that still works. There was also a few different MS-Windows programs that could read/rip that format.  Initially, those software makers were sued, but I think nobody cares anymore.

Another option is to use the "analog hole" - that is where you playback the content using the DRM-locked device, but have a TV-tuner or hidef video and 5.1 audio recorder like the Hauppauge HD-DVR to record it.  A few other makers handle this too.  Most use component cables. The devices have gotten cheaper ... just $150 or so now.  If you can stand a lower quality video and stereo audio, using almost any $30-$50 mpeg2 recorder from any of 20 different makers can work too.  

Whatever you do, **be certain to look for a complete Linux software stack before you purchase if that it important to you.**

Good luck.

---

### Post by Jacques van Gorp on 2013-03-24
I wonder about the difference between the old "analogic" HD-DVD recorder and the new one the "digital" HD recorder on which only a HDD, without the DVDevice.
With that Device I will be able to copy as many DVDisks as I prefer (in the bad way to sell).
Consequently I wonder the DRM is appliedin both versions of a "movie store"?
However, the remark of SeijiSensei delivers perhaps the reason that the Partition Manager PM) "GParted" did not detect the type of filesystem?
Old to old: I will try an old PM: "Partition Magic" or some one from Acronis.

---

### Post by SeijiSensei on 2013-03-26
Some DVRs have an eSATA port that you can use to copy stuff to an external drive.  I suggest browsing at [http://www.avsforum.com/](http://www.avsforum.com/) and see what information is there about your specific device.  But, as I said, the reason normal partitioning tools cannot handle the drive itself is because it uses a proprietary format.  Gaming consoles are the same I believe, though I can back up my PS3 over the network to an external device.  The backup is encrypted, though.

---

