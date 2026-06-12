---
title: "Scripting - with EXIF!"
date: 2009-07-21
forum: Multimedia Software
---

### Post by kaffemonster on 2009-07-21
Well here's a head-scratcher for y'all...

I need something that can pull the "date taken" tag from exif and use that date as part of a script that renames the file from something like 9709.CR2 to 2009_07_21-0001.CR2


Hmmm... not even sure if we need the date from EXIF, just need the date the file was created.

Can it be done? Anyone know in which direction I should look?

Hmmm... not even sure if we need the date from EXIF, just need the date the file was created.

---

### Post by kaibob on 2009-07-21
> **kaffemonster said:**
> ...I need something that can pull the "date taken" tag from exif and use that date as part of a script that renames the file from something like 9709.CR2 to 2009_07_21-0001.CR2...

There are a number of command-line utilities that will do what you want. The one I use is exiv2, which is in the repo's. By way of example, the following renames all JPG files in the current directory in the format YYYY-MM-DD_#:

```
exiv2 -F rename -r "%Y-%m-%d" *.JPG
```

The exiv2 man page indicates that "read-only" support is available for the CR2 file format. I assume this means that the rename command will still work. If not, you would have to use exiv2 to extract the date-taken data and then use that data to rename in a standard shell script. 

> exiv2  is  a program to read and write Exif, IPTC and XMP image metadata and image comments. Supported image formats  are  JPEG,  Canon  CRW  and Canon  THM.   Read-only  support is currently available for PNG and TIFF format and includes TIFF-based RAW formats: Adobe DNG, Canon CR2,  Fuji&#8208;film  RAF, Minolta MRW, Nikon NEF, Olympus ORF, Pentax PEF, Sony ARW and Sony SR2.

---

### Post by kaffemonster on 2009-07-21
Awesome - Thanks a bundle!

---

### Post by kaffemonster on 2009-07-22
Hmm... any way to add tags to filenames? Specifically adding the Camera model to the file name as I'm currently shooting two different DSLRs. Have looked at the exiv2 documentation online as well as the man page. All I know is that I need to use the tag Exif.Canon.ModelID somehow, but it seems that the rename option can only handle dates... Any way to append the model ID to the file name?

---

### Post by kaibob on 2009-07-23
> **kaffemonster said:**
> ...Any way to append the model ID to the file name?

I have quoted below the exiv2 output from a JPG photo. As you can see, it includes the camera make and model. A simple shell script can extract this information and include it in a rename command. 

As an alternative, you may want to consider pyrenamer, which will apparently include the camera information. See post 4 in the following thread:

[http://ubuntuforums.org/showthread.php?t=1204781](http://ubuntuforums.org/showthread.php?t=1204781)

> kaibob@dell:~/temp$ exiv2 test.jpg
File name       : test.jpg
File size       : 3006530 Bytes
Camera make     : Canon
Camera model    : Canon PowerShot SD1000
Image timestamp : 2008:09:23 10:12:57
Image number    : 100-0044
Exposure time   : 1/400 s
Aperture        : F8
Exposure bias   : 0
Flash           : No, auto
Flash bias      : 0 EV
Focal length    : 5.8 mm
Subject distance: 138
ISO speed       : 80
Exposure mode   : Easy shooting (Auto)
Metering mode   : Multi-segment
Macro mode      : Off
Image quality   : Superfine
Exif Resolution : 3072 x 2304
White balance   : Auto
Thumbnail       : JPEG, 4453 Bytes
Copyright       : 
Exif comment    : 

---

### Post by kaibob on 2009-07-23
As practice, I wrote the following script, which appears to work. It includes camera model plus date and time. You could alter this to camera model plus date plus sequential numbering but it requires a bit more work.

BTW, you have to change directory and file extension in the script. Also, I used copy (cp) rather than move (mv) to avoid overwriting the original files. 

```
#!/bin/bash

cd /home/kaibob/temp/

for file in *.jpg ; do
   model=$(exiv2 "${file}" | awk '/Camera model/ {print substr($0, index($0,$4))}')
   taken=$(exiv2 "${file}" | awk '/Image timestamp/ {print substr($0, index($0,$4))}')
   cp "$file" "${model} - ${taken}.jpg"
done
```

The following is a directory listing with original and new file names:

> /home/kaibob/temp/IMG_0042.JPG
/home/kaibob/temp/IMG_0043.JPG
/home/kaibob/temp/IMG_0044.JPG
/home/kaibob/temp/IMG_0045.JPG
/home/kaibob/temp/Canon PowerShot SD1000 - 2008:09:23 10:12:06.JPG
/home/kaibob/temp/Canon PowerShot SD1000 - 2008:09:23 10:12:22.JPG
/home/kaibob/temp/Canon PowerShot SD1000 - 2008:09:23 10:12:57.JPG
/home/kaibob/temp/Canon PowerShot SD1000 - 2008:09:23 13:14:18.JPG

As an aside, pyrenamer may still be the best option, as it appears to require less work.

---

