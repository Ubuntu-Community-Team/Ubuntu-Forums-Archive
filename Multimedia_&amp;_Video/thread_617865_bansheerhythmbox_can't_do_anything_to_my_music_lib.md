---
title: "banshee/rhythmbox can't do anything to my music library or my old ipod"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by deruberhanyok on 2007-11-19
Alright Ubuntu crowd, I've run into another problem that I *think* involves file permissions/ownership for at least part of it. Let me break it down into two parts:

Rhytmbox and Banshee are both set to be able to manage my music library. I've been trying both for a while to see which one I like more (I'm currently leaning towards Banshee if it matters). My music directory is located on a second internal hard drive's FAT32 partition, so that I can access it from Windows if I want. The partition is set to mount when Ubuntu loads. Here is my /etc/fstab file, before anyone asks:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fed3fbcd-6e23-459d-b39b-6a24b660ba8c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
# UUID=FEE8BF23E8BED95B /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
# UUID=3284CADB84CAA129 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=46F6-8559  /media/sdb2     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdb3
UUID=e77ab9dc-2c91-4f82-9d54-52eca81eb56a /media/linux_etc     ext3    defaults        0       0
# /dev/sda3
UUID=cdad71cd-a166-42f1-af9b-a5e082cacbc3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

The partition in question is /dev/sdb2. I already had [some issues]("http://ubuntuforums.org/showthread.php?t=570550") regarding permissions that led me to set up fstab this way.

The current issue is twofold:

1) Both Banshee and Rhytmbox cannot actually make changes to my library (file metadata in various formats doesn't actually update, files I delete aren't actually deleted, downloaded cover art never gets saved, etc).

I've tried changing ownership of the partition (sudo chown -R matt /media/sdb2) and I get 'operation not permitted' errors. For the heck of it I set both apps to use my /home/matt/Music folder and imported a single directory of about 20 tunes knowing I'd have full permissions.

If I change file metadata in banshee - and the 'write metadata to files' option is checked - and then update the library in rhythmbox, it doesn't show the metadata changes. Even in this folder in my home directory it won't make changes to the files or save cover art. Rhythmbox doesn't even let mechange things like artist/album name.

So, how do I get these programs to work like they should?

2) iPod functionality is... odd.

I've got a fourth gen 20GB iPod running firmware 3.1.1. I've just recently done a restore on it so I can start fresh in Linux.

Banshee doesn't seem able to sync playlists to the iPod, but if I drag files over manually and hit 'manual sync' it works. It puts the updated metadata on there, too, although my iPod's name still won't change on the device itself.

Syncing songs from Rhythmbox takes AGES over both USB and Firewire and the songs will not play on the iPod at all once they are done syncing. File sizes are all messed up, too, for example a 6MB M4A file that is about 3 minutes long, once synced, shows up as a 3MB file that is 13 minutes long in nautilus and nothing can read it.

That said I'm pretty much done with Rhythmbox. I'd like, if possible, to get Banshee working without relocating my music directory - my home folder and OS is installed on a small hard drive and I have a large drive for storing all of that stuff.

help?

---

### Post by deruberhanyok on 2007-11-20
I've just tried having the partition auto-mount to a folder in my home directory, just so I could skip around the permissions problem.

I also tried using Exaile - it's pretty nice so far, not sure if I'm gonna stick with it yet - and it helpfully displayed errors when I tried editing song info.

From what I can tell, the problem is more specific than I thought:

1) it doesn't seem that any of the apps I've tried can actually 'organize' the music library folder the way iTunes can - renaming files/folders, etc, although I can now edit some metadata and have it actually write to the file. Should Banshee (or Exaile, I suppose) be capable of this? Have I missed something?

2) apparently file metadata writing to AAC files isn't working in any application. Is this a bug that should be reported or am I just doing something wrong?

I'm starting to wonder if I'd be better off re-ripping what music I can to MP3 format, or trying to get ogg files playable on my iPod.

---

