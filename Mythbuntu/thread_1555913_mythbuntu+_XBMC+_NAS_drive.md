---
title: "mythbuntu+ XBMC+ NAS drive ??"
date: 2010-08-18
forum: Mythbuntu
---

### Post by WannaSpeedCom on 2010-08-18
I purchased a NAS media drive by iomega w/ UPNP/DLNA media server. I was going to use it with my xbox 360.It connects fine, but won't stream my DVD backups in DVD format. This means I would have to convert them to H.264 or other compatible media. My single core 2.66 ghz PC takes between 11-24 hrs to convert 1 movie at a decent bitrate! 

I started thinking about using a media front end or front end/back end instead of the x360. I'm using an old 1.2 ghz computer as a temporary test bed for different options.

Unfortunately I couldn't get XBMC to install due to graphics card/drivers. But I do have mythbuntu installed. 

Linux doesn't just see the NAS drive like XP. The NAS uses several folders that appear as seperate drives. As a test I temporarily mounted the music folder(drive)using cifs.

**Now for my questions:**

1) Does mythbuntu only work with mythbuntu (mythtv) running as a backend? Or can it detect other UPNP servers? (tversity, my NAS media drive, etc)

2)Where do I add video/music folders for streaming through mythtv? (not recording) Example: My NAS music folder is mounted at /mnt/NAS/music, In order to play the music do I add this directory to the mythtv backend or the front end? And where in the setup is it added?

3)Does anyone know if XBMC will work with UPNP servers? (tversity, my NAS media drive, ETC)

I'm thinking my best bet may be to build a dual core system with a UPNP compliant front end (such as XBMC?), then if I want to compress dvd's it can handle that, and with a good graphics card I can stream either file type directly to my Tv. Thoughts?

---

### Post by WannaSpeedCom on 2010-08-18
I just got XBMC installed and working on the XP machine and it sees the drive and plays the files no problem. Looks really nice so I might build a system around it. I'm still wondering how to work mythbuntu as well.

---

### Post by ian dobson on 2010-08-19
Hi,

1) you need to have a mythtv backend running. The frontends main role is to playback recorded programs.
2) To play back "non-recorded" programs you need to install mythvideo and get it to search it's directories for new files. Mythtv uses a sql database (mysql) where is stalls all configuration options. You'd need to tell the frontend where the videos are. 
3) I've not used XBMC so I can't say if it support UPNP, I would image yes, but I don't really know.

Regards
Ian Dobson

---

