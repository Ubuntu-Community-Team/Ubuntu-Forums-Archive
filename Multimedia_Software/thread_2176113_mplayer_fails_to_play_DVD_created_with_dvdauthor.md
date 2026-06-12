---
title: "mplayer fails to play DVD created with dvdauthor"
date: 2013-09-22
forum: Multimedia Software
---

### Post by George Heine on 2013-09-22
Hello -

Using Ubuntu 12.04 with MPlayer svn r34540 (Ubuntu), built with gcc-4.6.
It works on all DVDs I've ever tried, with one exception.  Here's the output from trying to play that disk:

```
$ mplayer dvd://1

mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.BU.
Can't open VMG info!
No stream found to handle url dvd://1

```

However, entering something like
```
$ mplayer /media//VolumeName/video_ts/vts_01_0.vob

```
 plays without complaiint.  Of course, mplayer doesn't know where the titles are, but at least it finds the videos.

Some other factors that might be relevant:

1) The disk plays on a Sony DVP-SR200P but not on a Toshiba D-VR7KC2.
2) Tried making a second copy of the disk, same problem.  Tried  loop-mounting the iso image from which the dvd was burnt; same problem.
3) This is a homemade dvd, created with dvdauthor.  Don't claim to be an expert, but have done the process a couple of dozen times and never had a problem until now.  Here's what the xml file looks like:
```
<dvdauthor dest="DVD_Image">
<vmgm>
</vmgm>
<titleset>
  <menus>
    <video  format="ntsc"/>
    <pgc entry="root">
      <vob file="menu5.mpg" />
        <button>jump title 1;</button>
        <button>jump title 2;</button>
        <button>jump title 3;</button>
        <button>jump title 4;</button>
        <button>jump title 5;</button>
        <button>jump title 6;</button>
    </pgc>
  </menus>
  <titles>
    <video  format="ntsc" />
    <pgc>
      <vob file="mpg/video1.mpg" />
      <post>call menu;</post>
    </pgc>
```
Repeat for video2,3,4,and 5, then
  ```
  <pgc>
      <vob file="mpg/video1.mpg" />
      <vob file="mpg/video2.mpg" />
      <vob file="mpg/video3.mpg" />
      <vob file="mpg/video4.mpg" />
      <vob file="mpg/video5.mpg" />
      <post>call menu;</post>
    </pgc>
  </titles>
</titleset>
</dvdauthor>

```

4) I burned another disk with the same five videos, but with the "play all" option as the first, rather than the last, menu choice.  That disk works fine.

NOTE mplayer does not display the menus and allow me to make a selection, but will worry about that later.  The man pages say "your mileage may vary" on this one.

---

