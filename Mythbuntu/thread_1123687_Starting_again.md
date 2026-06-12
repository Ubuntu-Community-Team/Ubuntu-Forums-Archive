---
title: "Starting again"
date: 2009-04-12
forum: Mythbuntu
---

### Post by Billsputters on 2009-04-12
I think I got in an awful mess with my last install attempt, so deleteing it all and starting again.

Two partitions
8 Gb EXT3 / for the install
980 Gb XFS /data for mythtv and backups

/data/mythtv is used for mythtv with directories
/data/mythtv/music
/data/mythtv/livetv
/data/mythtv/recordings
/data/mythtv/photos
/data/mythtv/posters
/data/mythtv/archive

all of which are quite obvious by their names

then 

```
sudo chmod a+rwx /data/mythtv/music 
sudo chmod o-w /data/mythtv/music 
sudo chmod g+s /data/mythtv
``` as per [ [COLOR="Red"]FatMonks suggestion[/COLOR]]("http://ubuntuforums.org/showthread.php?t=779498&page=3&highlight=partitions") suggestion
as well as the ```
sudo chown mythtv:mythtv /data/mythtv/music
sudo ln -s /data/mythtv/music /var/lib/mythtv/music
```
This is where I get confused. There is already a directory entry in /var/lib/mythtv called music, so adding a sym link in confuses things. So I deleted the directory before adding the sym link. As an experiment I fired up MythTV and imported some music files and it put them where I wanted - /data/mythtv/music although the default directory for music storage was left as its default of /var/lib/mythtv/music.

So far so good.

I notive that that all four directories in /var/lib/mythtv are shared. I lost the SMM mounts for them when did a system upgrade, so should I share them again (I assume it's so other frontends can access data from the backend), as what user and group (mythtv I am guessing) and can I share a sym link?

---

### Post by nickrout on 2009-04-12
> **Billsputters said:**
> I think I got in an awful mess with my last install attempt, so deleteing it all and starting again.

Two partitions
8 Gb EXT3 / for the install
980 Gb XFS /data for mythtv and backups

/data/mythtv is used for mythtv with directories
/data/mythtv/music
/data/mythtv/livetv
/data/mythtv/recordings
/data/mythtv/photos
/data/mythtv/posters
/data/mythtv/archive

all of which are quite obvious by their names

then 

```
sudo chmod a+rwx /data/mythtv/music 
sudo chmod o-w /data/mythtv/music 
sudo chmod g+s /data/mythtv
``` as per [ [COLOR="Red"]FatMonks suggestion[/COLOR]]("http://ubuntuforums.org/showthread.php?t=779498&page=3&highlight=partitions") suggestion
as well as the ```
sudo chown mythtv:mythtv /data/mythtv/music
sudo ln -s /data/mythtv/music /var/lib/mythtv/music
```
This is where I get confused. There is already a directory entry in /var/lib/mythtv called music, so adding a sym link in confuses things. So I deleted the directory before adding the sym link. As an experiment I fired up MythTV and imported some music files and it put them where I wanted - /data/mythtv/music although the default directory for music storage was left as its default of /var/lib/mythtv/music.

So far so good.

I notive that that all four directories in /var/lib/mythtv are shared. I lost the SMM mounts for them when did a system upgrade, so should I share them again (I assume it's so other frontends can access data from the backend), as what user and group (mythtv I am guessing) and can I share a sym link?

why not just use the setup mythbuntu gave you?

---

### Post by Billsputters on 2009-04-12
So that there is a separate partition for the data.

Doesn't /var get overwritten if you have to reinstall. You would have to backup all that video and audio data first. Same reason that it advised to keep /home on a separate partition on many installs.

---

### Post by nickrout on 2009-04-13
> **Billsputters said:**
> So that there is a separate partition for the data.

Doesn't /var get overwritten if you have to reinstall. You would have to backup all that video and audio data first. Same reason that it advised to keep /home on a separate partition on many installs.

by default now mythbuntu mounts /var/lib as a separate partition as xfs.

---

### Post by Billsputters on 2009-04-13
Indeed it does. But my point still stands that for whatever reason should use reinstall, /var gets reformatted. So all video data has to be backed up beforehand. There are other threads around regarding partitioning, and many use a separate partition for video and audio data for this very reason.

I wish to do the same, and also have the /data partition used as a backup area for out two laptops, hence the /data/backups directory.

It's just a different way of doing things, and shouldn't be that complex, just a case of pointing the defaults to somewhere else and trying to figure how things are done.

---

### Post by nickrout on 2009-04-13
> **Billsputters said:**
> Indeed it does. But my point still stands that for whatever reason should use reinstall, /var gets reformatted. So all video data has to be backed up beforehand. There are other threads around regarding partitioning, and many use a separate partition for video and audio data for this very reason.

I wish to do the same, and also have the /data partition used as a backup area for out two laptops, hence the /data/backups directory.

It's just a different way of doing things, and shouldn't be that complex, just a case of pointing the defaults to somewhere else and trying to figure how things are done.

Then I suggest you take guidance from the permissions etc for /var/lib/mythtv and apply the same permission and ownership to your /data directries.

---

