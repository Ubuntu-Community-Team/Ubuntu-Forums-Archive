---
title: "Can't play (or read) audio CD (Dapper, HP s7310n)"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by beowabbit on 2006-11-03
Hi.  I have an HP Pavilion Slimline s7310n PC with a "LightScribe" DVD-writer (which identifies itself in /proc/ide/ide0/hda/model as an "HP DVD Writer 740b").  The machines boot drive is SATA, so the DVD-RW shows up as /dev/hda.  I'm running Dapper Drake, with current updates.  /dev/hda is mode 660, owner root, group cdrom, and I am in group cdrom.  (I've also tried running cdparanoia and/or CD players as root, and opening up permisssions on /dev/hda.)

I can't play audio CDs (with gnome-cd, rhythmbox, or xmms), and I can't read data off of audio CDs with cdparanoia.  I've tried lots of CDs; they all have this problem.  gnome-cd, for instance, produces the following output:

** (gnome-cd:25289): WARNING **: Error opening CD

** (gnome-cd:25289): WARNING **: ERROR: Could not open CD device for reading.

** (gnome-cd:25289): WARNING **: ERROR: Could not open CD device for reading.

(and keeps repeating the last line).  dmesg has lots of lines saying

cdrom: open failed.

and nothing else obviously relevant (although I don't still have the boot-time messages about the device).

Data CDs mount fine.  Unencrypted DVDs mount and play fine.  I only have trouble with audio CDs.

Does anybody know what might be wrong here, and/or how to fix it?  I'm dyin' without my music!

PS -- In case it makes a difference, I'm using fvwm2 (but from a default Ubuntu install with fvwm2 installed afterwards, rather than an Xubuntu install).

---

### Post by beowabbit on 2006-11-16
Well, this seems to have been a hardware problem.  I actually found a couple of audio CDs that worked in the DVD-R drive that shipped in my S7310n, but only one in about ten or twenty would work.  If a disc worked, it would work fine -- all tracks would play, and I could extract audio.  Each disk that didn't work would exhibit consistent weird behaviour (some disks would cause the head to seek over and over, some disks would produce an error quickly, some slowly, but the same disk would always exhibit the same behaviour).  Data CDs consistently worked fine, though.

I swapped the drive that came with the s7310n (Model CGA-4166B by Hitachi-LG Data Storage, Inc., according to the sticker on it) with a no-name DVD-RW I had bought for another machine some time ago, and audio CDs work fine in the replacement drive.

I don't know if the problem is with the particular drive I got, or if that model is generally flaky about reading audio CDs.  I'd suspect I just happened to get a bad drive.

---

### Post by eyeonus on 2007-01-17
I'm having a similar problem on my computer whhen I try to mount an audio CDs- data CDs cause no problems- except that it looks like it's a software issue for me. Whenever I try to mount an audio CD, I get the following error:

mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg produces this:

[4372151.667000] hdd: command error: status=0x51 { DriveReady SeekComplete Error }
[4372151.667000] hdd: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4372151.667000] ide: failed opcode was: unknown
[4372151.667000] end_request: I/O error, dev hdd, sector 64
[4372151.669000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16

And the relevant entry in '/etc/fstab':
# <file system> <mount point>   <type>         <options>       <dump>  <pass>
    /dev/hdd        /media/cdrom0   udf,iso9660    rw,user           0             0


One interesting thing is, some programs, like Sound Juicer, are able to read the disc and even rip it without any apparent problems, even the mount command fails.

Any help would be appreciated.

---

### Post by Antonlacon on 2007-01-18
Audio CD's aren't mounted, don't try.  Just put it in and play.

---

