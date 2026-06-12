---
title: "? Home Movies onto DVD so they Play on my DVD player"
date: 2010-08-13
forum: Multimedia Software
---

### Post by Bushcraft Bill on 2010-08-13
I am very impressed with Ubuntu but with my lack of knowledge I am having trouble trying to put my home movies onto a DVD so that I can watch it on my DVD player I have tried using pitivi video editor to put my home videos together but then trying to save them to a DVD is were I have the problems am I using the wrong software if not what could I be doing wrong or is their an option/settings I am not finding?

---

### Post by LuridCinema on 2010-08-13
save them as mpeg2, then drag & drop them onto DVDstyler should do it easy. DVDstyler is in the Ubuntu Software Center

I might suggest Openshot for video editing.. It is fairly easy to use and has a lot of features & support

---

### Post by JBAlaska on 2010-08-13
If you just need to transcode them to DVD. **DeVeDe** is the easiest I've found.

For a nice NLE try Avidemux.

There both in the repo's, but a newer version of DeVeDe with 2-pass encoding is available for download [Here](http://www.rastersoft.com/programas/devede.html#download_section)

---

### Post by Bushcraft Bill on 2010-08-14
Thanks I will try those out and see how that goes for me...

---

### Post by Bushcraft Bill on 2010-08-14
I did something right got something burnt onto a DVD to play on the home dvd player and it works yee haa.....

---

### Post by Fatjoint on 2010-08-14
What I like to do is use DVDAuthor and FFMPEG.

Use FFMPEG to turn your movie into a mpeg2 file, then use DVDAuthor to create a DVD file-structure.




examples:

ffmpeg -ab 64k -sameq -target dvd-ntsc -aspect 16:9 -i somevideo.avi output.mpg

That transcodes it into a mpeg2 format with AC3 audio.

Taking your newly created file you use DVDAuthor:

dvdauthor -o /dvd output.mpg

dvdauthor -o /dvd -T

The first command transforms the movie into vob files in a dvd structured directory.  The second command creates a title structure within the directory for your dvd player to understand.  

Burn the contents of the /dvd directory onto a DVD and that's it!

You can do a whole lot more with dvdauthor and ffmpeg if you research it, but this is the bare bone cut and dry way of taking a single movie file and making it play on a dvd player.

---

### Post by GrouchyGaijin on 2010-10-25
I've been trying to burn a DVD of home movies with no luck.
I tried burning in Brasero and also making an ISO with DeVeDe then burning with Nero Linux.
In each case the burning seems to freeze then after quite a long time resumes only to either crash at the end or eject with an unusable disk.

I've tried using both mpeg files and avi files.

I gave up and booted into Windows to burn the disk with Nero.

Ubuntu reports my DVD drive as:

description:	DVD writer
product:	DVD+-RW DS-8W1P
vendor:	PBDS
physical id:	
0.0.0
bus info:	
scsi@0:0.0.0
logical name:	
/dev/cdrom
logical name:	
/dev/cdrw
logical name:	
/dev/dvd
logical name:	
/dev/dvdrw
logical name:	
/dev/scd0
logical name:	
/dev/sr0
version:	BD1B
capabilities:	removable audio cd-r cd-rw dvd dvd-r
configuration:	
ansiversion	=	5

Any ideas on what I should do to fix this?

---

