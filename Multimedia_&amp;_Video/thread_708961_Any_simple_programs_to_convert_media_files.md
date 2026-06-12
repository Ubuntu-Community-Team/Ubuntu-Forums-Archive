---
title: "Any simple programs to convert media files?"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by Danno2468 on 2008-02-26
i am trying to put music and video on my phone.  it is a nokia phone that takes,3gp,mp4 and rm file types for videos, and it takes AAC, AAC+, eAAC+, Mp3and wma file types for music.  converting the vidoe's is the main problem as my vid's are in WMV, and Avi files.  most of my music is in mp3, but maybe convert it to change size of music.(not really a problem at all, but a nice bonus if possible).  any help would be greatly appreciated.

---

### Post by em3raldxiii on 2008-02-27
There are a number of great applications to do what you are looking for, one that I use a LOT is called AVIDEMUX.  It's in the repositories (not sure which one specifically), but you should be able to install it with:

```
sudo aptitude install avidemux
```

It's a pretty robust program and probably does more than what you need, but there are a number of good howtos and tutorials on the 'net for avidemux.

Also, there are a number of nautilus scripts that you can install that allow you to right-click on files and just select what you want to convert them to.  Here's a website with some great scripts:  [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

It should have pretty simple instructions about how to install them.  Many of them will require that you have specific applications installed such as mplayer, ffmpeg, and others.

Good luck!

---

### Post by disturbedite on 2008-02-27
i second avidemux.  its really great.

---

### Post by cozmicharlie on 2008-02-27
> **Danno2468 said:**
> i am trying to put music and video on my phone.  it is a nokia phone that takes,3gp,mp4 and rm file types for videos, and it takes AAC, AAC+, eAAC+, Mp3and wma file types for music.  converting the video's is the main problem as my vid's are in WMV, and Avi files.  most of my music is in mp3, but maybe convert it to change size of music.(not really a problem at all, but a nice bonus if possible).  any help would be greatly appreciated.

Music
For your phone this is the best solution for aac.
[http://ubuntuforums.org/showthread.php?t=631835](http://ubuntuforums.org/showthread.php?t=631835)

It is a command line program but you can write a script that makes it easy.  It is explained in the thread.  

PACPL is another very good decoder/encoder ([http://pacpl.sourceforge.net/](http://pacpl.sourceforge.net/)).  It will work for all you r music files.  Though aacplusenc is better for aac.  

For basic music decoding soundconverter works fine.  

Video
PACPL also encodes a large number of video formats.  Another good package is winff - biggmatt.com/winff

Also, make sure and install the codecs - [https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067](https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067)

These threads have lots of good info 
[http://ubuntuforums.org/showthread.php?t=529759&highlight=kino](http://ubuntuforums.org/showthread.php?t=529759&highlight=kino)
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Enjoy

---

### Post by Danno2468 on 2008-02-27
I knew it was possible!  thanks works like a charm!

---

