---
title: "suddenly unable to play dvd"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by barna on 2007-07-10
Hi, 
I could play DVDs without any problem for a long time (Feisty). Suddenly, kaffeine and even gmplayer refuses to play them. Before the usual questions if libdvdcss2 or other libraries are installed: yes, they are. I could play encrypted DVDs as well. 

Kaffeine for example issues these messages:

xine Message:
The source can't be read. 
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (///dev/hdc)

xine Error:
No plugin found to handle this resource (dvd:///dev/hdc)

However, if I mount the DVD under /media/cdrom, for example, then I manage to play it via:
kaffeine dvd:///media/cdrom

Does anybody have an idea what could have happened suddenly?

Thanks
Daniel

---

### Post by barna on 2007-07-10
Gettint closer to the solution...
Recently I tried to play DVDs created by myself (kmediafactory), which failed. The dvd directory was created on an external harddisk, with vfat filesystem. Since this filesystem does not distinguish upper- and lowercase letters, all files seem to be written to the dvd with lowercase letters. Kaffeine also reports these errors:

libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO

For 'official' DVDs (filenames in capital) it works as before (kaffeine dvd://)

So the problem is now shifted to this: how to create a valid DVD (uppercase filenames) with kmediafactory+dvdauthor if I have no space on my local harddisk (ext2 filesystem), but only on an external harddisk with vfat filesystem. Any idea?

---

### Post by david_2001 on 2007-07-10
Some simple consistency checks:
[LIST=1]
[*]In kaffeine, select Settings | xine Engine Parameters, go to media Options and check the dvd.device setting.  (It will be /dev/dvd by default.)
[*]Check that the dvd.device exists.  If it was /dev/dvd then it should be a symbolic link to the actual dvd device, e.g. /dev/hdc.
> david@darkstar:~$ ls -l /dev/dvd
lrwxrwxrwx 1 root root 3 2007-07-10 19:19 /dev/dvd -> hdc
[*]Check that the dvd device established above has a line in /etc/fstab.  For /dev/hdc expect something like:
```
/dev/hdc        /media/cdrom0   udf,iso9660  ro,noauto,user,exec,unhide    0       0
```
[/LIST]
EDIT: I answered the first version of the question!

---

### Post by barna on 2007-07-11
Hi,
Thanks. I checked all these items, they are ok. Also, I can play an 'official' DVD without any problem. The problem seems to be with dvds created by me (kmediafactory+dvdauthor).

I tried to overcome the uppercase/lowercase problem by producing the DVD directory on the ext2 filesystem, where (as expected) every file has now uppercase names. Even this did not help. When trying to play this directory with kaffeine (that is, without burning a DVD) I get the same error messages as before, so I am pretty sure the problem is with kmediafactory+dvdauthor. And kaffeine is still complaining about
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
although this file is there in the VIDEO_TS subdirectory. 

...ooops, the file is there, but it is empty! Strange... I had no problems before with kmediafactory+dvdauthor, they produced usable DVDs. 
May the reason be that I have too many (above 30) small films, each with an entry in the title menu?
kmediafactory+dvdauthor claimed it succeeded, but looking into the log with more detail, I found entries like that:

[mpeg2video @ 0xb7e6f1a4] warning: first frame is no keyframe
[mpeg2video @ 0xb7e6f1a4] ac-tex damaged at 43 31
[mpeg2video @ 0xb7e6f1a4] invalid mb type in P Frame at 18 33
[mpeg2video @ 0xb7e6f1a4] mb incr damaged
[mpeg2video @ 0xb7e6f1a4] invalid cbp at 32 35

all the films were transformed to dvd format beforehand:
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:acodec=ac3:abitrate=192:aspect=4/3 -ofps 25


Daniel

---

### Post by barna on 2007-07-11
Getting quite fed up with all these programs...

The uppercase/lowercase thing was not the problem, seemingly: I had another DVD created by kmediafactory+dvdauthor, which had a non-empty VIDEO_TS.IFO file. I have renamed all the files to uppercase, and burnt them to a DVD. 
kaffeine dvd://
or
kaffeine dvd:///dev/hdc (this is my dvd rom)
gives the usual error messages, and it prints to the stderr:
libdvdnav: Using dvdnav version 1.1.4 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title:
libdvdnav: DVD Serial Number:  m
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/barna/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO

When I mount the dvd:
mount /dev/hdc /media/cdrom
and try to play it from the mounted directory:
kaffeine dvd:///media/cdrom
then everything works fine. What the hell is this?

Trying to play it from vlc: there is an endless stream of error messages:
[00000309] cdda access error: could not read block 147 from disc
[00000309] cdda access error: cannot read sector 147
etc


Thanks

---

### Post by jamb on 2007-07-12
I just decided to give Feisty a try on the desktop with a fresh install yesterday (but I still like the stability of Dapper on the server). 

I'm running Kubuntu, and in the beginning all was real nice, until I tried to play a DVD in Kaffein. The DVD was non-encoded, thus this is not necessary a pure codec-plugins problem.  

Basically I had the same xine error : 'No plugin found to handle this resource' (DVD:///dev/hdb).'

The sym link '/dev/dvd --> hdb and and fstab-file looks ok. Settings in xine as well. Opening the DVD disk in Konqueror shows an empty disk and 'media/cdrom0' (In the address field).

---

### Post by jamb on 2007-07-12
Comparison with Debian Etch 4.0
-------------------------------------------------
Since I have Debian Etch on another partition, I tried to play the same DVD with Kaffein (and it worked fine). 
Opening the DVD disk in Konqueror shows the disk content and 'media:/hdb' (In the address field).

---

