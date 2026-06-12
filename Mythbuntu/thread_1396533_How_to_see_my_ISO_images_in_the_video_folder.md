---
title: "How to see my ISO images in the video folder"
date: 2010-02-02
forum: Mythbuntu
---

### Post by jenskjensen on 2010-02-02
Hi.

Bear with me, I have not used Unix before but trying to find a system to watch TV and iso files instead of windows and I know that my question is for sure a newbi question.

Im trying it on a old laptop before going out buy hardware.

Im planning to buy a ASRock ION 330 to use as both frontend and backend and have all my video files shared from a Synology NAS Server using NFS.

I have managed to mount the Synology Video folder in fstab but when going into the video folder in mythtv its empty. 
I can see the videos (ISO images) in VNC so the mount is working.

I have also been into the setup of the video folder and set it up to look at the mount point.

Have I done anything wrong or do I only need to update Myth the database to see the videos? If so, how do I do that?

Please help a newbee :)

Best regards,
Jens

---

### Post by jayman8547 on 2010-02-02
If you set up the video folder for the backend then you are using storage groups and myth won't see the iso's.

If you set up the video folder for the frontend then it should work.

As for using an ASRock ION 330 for both a BE and FE, based on my experience, might be pushing it a little.  I have 2 Zotac ionitx-a (330 ion) as dedicated FE's and they run great.  Checking top or htop they run between 5-25% CPU utilization using vdpau.  Might want to grab an old system to use as a dedicated BE since you don't really need too much horsepower to run - Can be a single core P4 with a couple gigs of RAM.

---

