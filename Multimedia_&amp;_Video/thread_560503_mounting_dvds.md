---
title: "mounting dvds"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by rgb on 2007-09-26
Hi,

I had posted my problem in the 'Absolute Beginner Talk' section 
[http://ubuntuforums.org/showthread.php?t=542947](http://ubuntuforums.org/showthread.php?t=542947)
after trying out the suggestions in this user forum, that seemed relevant. but got no replies. So, I am retrying here:

First the background: I am running ubuntu edgy on a T42 laptop with a cd-dvd rom drive. I used to be able to play dvds on it using xine/vlc (last played about a month ago) . However, trying to do so today is giving me trouble.

1. dvds used to automount for me (gnome), and I could play them using xine/vlc without problems. Today it did not. However, I can still play multimedia clips (eg. avi format), or clips on youtube. 

2. I reinstalled w3codecs and libdvdread using apt-get. 

3. I also made the same modifications to the /etc/modules file suggested here, namely appending to the end
```

libata
ata_piix
piix

```

4.ls -l /dev/dvd gives
lrwxrwxrwx 1 root root 3 Sep 25 23:43 /dev/dvd -> hdc
On trying to run xine I get
```

libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

```

My fstab contains
```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /mnt/dvd   udf,iso9660 auto,user     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
5. ls -l gives
```

ls -l /dev |grep dvd
lrwxrwxrwx 1 root root           3 Sep 25 23:43 dvd -> hdc

```
6. Trying
```

sudo mount /dev/hdc

```
gives
```

mount: No medium found

```
I think I am unable to mount the dvd which has movies. I do not have a data dvd to check if it can read data dvds. I do not have a windows partition either to see if the drive will play it on windows, I can played audio cds. Later, I can check if the dvd plays on other computers.

Regards, and thanks in advance for help.

---

