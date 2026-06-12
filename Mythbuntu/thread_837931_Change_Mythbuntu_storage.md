---
title: "Change Mythbuntu storage"
date: 2008-06-23
forum: Mythbuntu
---

### Post by armandop on 2008-06-23
newbie here,

I installed Mythbuntu on a small partition and want to use another partition for storage.

Should I delete the folders under /var/lib/mythtv and mount the storage partition here ?

or delete the folders and create a link to the storage partition mounted somewhere else ?

What about rights as far as the mythbuntu account for writing to the storage partition ?

I'd prefer to keep mythbuntu config to default and modify the underlying filesystem to support my storage requirements.

Thanks

---

### Post by bah1976 on 2008-06-23
First, it is not difficult to change myth locations using storage groups (assuming you're using 8.04).  Look in the last option during backend setup.

However, I also did not want to change the myth config for storage locations, so I renamed the existing 4 folders in /var/lib/mythtv and created links to my new location.  In this setup, my /mnt/bfd is a 1TB RAID5 md array.

So I have this in /var/lib/mythtv:

```

bruce@MythTV-BE:/var/lib/mythtv$ ls -hl
lrwxrwxrwx 1 root   root     22 2008-06-11 15:48 music -> /mnt/bfd/mythtv/music/
drwxrwsr-x 2 mythtv mythtv 4.0K 2008-06-11 15:48 music.org
lrwxrwxrwx 1 root   root     25 2008-06-11 15:48 pictures -> /mnt/bfd/mythtv/pictures/
drwxrwxr-x 3 mythtv mythtv 4.0K 2008-05-15 20:09 pictures.org
lrwxrwxrwx 1 root   root     27 2008-06-11 15:30 recordings -> /mnt/bfd/mythtv/recordings/
drwxrwsr-x 2 mythtv mythtv 4.0K 2008-06-11 15:30 recordings.org
lrwxrwxrwx 1 root   root     23 2008-06-11 10:40 videos -> /mnt/bfd/mythtv/videos/
drwxrwxr-x 2 mythtv mythtv 4.0K 2008-04-21 08:03 videos.org

```

and this in /mnt/bfd/mythtv
```

bruce@MythTV-BE:/mnt/bfd/mythtv$ ls -hl
drwxr-xr-x 2 mythtv mythtv    6 2008-06-11 15:47 music
drwxr-xr-x 2 mythtv mythtv    6 2008-06-11 15:47 pictures
drwxr-xr-x 2 mythtv mythtv 4.0K 2008-06-22 22:49 recordings
drwxr-xr-x 2 mythtv mythtv   23 2008-06-18 08:05 videos

```

If I remember right, I did something like this for each of the four folders (videos, music, recordings, pictures).

```

sudo mkdir /mnt/bfd/mythtv/recordings

```

```

sudo chown mythtv:mythtv /mnt/bfd/mythtv/recordings

```

```

sudo ln -s /mnt/bfd/mythtv/recordings /var/lib/mythtv/recordings

```

---

### Post by jwrudolf on 2008-06-24
In my opinion the easiest way to do this is to mount your second hard drive as /var/lib/mythtv. Format the hard drive then launch a terminal.  Mount the hard drive as /var/lib/mythtv (the default directory).  Then make four folders within mythtv: music, videos, recordings, pictures.  You need to edit fstab to mount the hard drive upon boot. Then you have to give permission to the mythtv user to write to the new folders.  You might also consider creating temp and archive folders in mythtv so that this information is processed on the second hard drive.

Here's some code to do that. Note that your hard drive may not be sdb1.  It depends on what the type of drive and how it is connected to the motherboard.

```


sudo mount /dev/sdb1 /var/lib/mythtv

sudo mkdir music
sudo mkdir pictures
sudo mkdir recordings
sudo mkdir videos
sudo mkdir temp
sudo mkdir archive

cd ~
sudo umount /dev/sdb1


```

Now you need to check the UUID of the device so you can insert that information into fstab.

```

ls -l /dev/disk/by-uuid/

sudo nano /etc/fstab


```

add the following to the bottom of fstab (the first line is a label so you know which device the uuid refers to so name it whatever you want, hit enter and separate each group on the second line with a single space, don't forget to substitute your devices uuid number in the stead of pasteyouruuidnumberher)

```

# /dev/sdb1
UUID=pasteyouruuidnumberhere /var/lib/mythtv xfs defaults 1 2

```

hit ctrl-x to exit, y to save, then enter to return to the terminal

reboot and then we'll give permission for mythtv to use the new hard drive

```

sudo chmod 775 /var/lib/mythtv/music
sudo chmod 775 /var/lib/mythtv/pictures
sudo chmod 775 /var/lib/mythtv/recordings
sudo chmod 775 /var/lib/mythtv/videos
sudo chmod 775 /var/lib/mythtv/temp
sudo chmod 775 /var/lib/mythtv/archive

sudo chown mythtv:mythtv /var/lib/mythtv/music
sudo chown mythtv:mythtv /var/lib/mythtv/pictures
sudo chown mythtv:mythtv /var/lib/mythtv/recordings
sudo chown mythtv:mythtv /var/lib/mythtv/videos
sudo chown mythtv:mythtv /var/lib/mythtv/temp
sudo chown mythtv:mythtv /var/lib/mythtv/archive


```

If you elected to create archive and temp folders in the mythtv folder we need to change the archive and temp working paths to reflect the new temp and archive folders


Launch the Frontend and then navigate to archive file setting via the following

Utilities/Setup > Setup > MediaSettings > ArchiveFileSettings

Replace the temp directory with        /var/lib/mythtv/temp
Replace the archive directory with     /var/lib/mythtv/archive

You should now have the second hard drive configured as the space to work off of and save recordings to as well.  I hope this helps. 

If anyone else has a preferred method for how to best add a second hard drive, I think it would be great to add it or create a howto sticky where they could be located.  The second hard drive is a necessary addition in my book but is not all that easy to do for recent converts to linux (myself included).

---

### Post by gslauen on 2008-10-10
> **jwrudolf said:**
> In my opinion the easiest way to do this is to mount your second hard drive as /var/lib/mythtv. Format the hard drive then launch a terminal.  Mount the hard drive as /var/lib/mythtv (the default directory).  Then make four folders within mythtv: music, videos, recordings, pictures.  You need to edit fstab to mount the hard drive upon boot. Then you have to give permission to the mythtv user to write to the new folders.  You might also consider creating temp and archive folders in mythtv so that this information is processed on the second hard drive.

Here's some code to do that. Note that your hard drive may not be sdb1.  It depends on what the type of drive and how it is connected to the motherboard.

```


sudo mount /dev/sdb1 /var/lib/mythtv

sudo mkdir music
sudo mkdir pictures
sudo mkdir recordings
sudo mkdir videos
sudo mkdir temp
sudo mkdir archive

cd ~
sudo umount /dev/sdb1


```

Now you need to check the UUID of the device so you can insert that information into fstab.

```

ls -l /dev/disk/by-uuid/

sudo nano /etc/fstab


```

add the following to the bottom of fstab (the first line is a label so you know which device the uuid refers to so name it whatever you want, hit enter and separate each group on the second line with a single space, don't forget to substitute your devices uuid number in the stead of pasteyouruuidnumberher)

```

# /dev/sdb1
UUID=pasteyouruuidnumberhere /var/lib/mythtv xfs defaults 1 2

```

hit ctrl-x to exit, y to save, then enter to return to the terminal

reboot and then we'll give permission for mythtv to use the new hard drive

```

sudo chmod 775 /var/lib/mythtv/music
sudo chmod 775 /var/lib/mythtv/pictures
sudo chmod 775 /var/lib/mythtv/recordings
sudo chmod 775 /var/lib/mythtv/videos
sudo chmod 775 /var/lib/mythtv/temp
sudo chmod 775 /var/lib/mythtv/archive

sudo chown mythtv:mythtv /var/lib/mythtv/music
sudo chown mythtv:mythtv /var/lib/mythtv/pictures
sudo chown mythtv:mythtv /var/lib/mythtv/recordings
sudo chown mythtv:mythtv /var/lib/mythtv/videos
sudo chown mythtv:mythtv /var/lib/mythtv/temp
sudo chown mythtv:mythtv /var/lib/mythtv/archive


```

If you elected to create archive and temp folders in the mythtv folder we need to change the archive and temp working paths to reflect the new temp and archive folders


Launch the Frontend and then navigate to archive file setting via the following

Utilities/Setup > Setup > MediaSettings > ArchiveFileSettings

Replace the temp directory with        /var/lib/mythtv/temp
Replace the archive directory with     /var/lib/mythtv/archive

You should now have the second hard drive configured as the space to work off of and save recordings to as well.  I hope this helps. 

If anyone else has a preferred method for how to best add a second hard drive, I think it would be great to add it or create a howto sticky where they could be located.  The second hard drive is a necessary addition in my book but is not all that easy to do for recent converts to linux (myself included).

When I try this and do chmod I get an error message that the there is no such file or directory. I have the drive mounted but it seems to me that if your creating the directories they are just going to be created in the root and when I try to change permissions the directories can not be found.

Any ideas?

---

### Post by newlinux on 2008-10-10
yes, you should be creating the directories in /var/lib/mythtv. Easiest thing to do is probably a ```
cd /var/lib/mythtv
``` before creating the directories with mkdir.

---

### Post by MikeEnIke on 2008-12-28
Hey can I get a little help on this despite it being old? I got all the way down through the chmod but when I try to chown I get 

```
mike@mike-desktop:/var/lib/mythtv$ sudo chown mythtv:mythtv /var/lib/mythtv/music
chown: changing ownership of `/var/lib/mythtv/music': Operation not permitted
```

---

### Post by Das Hammer on 2009-06-02
If you put a -R at the end of the command you show there, that will change the ownership for all files and subdirectories within /var/lib/mythtv/music. That might help.

What you have typed there looks correct.

---

