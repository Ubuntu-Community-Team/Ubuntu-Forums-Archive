---
title: "Anyone use Rhythmbox Music Player?"
date: 2009-05-12
forum: Multimedia Software
---

### Post by The Switch Blade on 2009-05-12
I have a few problems with it.

My folder hierarchy isn't listed. I have /Artist/(Year - Album)/

My file name isn't listed. I have Artist - (Year - Album) Number. Title

It won't let me move the columns to where I want them. It shows Track Title Artist Album Year Time. I want Artist Year Album Number Title Time, or something like that. Just different than what it is now.

Most importantly, my files won't sort correctly. It only sorts by one column, so I can sort by album but then it shows the album with the lowest first letter rather than the lowest year.

:( Help?

---

### Post by The Switch Blade on 2009-05-15
Oh, and this is the worst part: every time I open the program it has to search for all 115gb of my music. It takes 20 minutes for my collection to be ready to play!

---

### Post by kpkeerthi on 2009-05-15
Is your music collection properly tagged? I don't face any of the issues you have with Rhythmbox.

---

### Post by Gausian on 2009-05-15
i agree with the tags issue.  take the time to correctly tag your files and you'll save yourself time in the longrun

---

### Post by The Switch Blade on 2009-05-15
Every single one of my 12936 songs is tagged exactly correctly. I have mild OCD with regard to my music collection.

Every single song has artist, title, year, album, and track number... and ONLY those tags.

In addition to that, my folder structure and filenamings are precise as well. Every song is in Storage/Music/Artist/Year - Album with the filename Artist - (Year - Album) Number. Title.

Everything. I also don't have any single MP3s, everything is a full album.

Yet it shows my albums in the incorrect order. It will sort them by artist and album, but it disregards year. The only solution I could think of for this is to put the year in the album tag... but that would be a lot of work for 1143 albums. :/

---

### Post by The Switch Blade on 2009-05-17
Any thoughts on the sorting problem? If anything, I'd really like that to be solved.

For example, this is how it shows:

[IMG]http://img40.imageshack.us/img40/4827/screenshotjasonmrazcurb.png[/IMG]

Clearly, it's not right. The year column is completely ignored.

Also, it can't detect FLAC quality, but that doesn't bother me.

---

### Post by mrdoser on 2009-05-21
*bump*

I have the same problem. I want to sort by:
Artist - Album Year - Album Title - Track# - Track Title

Is this not possible with Rhythmbox? I'd have to find a music player that does this then.

---

### Post by durand on 2009-05-21
Have you tried other music players like amarok or banshee or listen to see if the problem is with rhythmbox and not your music files?

---

### Post by The Switch Blade on 2009-05-21
I tried amarok and it didn't work.

If it makes a difference (it probably does) my music is on my slave drive, which is NTFS.

---

### Post by durand on 2009-05-21
> **The Switch Blade said:**
> I tried amarok and it didn't work.

If it makes a difference (it probably does) my music is on my slave drive, which is NTFS.

Elaborate on "didn't work". It won't matter if it's on a slave drive. If amarok doesn't work with your music, I'd have to say that your music files are the problem and not the media player though I'm not really sure why.

---

### Post by zika on 2009-05-21
> **The Switch Blade said:**
> I tried amarok and it didn't work.

If it makes a difference (it probably does) my music is on my slave drive, which is NTFS.
do You auto-mount Your NTFS partition or not? do You mount it after log-in? If that is the case that might be the source of Your problems ... :)

---

### Post by The Switch Blade on 2009-05-21
It wouldn't play the music, said it had errors or something like that. It imported all of them but just wouldn't play them.

I just switched over from windows and had absolutely 0 problems... =/

---

### Post by The Switch Blade on 2009-05-21
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=56682c83-fcbf-4915-b037-9177abb55cf9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63482991-a509-4d2f-bfa1-3f52d215ad5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

sudo fdisk -l
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b037b03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9598    77095903+  83  Linux
/dev/sda2            9599       10011     3317422+   5  Extended
/dev/sda5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
16 heads, 63 sectors/track, 1240341 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb7931725

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4162     1240338   623033208    7  HPFS/NTFS
```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G   13G   57G  19% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  224K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  148K  1.5G   1% /dev
tmpfs                 1.5G  188K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             595G  211G  385G  36% /media/Storage
```

How do I make it a static device?

---

### Post by durand on 2009-05-21
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by The Switch Blade on 2009-05-21
Okay, I did that. Hopefully it will solve some problems. Still won't sort by artist/year :(

---

### Post by durand on 2009-05-21
Hmm, you might be able to fix the tags with [easytag]("apt://easytag").

---

### Post by The Switch Blade on 2009-05-22
I have easytag and all of my files are correctly tagged, I promise you.

---

### Post by durand on 2009-05-22
In that case, I really have no others ideas other than to suggest other media players. Banshee would be a good choice but I can't vouch for it. I use mpd+sonata which isn't really a traditional media player so it might not be for you but it's very good.

---

