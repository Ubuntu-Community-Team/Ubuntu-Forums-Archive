---
title: "Repairing corrupted JPEGs"
date: 2013-11-14
forum: Multimedia Software
---

### Post by Lars Noodén on 2013-11-14
What utility is good for repairing corrupted JPEGs that won't open with eog or gimp?

---

### Post by sudodus on 2013-11-14
Do you know how they are corrupted? Made with a particular program/camera or damaged somehow?

---

### Post by FakeOutdoorsman on 2013-11-14
Please provide a sample file.

---

### Post by Lars Noodén on 2013-11-15
Ok.  Looking at it more refreshed, the worst "corruption" problem comes from a failure in eog's error message.  If a file is missing eog reports it this way:

[indent]
*No images found in file:///home/user/Pictures/foo.jpeg*
[/indent]

So eog, needs a better error message.  Gimp does better, I was just misreading it.  

The EXIF data is where the problems seem to lie.  I'm getting two kinds of error messages.

[indent][i]
Corrupt data
The data provided does not follow the specification.
ExifLoader: The data supplied does not seem to contain EXIF data.
 [/i][/indent]

I've attached a JPEG sample with the above error.

[indent][i]
Corrupt data
The data provided does not follow the specification.
ExifMnoteCanon: Invalid zero-length tag size
[/i][/indent] 

That one seems to be because of a missing date - time stamp in the images.  It might have been a fault in the camera.  It looks like the work-around is to use jhead to try to set the date manually.

---

### Post by Lars Noodén on 2013-11-15
Trying the attachment again.  It seems not to upload.

---

### Post by FakeOutdoorsman on 2013-11-15
I get no such messages from gimp 2.8.8 (or in the console) upon opening this file.

---

### Post by Lars Noodén on 2013-11-15
gimp is ok with that one, where to I find the exif data in gimp?

The eog error is due to an inaccurate error message with regards to missing files, something which doesn't apply because this file actually exists: [https://bugs.launchpad.net/ubuntu/+source/eog/+bug/1251562](https://bugs.launchpad.net/ubuntu/+source/eog/+bug/1251562)

/usr/bin/exif has trouble and chokes on it though.  It says :

Corrupt data
The data provided does not follow the specification.
ExifLoader: The data supplied does not seem to contain EXIF data.

---

### Post by FakeOutdoorsman on 2013-11-15
> **Lars Noodén said:**
> gimp is ok with that one, where to I find the exif data in gimp?
I'm not sure (but I was too lazy to search).

> **Lars Noodén said:**
> /usr/bin/exif has trouble and chokes on it though.
I can confim that on 0.6.21, but this might be its standard behavior although it did the same on all inputs that I added some exif info to with exiftool. I'll blame exif.

exiftool (libimage-exiftool-perl package) works fine:
```
$ exiftool 100_193.jpg 
ExifTool Version Number         : 9.27
File Name                       : 100_193.jpg
Directory                       : .
File Size                       : 13 kB
File Modification Date/Time     : 2013:11:15 09:54:34-09:00
File Access Date/Time           : 2013:11:15 09:54:34-09:00
File Inode Change Date/Time     : 2013:11:15 09:54:34-09:00
File Permissions                : rw-r--r--
File Type                       : JPEG
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 230
Y Resolution                    : 230
Comment                         : AppleMark.
Image Width                     : 240
Image Height                    : 180
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:2 (2 1)
Image Size                      : 240x180

```

---

### Post by Lars Noodén on 2013-11-16
Ok, thanks.  I'll work with exiftool for a while on these jpegs.

---

### Post by Dee Jay on 2013-12-12
> **Lars Noodén said:**
> Ok.  Looking at it more refreshed, the worst "corruption" problem comes from a failure in eog's error message.  If a file is missing eog reports it this way:[INDENT]...[I]
Corrupt data
The data provided does not follow the specification.
ExifMnoteCanon: Invalid zero-length tag size
[/I][/INDENT]
That one seems to be because of a missing date - time stamp in the images.  It might have been a fault in the camera.  It looks like the work-around is to use jhead to try to set the date manually.

FWIW, I have never seen this error in my exif data until today. After identifying the faulty images I realized that it was caused by using Windows Explorer's "Rotate clockwise" or "Rotate counterclockwise" on the images.

---

