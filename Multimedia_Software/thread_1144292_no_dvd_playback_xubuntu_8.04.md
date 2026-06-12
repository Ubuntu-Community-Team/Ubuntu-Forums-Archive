---
title: "no dvd playback xubuntu 8.04"
date: 2009-04-30
forum: Multimedia Software
---

### Post by DonaldTrumpsAlterEgo on 2009-04-30
hello I cannot seem to get any dvd's to play.  I have installed all the necessary codecs, using several different methods to no avail.  I ran vlc from the terminal and this is what it spits out

```
wilson@rambo:~$ vlc &
VLC media player 0.8.6e Janus
[1] 7202
wilson@rambo:~$ libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: faild to open/read the DVD
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/dvd
[00000297] vcd access error: no movie tracks found
ioctl(): Input/output error
[00000297] vcdx access error: error reading Info sector (150)
[00000297] access_file access error: file /dev/dvd is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block -150 from disc
[00000307] cdda access error: cannot read sector -150
[00000307] cdda access error: could not read block -149 from disc

```
It seems like an encryption problem, but I have tried everything in the forums and the wiki, but no dice.  If someone could help me that would be great.  By the way the dvd is the pink panther classic cartoon collection.  Thanks in advance.

---

