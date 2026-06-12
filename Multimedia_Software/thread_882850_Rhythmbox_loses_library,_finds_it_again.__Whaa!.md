---
title: "Rhythmbox loses library, finds it again.  Whaa?!"
date: 2008-08-07
forum: Multimedia Software
---

### Post by eOgas on 2008-08-07
So I've got a pretty strange problem with Rhythmbox.  I'm assuming that this is the right forum to post on, if not please disabuse me.  Anyway, I have Rhythmbox set up to look for music in my My Music folder on my windows partition, because that's where all my music is.  When I start Rhythmbox, it starts with all the songs loaded already, but proceeds to lose them all.  The track count goes down (from 2364) all the way to zero because it thinks it doesn't have the tracks.  They all show up in the 'missing tracks' menu.  Rhythmbox then proceeds to find them all again, counting up from 0 all the way to 2364.  While everything still works, eventually, there is a considerable amount of time between when it starts and when I can listen to music....so what's up?!  Anybody have any ideas?  Thanks.

---

### Post by eOgas on 2008-08-07
bump?

---

### Post by hughc1 on 2008-08-20
I don't know why your library goes away. 
I've have a  similar problem when the network is down and Rhymbox can't find the drive.  The library deletes all the music.  Maybe your Windows partition isn't mounted when Rhythmbox starts?
Since losing the library I selected Edit/ Preferences/ Music and uncheck "watch my library for new files".  Maybe that will help.

---

### Post by xouns on 2009-06-30
I have the same problem, and know what it is, not how to fix.

Because Rhythmbox looks for the files at startup, it tries to connect to the windows partition. However, before accessing, this partition is not yet mounted, so it cannot find the first files. Then, I think, it assumes that all the files on that partition are missing, so removes them from the library. After trying to access the partition, it is mounted by the system (it is needed, so mounted) and Rhythmbox later finds all the music files. What I do, is open the music partition trough Places, then open Rhythmbox. Or close Rhythmbox, open the partition, and restart Rhythmbox.

But I have a different problem right now with Rhythmbox: when I start listening to music, it forgets the library, leaving a few random songs and the complete works of the artist I'm listening to. Draging and dropping does not work, only reloading Rhythmbox brings back my library. Any suggestions?

---

### Post by mcduck on 2009-06-30
Two simple solutions.

1. Configure your windows partition to mount at boot time (by adding it to /etc/fstab).

2. Disable automatic library updating in Rhythmbox's preferences.

I'd go for the first option. :)

If you set Rhythmbox to automatically update the library, and the partition where your music files are isn't mounted, there's little else Rhythmbox could do but to assume that those songs aren't available any more and remove them from the library..

---

### Post by timmynana on 2009-08-23
a little advice on /etc/fstab please. MY current one looks like:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=914db875-0279-4947-b182-af65d4c2d66a /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=04de11a7-21d7-410e-b356-8082fdf10f97 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=4be91663-0e88-499c-8583-bc2f33c36c18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I'm looking to add /dev/sda2 partition called 'Files' - ntfs partition. Where would this be added and what extras are needed.

(these are all on usb as there is no internal harddrive)

---

### Post by nortexoid on 2009-09-01
I have exactly this problem even when my partition is mounted! I don't have any obviously problematic settings enabled, such as "Watch my library".

Is it a problem with finding songs of NTFS partitions? What's the deal? I hate Songbird!

---

### Post by starscreamx86 on 2009-09-01
Kinda same thing with me. I import my music from a 3rd hard drive ( storage ) no windows or linux installed what so ever. And every time I open it, I have to re import all my music again.

---

