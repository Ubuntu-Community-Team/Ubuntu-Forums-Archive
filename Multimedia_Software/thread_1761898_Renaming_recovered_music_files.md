---
title: "Renaming recovered music files"
date: 2011-05-18
forum: Multimedia Software
---

### Post by virtualcourtney on 2011-05-18
Hey folks,

I managed to very stupidly (and avoidably) overwrite the hard drive that contained all my stuff--music, photos, home videos from the 80's that were painstakingly converted to digital movies, etc.  After running Photorec and recovering much of the data to another disk, I'd like to be able to rename the music files using whatever exif data/tags are available.

Anyone have any utilities they can recommend for this?

I hope you all back up your data better and more regularly than I do!

-Courtney :)

---

### Post by coffeecat on 2011-05-18
There must be a command line utility that will take the 'Title' id3 tag and use that to rename music files. But I don't know of one. However, if you are prepared to do this laboriously file by file in a GUI, have a look at Easytag. It's in the repositories.

In the right pane are the ID3 tags, and the "Title" field is probably the one you'll want to copy for the filename. The field at top right is the filename field (less the mp3/flac/ogg/whatever extension). That's where you can rename the file from within Easytag. With Easytag, once you've edited your tags (or the filename field) you have to click on the disk icon to write the changes. It'll prompt you to do this if you try to change to another folder anyway.

You don't ask how to rename jpegs from metadata, but Gthumb has a nifty rename utility for this.

---

### Post by papibe on 2011-05-18
If you have a collections of songs instead of full CD rips, I highly recommend kid3.

Regards.

---

### Post by virtualcourtney on 2011-05-19
Thanks for the replies!  I think Easytag will work for my purposes--it has a renaming mask that can, I think, be applied to an entire directory.  For pictures, I used jhead to rename them according to their metadata.

Thanks again!  Now if only there were other handy utilities for renaming, you know... doc, odt, tex, and other types of files.  It's going to be a long haul.

---

### Post by virtualcourtney on 2011-05-19
An update: still not solved!

I have about 25000 music files that were recovered using photorec, and I think the sheer number of files I'm trying to work with is killing Easytag.

Does anyone know if there a command line tool that I could use to rename my files (along the lines of jhead for JPEG files)?

---

### Post by papibe on 2011-05-19
I think with a combination of scripts and id3ren you may accomplish that. Here's its [man ]("http://www.digipedia.pl/man/doc/view/id3ren.1/")page.

I hope it helps.

---

### Post by virtualcourtney on 2011-05-22
Ex Falso did it in the end.  It has a pretty reasonable GUI (I couldn't figure out how to actually use command line tools like id3ren or id3v2).

---

