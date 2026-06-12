---
title: "Batch Rename Photos to Creation Date in Meta Info? Please help."
date: 2009-07-05
forum: Multimedia Software
---

### Post by Eli Turk on 2009-07-05
How can I rename multiple photos to their individual creation dates that are in their individual meta infos? I would like to know of a program (GUI preferably) that can rename multiple photos to the creation date in the meta data.

I know that Gwenview, with the KIPI plugin, can (under *Plugins > Batch Processing > Rename Images*) batch rename all the photos in one folder to the **last "Modified" date** (to see what I mean, right click a photo, click "Properties", look under the "General" tab and you have "Modified". Or just look at the first snap-shot attachment in this post). But, the problem is that the **last "Modified" date** and the **"Creation Date"** is often different.

I need the filename to be the "creation date" (which can be found in the photo properties under the "Meta Info" tab). Because, many of the photos have been recently modified, so the date in the filename will be incorrect if I use Gwenview.

So, for example, if the last "Modified" date is "2009-04-19" and the "Creation Date" is "2009-03-27" then I want the filename to be like this "2009-03-27_01.jpg". (NOTE: the "_01" at the end is just the sequence number. So the first photo to be converted will be *_01.jpg, the second *_02.jpg, etc.)

I have attached two screen shots of the photo properties showing what I need.

Thank you very much for taking the time to read this and for any help you can give. It is greatly appreciated!

---

### Post by kaibob on 2009-07-05
> **Eli Turk said:**
> How can I rename multiple photos to their individual creation dates that are in their individual meta infos? I would like to know of a program (GUI preferably) that can rename multiple photos to the creation date in the meta data.... 
I don't know of a program with a GUI that will do what you want. Two programs that you may want to look at are pyrenamer and phatch:

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

[http://photobatch.stani.be/](http://photobatch.stani.be/)

If you do not find a program that meets your needs, you may want to consider one of the command-line options. The one I use is exiv2. The following exiv2 command will rename all JPG files in the current directory in the format YYYY-MM-DD_#:

```
exiv2 -F rename -r "%Y-%m-%d" *.JPG
```

The man page describes the rename action as follows, so it appears that the time used is the create timestamp from the exif data:

> Rename  files  and/or  set  file timestamps according to the Exif create timestamp. Uses the value of tag Exif.Photo.DateTimeOriginal  or,  if  not  present,  Exif.Image.DateTime to determine the timestamp. The filename format can be set with -r fmt,  timestamp options are -t and -T.

---

### Post by coffeecat on 2009-07-05
The GUI app gThumb (it's in the repos) might do what you want, although the rename utility is a well hidden secret in it.

Highlight the images you want to rename in the right pane of gThumb, right-click on one of them and choose 'Rename". The special character %n gives you the original creation date from the EXIF data which unfortunately also includes the image creation time as well.

---

### Post by Eli Turk on 2009-07-06
Success! Thank you both! \\:D/

coffeecat,
gThumb works perfectly! It even puts in the time! But I had to use "%d", not "%n". Maybe different versions?


kaibob,
Phatch is no good for what I'm trying to do. It's actually worst than Gwenview for renaming photos. It gives the last modified date like the following: 2009-1-27, 2009-3-27, 2009-12-27; thus getting the files out of order.

But, pyRenamer is AWESOME! It can rename many different file types, many different ways (even music using its metadata). It can even put the brand and model of the camera that took the photo, and photo dimensions in the name. I will definitely be using this program often. Although, one thing that gThumb has that pyRenamer does not is the option to put the file size in the name.


Thanks again to both of you! :D

---

### Post by coffeecat on 2009-07-06
> **Eli Turk said:**
> But I had to use "%d", not "%n". Maybe different versions?

No, my mistake - temporary brain malfunction. :( :oops:

> **Eli Turk said:**
> Although, one thing that gThumb has that pyRenamer does not is the option to put the file size in the name.

I don't know whether this will work, but you could try this. Use pyRenamer for everything you want except the image size, and then %f%s in gThumb to add the image size to the name given by pyRenamer.

---

### Post by Eli Turk on 2009-07-07
Great! That works just fine. Thanks again.

---

