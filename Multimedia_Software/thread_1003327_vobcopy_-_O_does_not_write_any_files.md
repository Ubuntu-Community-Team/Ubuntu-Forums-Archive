---
title: "vobcopy - O does not write any files"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Frolicsome Otter on 2008-12-06
I've been trying to copy a single vob file with 
vobcopy -O FILENAME.VOB

It creates directories within the current directory like
DVDNAME/VIDEO_TS
So I know it finds the DVD in the source drive, but it doesn't copy any files over.  DVDNAME/VIDEO_TS remains empty.  

I have successfully copied many dvd's with vobcopy -m, but this time it hung on the first .VOB in the main title.  I was able to copy the movie into three files by starting at a point 50 mb past the beginning of the first .VOB file, but I don't get the titles or the original chapters this way.  I'm satisfied with the copy this way for this particular movie, but I would like to learn how copy single .VOB files one at a time.  This would give me more options for dealing with problems in the future.

Has anyone been able to copy .VOB files one at a time with vobcopy?

I'm running Ibex, and I had the same behavior previously with Hardy.
I get the same behavior both with vobcopy-1.1.0 installed with Synaptic, and with vobcopy-1.1.2 that I compiled from tar.gz downloaded from vobcopy.org.  

Thanks in advance for any help.

---

### Post by Frolicsome Otter on 2008-12-19
Hi everyone,

Being still very new to linux and ubuntu, I'm guessing that I've chosen the wrong forum for my question about vobcopy based simply on the fact that no one has responded.  Or perhaps it's something about how I posed my question...  I recognize that everyone helping each other on the forums is giving advice from a sense of community, and I certainly don't feel entitled to an reply to my question.  But if there is a better forum to pose my question about vobcopy, could someone please tell me.  Best wishes.

---

### Post by xc3RnbFO8P on 2008-12-19
Did you try from Terminal:
> sudo vobcopy -O FILENAME.VOB

---

### Post by mc4man on 2008-12-19
I believe the -O option is broken in the versions your trying (at least in 8.04

If you really need this method than use v. 1.02

When you say 'hanging' what do you mean?

Vobcopy can be used on many structured protected titles in the -m mode (with slight edit of source

---

### Post by Frolicsome Otter on 2008-12-19
Thank you both for the suggestions:

1. I tried as sudo, and got the same behavior as without sudo.
bob@Dell2007:~/dvd$ sudo vobcopy -O VTS_07_1.VOB
[sudo] password for bob: 
Vobcopy 1.1.2 - GPL Copyright (c) 2001 - 2007 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

[Info] Path to dvd: /dev/scd0
[Info] Name of the dvd: DVD_NAME
[Info] There are 21 titles on this DVD.
[Info] There are 66 chapters on the dvd.
[Info] Most chapters has title 1 with 16 chapters.

[Info] There are 21 angles on this dvd.

[Info] DVD-name: DVD_NAME
[Info]  Disk free: 21230 MB
[Info]  Vobs size: 7962 MB
[Info] Writing files to this dir: /home/bob/dvd/DVD_NAME/VIDEO_TS/

Then when I check in this directory it is empty.  

2. When I use vobcopy -m, it usually works fine.  With this DVD when it hangs, it simply stops copying.  The percent readout no longer increments and leaving it sit for an hour does nothing.  Even with -v there is no further output like bad sectors.  The -b 50m option copied the movie and lumped all the VOB's into file 2GB each losing the chapters.  I believe the disk is damaged as there is a divot in the inner fifth of the disk, so I would like be able to copy the damaged VOB file starting 50 MB past the beginning, the remaining VOB's and then make an image of the files preserving the chapters.  

I compiled version 1.1.2 from tar file I downloaded from vobcopy.org.  That took a while, as it was the first time I'd compiled anything myself.  I read enough to work my way through the compiling and used checkinstall to install it.  I can then see vobcopy with the synaptic manager.  

It sounds like the -O option may not be functioning properly.  I would love to hear if anyone has successfully used this option.

Thanks in advance for any help you might provide

---

### Post by mc4man on 2008-12-19
I don't see the -O working after 1.02 (which I just tested and works).

Now that you've done it you could build in a few  min. and see, though ripping a disk a file at a time to rebuild  will prove to be time consuming.

If it was read errors you should see "Warn] Had to skip 0 blocks[!  [Warn] Had to skip 1 blocks!" ect.

By default vobcopy attempts 9 read retries so normally the same warning would be repeated up to 9 times or until read was successful.
( in the case of structure protection the sectors can't be read so you limit the try's to 1 to save time (*a lot*.

If you wanted you could try dumping an encrypted iso with dvdisaster, if it gets past the damage and completes then try playing the iso and see if the title is still functional as far as opening and navigation.

You'd need to be able to at least partially open the disk in a player to authenticate the drive for dvdisaster to work. 

If so mount the iso and re rip with vobcopy (1 read try with -F 16 option) to get a decrypted VIDEO_TS

---

### Post by andrew.46 on 2008-12-24
-------------------Removed my own post-----------------

---

### Post by Frolicsome Otter on 2008-12-31
Thank you mc4man.  I installed version 1.0.2 and yes indeed it does copy only one VOB file at a time with -O.  It does not at the same time offset with -b, like I hoped.  I appreciate knowing that versions after 1.0.2 do not function with -O.  That saves me from questioning whether I'm using it correctly.  I think I'll let the problem sit for a while now.  Thanks to everyone who has checked into this thread.
Cheers.

---

### Post by Frolicsome Otter on 2009-03-03
> **mc4man said:**
> I believe the -O option is broken in the versions your trying (at least in 8.04

If you really need this method than use v. 1.02

When you say 'hanging' what do you mean?

Vobcopy can be used on many structured protected titles in the -m mode (with slight edit of source

Hi mc4man,

I've learned enough now to be interested in modifying the source of vobcopy so that it can handle many structure protected dvd's.  

How can I find out about that modification?

Thanks,
Otter

---

### Post by mc4man on 2009-03-03
> so that it can handle
You may or may not have have 'mis understood' that comment, by handle I mean rip in a timely fashion.
In most cases the sp will have to be manually 'repaired' to do anything with the rip.

For me it's more of an interest in sp and how it's implemented, and the challenge to repair myself rather than any need to make backups.

For putting titles on a hdd for playback I just use the dvdisaster method (which is 'clean' in that there is no reason to remove css or sp protections for playback from an .iso, nor any 'circumvention' of such protections

There would be some caveats to using vobcopy on sp titles
Some can't be ripped at all (will be immediately obvious - hundreds of Warn... scrolling by very fast - abort and forget

Some have too many unreadable sectors to be practicable time wise (over 5000 or so

Some have large #'s of bogus titlesets, in these cases predetermine where they start and when you reach them abort and work with what you have. (Ex titlesets 1-9 are good, 10 - whatever are bad, stop after 9

The in's and out's of fixing after rip aren't really appropriate for this forum, you would need a ifo editor and a vob editor. (PgcEdit v. 0.8.6, linux or win ver. in wine, Vobblanker


Anyway
unpack vobcopy source
find vobcopy.c and open in text editor
Using the search tab -> find, enter 9 and press enter
close out the find box and then Ctrl+g  till you see this set of lines
> while( ( blocks = DVDReadBlocks( dvd_file, i, file_block_count, bufferin ) ) <= 0 && tries < 10 )
                        {
                          if( tries == 9 )

Change the 9 to 1 and save
Then build and install

Also in your rip command use this
-F 16
Ex. 
vobcopy -v -m -F 16 

This will allow you to read/skip in blocks of 16 sectors instead of 1 by 1
So between the 9 tries to 1 try and 1 sector to 16 you can save a huge amount of time

---

### Post by Frolicsome Otter on 2009-03-05
Thanks mc4man,

Yes, this worked though it still took over seven hours for vopbcopy to rip the disk.  There were over 4200 corrupted sectors in four different files.  I'm not sure exactly how long as I'd gone to bed before it finished.  Even so, I've got a good quality backup of this dvd now.  

Rereading this thread I see that this was described above, I just didn't understand at the time.  In the future, it sounds like I should just make a copy of the disk with dvdisaster since I don't really need to rip it.

Thanks again.
Otter

---

### Post by mc4man on 2009-03-05
> till took over seven hours
As noted some aren't worth the time, (the other factor is that some drives can recover read speed after a section of read errors, others though will default to a min. read speed.

dvdisaster will read a bit quicker, though again the time involved isn't worth it for some sp's. (more a means to dump with sp intact to look at in those cases.

Many sp's these days use a very small # of unreadable sectors. using borked .ifo's and bogus titlesets, in these cases dvdisaster is ideal, when playing back from an .iso the sp is a non factor (the same as playing the disk on the pc or standalone

Many times k9copy is good for titles with large #'s of bad sectors, some # in the tens of thousands. (set target size above disc size and it won't shrink (trancode

(  for dvdisaster to 'read' a comm. disk you need to authenticate the drive first. Start the disc in a player, pause, then open dvdisaster and close the player.
Note on 8.10 settings don't take hold on dvdisaster, none are needed from default, but there will be a pop up about rs01, choose no and disable (the pop up will keep coming back on 8.10, on 8.04 the 'disable' is respected

---

