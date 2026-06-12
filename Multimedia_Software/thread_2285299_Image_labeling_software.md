---
title: "Image labeling software"
date: 2015-07-04
forum: Multimedia Software
---

### Post by kumoshk on 2015-07-04
I've got a whole bunch of old pictures that I scanned. I would like to label them somehow (like who is who in each picture, where/when it is and such, without making an enormous file name).

So, I'm looking for a program where it'll show the image and allow you to type in a caption, and move on to the next image. It would be nice if it simply saved a txt file with the same name as the picture (besides the file extension) with the label text inside. However, I'm open to other solutions, too, especially if they're better. Do you know any software like this for Linux, or lacking that, another solution?

I imagine this is an issue people encounter a lot.

---

### Post by tgalati4 on 2015-07-04
If you want to store such data within the file itself, you can use the "notes" section of EXIF and use one of several EXIF tools.  It's similar to ID3 tags for mp3 music tracks.

> eog-plugins - set of plugins for eog
exif - command-line utility to show EXIF information in JPEG files
exifprobe - Read metadata from digital pictures
exiftags - utility to read Exif tags from a digital camera JPEG file
exiftran - transform digital camera jpeg images
exiv2 - EXIF/IPTC metadata manipulation tool

Otherwise use a photomanager, which stores the data in a database, but does not travel with the image, when the the image is moved off of the machine.

---

### Post by Dennis N on 2015-07-04
I use gthumb for our old family photos that have already been scanned into digital images. When in gthumb's viewer mode, there is a "Comment" button that allows you to add a description (and more) which is then saved as metadata in the image file (not as a separate file). Digital file formats for images allow this. This is preferable to a separate file because the comments won't ever get separated from the pictures.

Then when viewing in gthumb's browser mode, your information shows up under the photos. 

Other basic image viewers can usually at least show the metadata and display it under Properties.

---

### Post by ajgreeny on 2015-07-04
+1 for gthumb.

It is my favourite image management tool, closely followed by digikam, even though that is a KDE app and brings in lots of kde libs.  I need those libs anyway for kmymoney2, so there are not too many extra.

I find shotwell slow and cumbersome, but it will also do what you want, as far as I'm aware.

---

### Post by kumoshk on 2015-07-09
Thank you for all the help, everyone! That's awesome. :)

---

