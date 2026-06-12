---
title: "Where does Mythbuntu put its media?"
date: 2011-03-23
forum: Mythbuntu
---

### Post by beardos on 2011-03-23
Afternoon,
I'm building a new system and have looked into how I should partition my hard drives (1x SSD 60GB and 1x 3TB drive).
I've settled on a swap space of 4GB on SSD, 20GB on/root (for programs) but if I create the 3TB drive as a /home drive, will Mythbuntu automatically put its recording in here or will I have to some how repoint things to this drive? If so, how do I do it?

I've searched through these forums all day (Rather than do my job so I'm already a winner today) but don't want to do a fresh install of mythbuntu only to find it's putting all the media in root.....

Please somebody, give me some advice.......

Thanks

---

### Post by tgm4883 on 2011-03-23
> **beardos said:**
> Afternoon,
I'm building a new system and have looked into how I should partition my hard drives (1x SSD 60GB and 1x 3TB drive).
I've settled on a swap space of 4GB on SSD, 20GB on/root (for programs) but if I create the 3TB drive as a /home drive, will Mythbuntu automatically put its recording in here or will I have to some how repoint things to this drive? If so, how do I do it?

I've searched through these forums all day (Rather than do my job so I'm already a winner today) but don't want to do a fresh install of mythbuntu only to find it's putting all the media in root.....

Please somebody, give me some advice.......

Thanks

Default locations are at /var/lib/mythtv/<folder>  Do **_not_** put the storage directory in your home directory, you **_will_** have issues.

---

### Post by xinix on 2011-03-23
You can mount your drive at a mount point you choose and then point mythtv to this partition in storage groups.  For example I have multiple drives that I mount in logically named folders eg. /Mythtv/1, /Mythtv/2 ...

---

### Post by LowSky on 2011-03-25
create the new folders in a new location. like tgm4883 said dont put them in your home folder as the permissions will be a problem. If the /home/user directory takes up the entire 3TB HD, then the easiest thing to do without creating new partitions would be to create a /home/media directory that will be part of the mythtv group and permission of the mythtv user.

copy the folder names from /var/lib/mythtv into the new /home/media/ folder
then go insto the mythtv backend and change the storage group locations

then sign into the mythtv frontend go into setup> media settings> video settings (i think.. and too lazy to check) and change the folder locations to the new ones there too.

that should do it.

---

