---
title: "drive configuration"
date: 2011-10-23
forum: Mythbuntu
---

### Post by T-W-X on 2011-10-23
Hello, old to Linux, but new to Ubuntu and MythTV.

I'm building a box for a backend/frontend setup.  Core2Quad Q8400, plan to have 8GB RAM, and I'm now at the point of choosing hard disk for the recording data and video capture device.

The board has four SATA ports, one in use for the 160GB OS drive, one in use for the SATA DVD, which I plan to upgrade to Blu-ray later.

We have broadcast TV only, no cable, no satellite.  I'll probably pick up a Hauppauge HVR-2250 or the like for the one PCIe slot on the board.  I'm considering either one or two hard disk drives, probably mirrored.  I plan to use this box to record all of our 1500 or so movies into, but most are on Laserdisc or VHS, so I won't have to go nuts with the quality settings.

Would you think a pair of 3TB drives mirrored would be adequate?

I do have an SAS controller in PCI laying around here somewhere, so if it's not I can always go bigger, but it'll obviously cost more, and I'm trying to avoid that as much as practical.

Thanks!

---

### Post by nickrout on 2011-10-24
> **T-W-X said:**
> Hello, old to Linux, but new to Ubuntu and MythTV.

I'm building a box for a backend/frontend setup.  Core2Quad Q8400, plan to have 8GB RAM,about four times more than you need, save your cash>  and I'm now at the point of choosing hard disk for the recording data and video capture device.

The board has four SATA ports, one in use for the 160GB OS drive, one in use for the SATA DVD, which I plan to upgrade to Blu-ray later.

We have broadcast TV only, no cable, no satellite.  I'll probably pick up a Hauppauge HVR-2250 or the like for the one PCIe slot on the board.  I'm considering either one or two hard disk drives, probably mirrored.  I plan to use this box to record all of our 1500 or so movies into, not really what myth is designed to do, you only really want myth if you plan to record TV. If you just want to watch movies, go XBMC.> but most are on Laserdisc or VHS, so I won't have to go nuts with the quality settings.

Would you think a pair of 3TB drives mirrored would be adequate?
well an SD movie can take, say, 1.4G if encoded with reasonable quality. Take 1500*1.4G = 2.1TB, so you have a bit of space, but you will run out eventually, we all do :)> 
I do have an SAS controller in PCI laying around here somewhere, so if it's not I can always go bigger, but it'll obviously cost more, and I'm trying to avoid that as much as practical.

Thanks!
Add more storage later.

If you are using your hvr2250 to encode your movies, you need do no more than connect the vhs or videodisk player to the analogue input and type cat /dev/video0>mymovie.mpg. Press ctrl-c when the recording is over. You will end up with an mpeg2 encoded movie. If you want to make it smaller, use handbrake to convert to the far superior h.264 codec.

Taking vhs and encoding it is a fine art, there are a lot of ways to enhance, and ruin, your movie. Do some reading at doom9.net and videohelp.com

Oh and personally I wouldn't bother with encoding crappy old vhs, unless it was irreplaceable. DVD is a much better source. As is bittorrent (obviously only for material that is legal to download ;) )

---

