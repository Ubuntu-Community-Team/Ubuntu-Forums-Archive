---
title: "Mythvideo - sharing files to remote frontend"
date: 2009-10-18
forum: Mythbuntu
---

### Post by johnvan on 2009-10-18
It seemed like it was going to be simple but I guess not. I'm setting up a separate frontend, everything went pretty smoothly except I can't figure out how to make the videos on my backend accessible to my frontend.

I have the folder shared with samba and can access all videos easily with my XBOX running XBMC.

When I first installed this mythtv frontend I was able to see all of the videos but couldn't play them.  I messed around with some things and now I cant even see them.
I've googled around and can't find any decent info on this.  I tried the wiki mediashares page and got to the part about doing mythtv id.  It says if your uid is different you need to fix that, great, real helpful. How?

Anybody have any links to a basic tutorial on this.
Thanks.

---

### Post by SiHa on 2009-10-19
Are the paths to the media foldesrs on your frontend the same as on the backend? They should be.

---

### Post by johnvan on 2009-10-19
I have a combine frontend/backend where the path to my videos is /media/sdb1/seagate.  I can access and watch videos from that directory on that frontend.

I'm setting up a remote frontend and can't figure out the videos.  I guess I need to figure out a way to browse the files on my backend, create a link to them and then have it automount??

---

### Post by SiHa on 2009-10-19
I suppose. I'm not too knowledgeable on Samba, I use NFS - it seemed far simpler to setup when I first looked at this last year. (Still does!)

You need an fstab entry on the remote frontend for the samba share, and the mount point on that FE should match the path to the folder on the BE/FE machine.
**However,** I'm not sure that having a path that explicitly refers to sdb1, which is on the backend will work (or is a good idea, at least). You'd have to create /media/sdb1 on the FE, and that could cause all sorts of nasties should you ever mount a second drive on that machine.

I would change the mount point of the drive on the BE/FE to something else (maybe /var/lib/mythtv/videos?:)), and duplicate that in the fstab entry on the FE.

Googling 'samba ubuntu fstab' yields quite a few hits on automounting samba shares.

---

### Post by johnvan on 2009-10-19
Major progress!  I insralled pyNeighborhood and had two groups, MSHOME and WORKGROUP. I renamed my new mythtv frontend to WORKGROUP in smb.conf. I could only get to my videos by manually adding the machine in pyNeighborhood and starting pyNeighborhood in terminal with sudo.

I created a link and stuck it in /var/lib/mythtv/videos on my new frontend. It works!

The only problem now is to have it mount automatically.  The mount point is /mnt/lan/john-desktop/seagate  I guess I put that in FSTAB?

---

### Post by bsntech on 2009-10-19
In the FSTAB, you will probably need something like:

//john-desktop/seagate  /var/lib/mythtv/videos smbfs users,default,umask=000 0 0

This  might be of some help:
[http://www.linuxquestions.org/questions/linux-newbie-8/mounting-an-smbfs-using-fstab-461202/]("http://www.linuxquestions.org/questions/linux-newbie-8/mounting-an-smbfs-using-fstab-461202/")

---

### Post by johnvan on 2009-10-19
I got it working in FSTAB, thanks a lot!

---

