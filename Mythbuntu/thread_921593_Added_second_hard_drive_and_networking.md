---
title: "Added second hard drive and networking"
date: 2008-09-16
forum: Mythbuntu
---

### Post by Caps18 on 2008-09-16
It's been a long time since I've had to ask any questions here, which is a good thing since my Mythbuntu computer has been running great.  I love it and am thinking of getting a third 1080p display for another room in my house.

I was able to install a 1 TB hard drive yesterday with no problems with the JFS file system.  It shows up as a empty disk under /media/disk (or something like that).  I would like to use this new hard drive just for MythVideo, but I'm not sure how to switch it from /var/lib/video to /media/disk/video or where ever it should be.  Do you guys have any advice or how-to's hidden away someplace?

The second question is about setting up basic networking.  I have a laptop (192.168.1.44) and my mythbuntu computer (192.168.1.46).  I'm trying to setup NFS, but I get Permission Denied error messages when I try to mount the remote directory.
(mount -t nfs caps:/home/caps/remote /mnt/laptop)  caps is the user on my laptop, but mythbuntu is the user on the mythbuntu computer.  I thought that I had updated the /etc/exports file correctly, and the /etc/fstab to automatically connect, but is there any other file that I need to update?  Or do I need to restart my laptop for the settings to take effect?  What permissions should the directories have and who should be the owner/user?

(I will say that I only spent 30 minutes trying to get networking to work last night a 1:30am, I'll try again tonight a little earlier)

Thanks!

---

### Post by anonymousdog on 2008-09-16
Try 'mount -t nfs 192.168.1.46:/home/caps/remote /mnt/laptop' instead.

The quick 'n dirty: Move your videos to the new drive, change their location in mythtv setup, and use the video manager to rescan for them.  Change the symlinks in /usr/share/mythtv/mythweb/data to point to the correct directories for video and video_covers.

---

