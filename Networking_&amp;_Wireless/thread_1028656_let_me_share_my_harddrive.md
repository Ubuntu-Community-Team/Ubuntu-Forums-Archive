---
title: "let me share my harddrive"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by brusifur on 2009-01-02
ok so, i have 2 machines, one with xp and one with ubuntu. The latter has my music/pics/vids etc on a second  internal harddrive. I want to share this drive. If i right click on the drive, and go to "sharing options", i get this message:
> 'net usershare' returned error 255: net usershare add: cannot share path /media/DRV2_VOL1 as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

I am the only user of this computer, and i thought i gave myself all the admin rights.  When i open the file and edit the line to read "usershare owner only = False", i get a similar message saying im not allowed to do that either. At this point ive hit the brick wall.  I poked around in System->Admin->Authorizations but nothing there looks promising.  Helo, i am frustrated:confused:

---

### Post by mrjohnston on 2009-01-02
Alright, it likely is mounting the second hard drive as root for the owner.  Right click on the files or folders on the second hard drive and go to permissions to verify owner.  

If that is the case, you can open a terminal and type sudo chown [your user]:[your user] -R /path/to/drive

Make sure to use your username in the 2 spots listed (and no brackets) and the path to your drive where it says path to drive (likely /media/disk or something similar)

That should let you share everything just fine.

---

