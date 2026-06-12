---
title: "Want to add Timestamp to digital photos."
date: 2009-08-08
forum: Multimedia Software
---

### Post by blackbird3216 on 2009-08-08
I prefer to have no timestamp on my photos, but my parents like to have them because they can see when the photo was originally taken when inside their photo album. My camera(the Canon a540) automatically saves the date and time the photo was taken to the jpeg, but it does not show as a timestamp on the photo, which is good. In order to make both my parents and I happy, I'd have to add the timestamps before developing. Is there software that allows me to batch add timestamps to the photos(Sometimes more than 300 at a time), preferably open source/linux compatible? It is also ok if it is windows compatible. That would be much easier than manually entering the date to the photos in a text box.

---

### Post by potam on 2009-08-09
Do you mean something like this? : [Picture with Exif data]("http://www.pbase.com/image/38767795/original.jpg")
I found a bash script that will help you: [adding exif data to picture with imagemagick]("http://blog.wikifotos.org/2008/07/04/anadir-marco-descriptivo-con-datos-exif-a-las-fotos/")

---

### Post by arky on 2009-08-09
What you need is this 

[http://dptnt.com/2009/04/how-to-add-date-time-stamp-to-jpeg-photos-using-free-software/](http://dptnt.com/2009/04/how-to-add-date-time-stamp-to-jpeg-photos-using-free-software/)

---

### Post by blackbird3216 on 2009-08-09
> **arky said:**
> What you need is this 

[http://dptnt.com/2009/04/how-to-add-date-time-stamp-to-jpeg-photos-using-free-software/](http://dptnt.com/2009/04/how-to-add-date-time-stamp-to-jpeg-photos-using-free-software/)
I tried doing what the site said in windoes, but I keep getting this error message. 
> 'CHOICE' is not recognized as an internal or external command,
operable program or batch file.
Missing operand.
'identify' is not recognized as an internal or external command,
operable program or batch file.
Missing operand.
Could Not Find C:\Documents and Settings\Mom\My Documents\dttempfile
Processing C:\Documents ...
Invalid Parameter - -gravity
No files processed

What am I doing wrong? I'm using the newest version of Imagemagick.

---

### Post by blackbird3216 on 2009-08-12
anyone?

---

### Post by kaibob on 2009-08-13
> **blackbird3216 said:**
> anyone?

I don't know anything about Windows batch programs, but the following shell script will do what you want:

```
#!/bin/bash

for file in *.JPG ; do
   convert "$file" -font arial.ttf \
      -pointsize 72 -fill white -annotate +100+100  \
      %[exif:DateTimeOriginal] "new-${file}"
done
```

If the font you use is not in your path, you will have to include the path in the command. With a large number of files, this command may take a while. I tested the shell script on a group of ten photos and it worked fine.

---

### Post by arky on 2009-08-13
Hardcoding paths in script is a bad idea. 

Copy the arial.ttf to your .fonts folder that way you don't have to mention the path in script.

---

### Post by blackbird3216 on 2009-08-17
> **arky said:**
> Hardcoding paths in script is a bad idea. 

Copy the arial.ttf to your .fonts folder that way you don't have to mention the path in script.
Stupid question. Do I need to install imagemagick to use the script?

---

### Post by Whiffle on 2009-08-17
looks like you do.

---

### Post by arky on 2009-08-17
Yes, the convert is provided by imagemagick

---

### Post by hemna on 2009-11-14
I'd like to do this as well, but during mencoder time.  I'm using mencoder to convert a directory of images to an .avi (timelapse photography).  I know I can run convert on the images first, but this either 1) alters the original image or 2) duplicates the images.  I have about 4000 or so images that I use for each timelapse and I don't want to alter the images or duplicate them.

I basically want to do multiple test runs on using different settings on mencoder to determine the optimal frame rate, resolution etc.   

Here is a sample movie [http://www.youtube.com/watch?v=dIcpEK4116M]("http://www.youtube.com/watch?v=dIcpEK4116M")

I wrote a bash script that will allow me to do test runs with different settings, but I'd like one of the runs to include the exif timestamps.

It would be ideal to have mencoder call convert on each image prior to adding the image into the .avi stream without duplicating the original or making a copy.

---

### Post by hemna on 2009-11-14
Here is a copy of my updated script that has the option to add timestamps from exif data of each image.  


I tried in vain for hours to get mencoder to add the timestamps from exif on the fly, but it just doesn't work.


this script will process all of the images in a dir and create a ts dir with new images w/ timestamps then dump those images into mencoder.  It blows, but works.

---

### Post by Papa_Smurf on 2009-11-14
Blender has a timestamp feature that it can put on all its graphic output. It reads and writes lots of different video files and image files and sequences. The Video Sequence Editor can load in many images at the same time and write them out with a TimeStamp. Using the timestamp is[ documented here]("http://wiki.blender.org/index.php/Doc:Reference/Panels/Scene/Render/Stamp")

---

### Post by Papadzulinux on 2010-12-14
Hiya, There's a wonderful program called Phatch, among it's batch actions it includes an "add text" feature that can read and print Exif information (original date included, of course) directly into the image, with configurable format.

---

### Post by Lubelaczek on 2011-08-18
> **arky said:**
> Yes, the convert is provided by imagemagick

Unfortunately doesn't work in my XP machine. It is used for different purpose:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

Z:\>convert /?
Converts FAT volumes to NTFS.

CONVERT volume /FS:NTFS [/V] [/CvtArea:filename] [/NoSecurity] [/X]

  volume      Specifies the drive letter (followed by a colon),
              mount point, or volume name.
  /FS:NTFS    Specifies that the volume is to be converted to NTFS.
  /V          Specifies that Convert should be run in verbose mode.
  /CvtArea:filename
              Specifies a contiguous file in the root directory to be
              the place holder for NTFS system files.
  /NoSecurity Specifies the converted files and directories security
              settings to be accessible by everyone.
  /X          Forces the volume to dismount first if necessary.
              All opened handles to the volume would then be invalid.

So neither -gravity, -font, -pointsize, -fill,  -annotate will work. That means to me this script is not meant to be used on XP machines. Is that right?

---

### Post by coffeecat on 2011-08-18
> **Lubelaczek said:**
> 
So neither -gravity, -font, -pointsize, -fill,  -annotate will work. That means to me this script is not meant to be used on XP machines. Is that right?

If you run the command "convert" in a Windows command prompt, it will invoke the Windows executable convert.exe, which is used to convert FAT filesystems to NTFS. So the output you got is not surprising.

Are you trying to run a bash script in Windows? There have been a couple of bash scripts posted, but none that I can see called "convert". No, a bash script will not work in Windows, unless you install gnu bash for Windows. What are you trying to do?

---

