---
title: "best backup strategy for media files?"
date: 2019-11-29
forum: Multimedia Software
---

### Post by meobeobongbay92 on 2019-11-29
[COLOR=#000000][INDENT]Is there something other than just a direct copy or rsync for a boat load of media?


I'm currently at 1.4tb of media, with growth coming. The existing data never changes, just gets added to. What is the idea way to back this up?
[/INDENT]
[/COLOR]

---

### Post by Tadaen_Sylvermane on 2019-11-29
a proper backup for media is a copy somewhere. that can be cumbersome though imo for media if you regularly add to it. while not a true backup, i like the way snapraid works. is easy to work with and works on the existing filesystems. can use any size disks, or mixture of disks. only rule is the parity drive(s) need to be the same size or bigger than the biggest data drive you have. single parity is basically raid 5 without the higher i/o of striping. the more disks you have for parity (up to 6 I believe) is how many disks you can have die at a single time and not lose anything. totally worthless though if the data is constantly changing. i love it for my media storage. regular scrubs do bit rot checking as well. combined with mergerfs it is a nice solution for media.

I did not write this. [https://blog.linuxserver.io/2016/02/02/the-perfect-media-server-2016/](https://blog.linuxserver.io/2016/02/02/the-perfect-media-server-2016/)

in my current setup of 1.6tb of media i'm running a 2tb and 250gb sata for storage with a 2tb usb drive for parity. i don't worry about the parity being on usb as it is only mounted with autofs as needed. scrubs and syncs only.

---

### Post by speartip on 2019-12-06
I know you say "other than rsync" but IMO for that amount of media, rsync is your best bet. After the initial full backup, it will only add new data & changed files.
I've tried all kinds of Backup utilities. Backintime, Luckybackup, Areca etc... But always keep coming back to using rsync from the command line for it's ease & accuracy.

---

### Post by TheFu on 2019-12-06
For media that doesn't get edited, I use rsync.  I don't know of any shortcut to having 2 copies of the data.  RAID is never a backup.  

If there aren't 2 copies, it isn't a backup.
If it cannot be restored, it isn't a backup.

There might be better solutions, but none cross my mind.  This only applies to media storage, for OSes, configs, documents, and other files that change over time, there most definitely ARE better solutions than rsync.

To fight bit-rot, which I believe is 100% real, I force copies to be rewritten.  The source files have bit-rot and my solution to monitor that is using par2. My goal isn't to handle use corruption, just to know what is corrupted so I can re-rip from the source disc.
```
$ more par2-create-1_percent 
#!/bin/sh
for filename in "$@"; do
   # Create a 1% recovery data with blocksize of 300KB
   nice /usr/bin/par2   create    -s307200     -r1     "$filename"
done
```
No spaces allowed in filenames.  Shell globbing is fine for the input filenames. 

For a 1.5G video, the par2 files are about 15MB.  Small corruption issues easily discovered and fixed.  Big ones, discovered. ;)
```
par2 v some-file.mkv.par2
....
All files are correct, repair is not required.
```
Happiness. I keep the par2 files with the media. They are backed up.

---

