---
title: "Upgraded to 0.27 no commercial detection during recording"
date: 2013-09-27
forum: Mythbuntu
---

### Post by TheFuzz4 on 2013-09-27
So yesterday I upgraded from 0.26 to 0.27.  The main reason for going to the next version was due to exiting the video playback (not recordings) would kill the front end with video files with H264.  (Its a documented bug that was fixed in 0.27)  

Since upgrading all of my new recordings, the commercial detection is not running on the shows.  I've had it set up for a long time to do the detection while it records but none of the shows yesterday were flagged.  I went back into each show and told Myth to go flag each show and that worked.  Has anyone else experienced this?  Did I miss something in the release notes that changed how the commercial detection works?  Thank you all in advance for your help with this.

---

### Post by TheFuzz4 on 2013-09-27
So I just noticed one of the things its doing.  During the recording its attempting to flag the commercials however after a few mins it marks the job as completed although the recording is still being recorded.

---

### Post by TheFuzz4 on 2013-09-27
Ok so I think that I have discovered the problem.  Up until yesterday I was storing my recordings on a USB enclosure setup in Raid1.  Recently we've had issues where the drive would just unmount itself under any kind of load.  So in order to rectify this I took the drives out of the enclosure and stuck them into my FreeNAS box.  It appears that the 1GB network that my backend, freenas and other servers at home are on (my frontends and everything else in the house is 100BaseT) can't handle the HD Homerun Prime, backend, and freenas all working at top speed.  So I turned off the realtime detection and just have it set to detect after it completes the recording.  Why didn't I put the drives in the backend?  Because my backend is a HP DL385 that holds SAS drives and once Comcast starts encrypting my Clear QAM next month the internal Hauppauge tuner card will be rendered useless and I intend to stick ESXi on this server and then virtualize my backend, and get another HD Homerun to make up for the 2 tuners that I'm going to loose.  At least this way with the drives in the NAS it will make migrating my backend to a VM quite simple.  If anyone has any tips on a work around to leave the on the fly detection enabled let me know.  Thanks.

---

