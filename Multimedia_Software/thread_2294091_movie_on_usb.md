---
title: "movie on usb"
date: 2015-09-09
forum: Multimedia Software
---

### Post by inxs1111 on 2015-09-09
hi i download a movie and put it on usb stick on windows and plug into tv usb slot and the movies there ready to play,but when i down loaded a movie from ubuntu mate and put it on usb and put into tv no movie file shows up to play?could you help me please because this is the only reason stoping me going full time with linux thanks

---

### Post by QIII on 2015-09-09
Where did you download the movie from?

---

### Post by ajgreeny on 2015-09-09
Most TVs need mpg2 movies and nothing else will be viewable.

If you have downloaded another file-type of movie you will probably have to convert it in command line with avconv or ffmpeg, or use a GUI app like winff, or vlc, which can convert video files, or handbrake.

There are many options for you, but tell us in more detail what you've done so far.

---

### Post by Rob Sayer on 2015-09-12
From what I see in the OP there's nothing about this problem specific to linux.  You dl'ed a video, put it on a usb, and plugged it into the tv.  I suspect the TV may not recognize the format.

First, look at the docs for the tv and see what format it recognizes.  You can guess the video format of a file to some extent from the file extension but not reliably.

Second, install mediainfo-gui.  Then open the video file with that.  It'll tell you what format/codec is there.  Mediainfo is an essential app for media users IMO.

---

### Post by Bucky Ball on 2015-09-12
Most systems also want the partitions in a particular filesystem. If you are using the native linux EXT filesystem for your partitions on the USB they almost definitely wouldn't be recognised. I think most recommend the old FAT format.

---

### Post by coldraven on 2015-09-13
You also need to check the size of the downloaded file. USB sticks are generally formatted to FAT32 which cannot save files bigger than 4GB.
From Wikipedia:
[https://en.wikipedia.org/wiki/Fat32#FAT32](https://en.wikipedia.org/wiki/Fat32#FAT32)
> The maximum possible size for a file on a FAT32 volume is 4 GB minus 1 byte or 4,294,967,295 (2[SUP]32[/SUP] &#8722; 1)  bytes. This limit is a consequence of the file length entry in the  directory table and would also affect huge FAT16 partitions with a  sufficient sector size.[SUP][[1]]("https://en.wikipedia.org/wiki/Fat32#cite_note-GB4-1")[/SUP] Large video files, DVD images and databases easily exceed this limit.

If you want to save files larger than that and be able to use the stick in both Windows and Linux then format it to NTFS.
Use gparted to do this, make sure that you **select the correct drive** from the drop-down menu in the top right corner **or you will erase your hard drive!**

---

