---
title: "Damaged jpg files"
date: 2015-05-24
forum: Multimedia Software
---

### Post by bill-lancaster on 2015-05-24
I have a large number of jpg files going back to 1999.
Over time I have noticed that some of these have become corrupt in some way.
By corrupt I mean that:-
a)  Gimp can't open them ("Not a JPEG file: starts with 0x1c 0xe6" for example).
b)  exif from the command line says "Corrupt data, The data provided does not follow the specification.  ExifLoader: The data supplied does not seem to contain EXIF data.

These files were once readable.

Have tried 'recoverjpeg' to no avail.

Having looked at a large number of articles I haven't found much to help me so I would appreciate any advice.

---

### Post by TheFu on 2015-05-24
Bitrot is a real thing. Keep backups - multiple versions.
Might want to keep parity files too, which help correct corruption. I use **par2** for this and it has seen storage failures and been able to correct it, provided it isn't too bad.
And of course, don't use new file systems that haven't been completely, 100%, tested for many years. I didn't switch off JFS to EXT4 until last year. 

Our data is much more important than hardware it runs on. 

Oh - sorry, I don't have any idea how to fix broken image files.  Good backups, parity files, and testing that the files have NOT been corrupted from time to time is necessary.
```

#!/bin/sh
for filename in "$@"; do
   # Create a 10% recovery data with blocksize of 300KB
   nice par2 create -s307200 -r10 "$filename"
done
```
A simple script to help create the parity files. Filenames cannot have odd characters or spaces or this script will fail.
Good luck!

---

### Post by mörgæs on 2015-05-24
I've had a similar problem. When opening old .jpg's they are sometimes cut off horizontally, upper part is fine but the lower is garbage. 

Is .jpg more fragile than other file formats?

---

### Post by TheFu on 2015-05-24
I think there are many different "jpg" formats and different programs, especially pre-2005, didn't always follow the standards.  I'd try using convert from the imagemagick suite of tools to move the most important files to png. That file has a strong standard.

My photo organization technique: [http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival)

Of course, I would be completely wrong too.

---

### Post by bill-lancaster on 2015-05-24
Thanks TheFu you haven't solved my problem but I like your advice!
An analysis of the problem photos shows that the oldest is 2006 - I converted to Ubuntu in 2008.
I'll probably convert to png files to head off future problems.
Still, it seems to me that most of the data is probably still present in the broken files so its a pity that even a partial recovery doesn't seem possible.
Thanks for all the ideas.

---

### Post by SeijiSensei on 2015-05-24
Have you tried something like [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec")?

---

