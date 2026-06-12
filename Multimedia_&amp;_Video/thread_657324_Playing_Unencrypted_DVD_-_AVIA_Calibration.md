---
title: "Playing Unencrypted DVD - AVIA Calibration"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by skskarda on 2008-01-03
I can play DVD's with no issue on my Gutsy Ubuntu PC through Mplayer, Xine, or MythTV.   For the life of me, I can't figure out how to get an Avia DVD from Ovation to play.  This DVD by Ovation is used for calibrating video and sound.  According to the FAQ on Ovation website, this DVD does not have any copy right protection (to ensure purse quality signals).

I managed to get the FBI notice to play on one of my Ubuntu machines but after that it froze up.  Most of the time, I get a data error.   I have also seen a decoder problem.  I tried dvd-rip and it said there was no TOC.

I would really appreciate any ideas.  Thanks!!

---

### Post by yabbies on 2008-01-03
open the dvd files is there an Audio_ts and Video_ts directories?
what's in each of those folders?

what types of files are on the disc?
not real familiar with calibration discs

---

### Post by skskarda on 2008-01-03
Thanks for the reply!

It has the normal Audio_ts and Video_ts directories that you'd expect to see.   I have attached a screenshot.

I have also attached screenshots of the errors I get back from xine.  I should note that I do have libdvdcss installed although I am not sure that it is necessary for this disk.

The calibration dvd is for setting up the correct color and sound in a home theater.  [www.ovationmultimedia.com/avia.html](www.ovationmultimedia.com/avia.html)
[IMG]http://i227.photobucket.com/albums/dd106/skskarda/Screenshot.png[/IMG]
[IMG]http://i227.photobucket.com/albums/dd106/skskarda/Screenshot-1.png[/IMG]
[IMG]http://i227.photobucket.com/albums/dd106/skskarda/Screenshot-2.png[/IMG]

---

### Post by yabbies on 2008-01-03
just for a giggle have you tried playing  it with vlc?

I'm curious as to why all of sudden xine is not recognizing your dvd
MRL stands for Media Resource Locater

---

### Post by skskarda on 2008-01-03
I tried that also.  Here is the result:

VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: AVIA
libdvdnav: DVD Serial Number: 16607a13
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/steve/.dvdnav/AVIA.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: no movie tracks found
ioctl(): No medium found
[00000297] vcdx access error: error reading Info sector (150)
[00000297] access_file access error: file /dev/scd0 is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc
[00000307] cdda access error: cannot read sector 0
[00000307] cdda access error: could not read block 1 from disc
[00000307] cdda access error: cannot read sector 1
[00000307] cdda access error: could not read block 2 from disc

and this goes on and on indefinitely

---

### Post by skskarda on 2008-01-03
Hold on a minute.  I decided to try a normal dvd with vlc but it wouldn't eject so I rebooted.  Lo and behold vlc plays the DVD!   Xine and mythtv don't work but that is OK.  I'll just use VLC. 

Thanks for the idea!!!!!!!

---

### Post by mc4man on 2008-01-03
The players your trying  are using libdvdread and libdvdnav to access and navigate the disc.
While hardly ever used there are ways to structure a dvd that will result (maybe or maybe not intentional ) in the inability of "free" software players to playback. I wouldn't doubt the disk would work in windows with powerdvd, windvd, ect. It's very possible lindvd could play it. One possibility is to rip the disk to hdd and use a program that may correct the structure, if indeed that's the issue.

---

