---
title: "devede - failed to create bin/cue file"
date: 2008-04-24
forum: Multimedia Software
---

### Post by sundar261 on 2008-04-24
I am trying to create a VCD out of my .avi file.  I am using getting an error message "failed to create bin/cue file".  Possible reason suggested was that there is no disk space available.  But I have around 20GB of free space. 

Any help on this issue is appreciated.

---

### Post by darkerlink on 2008-04-26
I have this same problem, I have 90 gigs free but I get that error trying to make a video dvd. I will keep this thread bookmarks for future replies.

EDIT: I am using an external hd to store the iso. It is an NTFS file system.

---

### Post by ITAndrew on 2008-04-26
Possibly a permissions issue, do you know where its trying to place the newly created files.

I know this is usually a no-no, but have you tried running the application as root to see if the same issue occurs. If it works under root, that you can almost be sure that it either cannot create a new folder where it would like to to place the new files, or its trying to place the newly created files in another location besides your "Home Folder"

---

### Post by darkerlink on 2008-04-27
No, i dont think its a permission issue as I have made iso's from Devede before and it just worked now. The problem it seems that sometimes, I will get the error and sometimes I won't. It's frustrating in that it takes me over 2 hours to create a ready to burn iso using devede and it's time wasted when it fails. Maybe this is a software issue?

---

### Post by ITAndrew on 2008-04-27
If thats the case and this is effecting more than one user, feel free to file a bug report to get some attention to it.

---

### Post by judas3000gold on 2009-01-25
this is the cmdline output

++ WARN: initializing libvcd 0.7.23 [linux-gnu/i486]
++ WARN:  
++ WARN:  this is the Beta development branch!
++ WARN:  use only if you know what you are doing
++ WARN:  see [http://www.hvrlab.org/~hvr/vcdimager/](http://www.hvrlab.org/~hvr/vcdimager/) for more information
++ WARN:  
++ WARN: mpeg stream contained no scan information (user) data
++ WARN: mpeg stream contained no scan information (user) data
**ERROR: image too big (1278858 sectors > 449850 sectors)

maybe it's still trying to create the file in /tmp (there is not enought space) and not in my /home folder (there is enough space)

---

### Post by judas3000gold on 2009-01-25
the point is, devede uses vcdimager to make the iso (which also throws the error)

then i found this [http://osdir.com/ml/gnu.vcdimager.bugs/2003-06/msg00001.html](http://osdir.com/ml/gnu.vcdimager.bugs/2003-06/msg00001.html)


> Sorry for the delay. Herbert Valerio Riedel has this to comment:

well... there's a general issue with sector addressing; it's a
limitation in the format:

sectors aren't represented by simple (linear) 32bit values in the vcd
structs and the cdrom sector headers, but instead msf-style bcd-coding
is used, leading to an upper limit of ~450k sectors (== 100 minutes)

the other issue is, that vcd's use cdrom mode2form2 sectors, which are
able to carry 2324bytes of payload together with a few bytes of
subheader; but afaik the DVD media allows only for 2048 byte
payload/sector without any provision for subheaders... so it simply
makes no sense to write a vcd image to dvd media....

one should really just use the dvd-v format for video-carrying dvd's...
dvd players already have a hard time recognizing vcd's on CD-R's...

tl:dr use dvd format cause svcd is not able to do it

---

