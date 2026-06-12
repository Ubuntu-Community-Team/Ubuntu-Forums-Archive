---
title: "change EXIF data"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by finite9 on 2007-06-13
Is there a GUI tool that can easily change the creation date in the EXIF data of a photo?  I have heard of exiv2 and another CLI tool, but cannot for the life of me figure out how to display EXIF fields and/or change the data with these tools.

---

### Post by mitch.c on 2007-06-14
Digikam will let you edit date and time... it's a KDE photo management program like F-Spot or Picasa. I don't know of any others.

As for the CLI tools most will dump Exif data, or adjust date/time as on offset of the original EXIF stamp:
```
# to dump exif data
$ exiv2 -p s filename.jpg

# adjust date/time +1 day (in hours)
$ exiv2 ad -a 24 filename.jpg

## or use jhead ##

# to dump exif data
$ jhead filename.jpg

# adjust date/time
$ jhead -ta+24 P1000616.JPG
```
IMHO, jhead is much more capable, and provides more control over date/time (see the '-da' option).

Hope that helps.

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by finite9 on 2007-06-14
thankyou very much!!  It worked really well with Jhead, but for some reason, gThumb will not update the Exif data when I choose properties on the image.  I reloaded gThumb, but still was old date.  When I run jhead <image> the new date is displayed.

I used the -ts option instead so that I just need to specify one new date, so I can bulk rename all files in a folder at once.

---

### Post by mitch.c on 2007-06-14
> **finite9 said:**
> thankyou very much!!  It worked really well with Jhead, but for some reason, gThumb will not update the Exif data when I choose properties on the image.  I reloaded gThumb, but still was old date.  When I run jhead <image> the new date is displayed.

I used the -ts option instead so that I just need to specify one new date, so I can bulk rename all files in a folder at once.
From the jhead man page:
> ```
-ts    Sets the time stored in the Exif header to what is specified on the com-
       mand line.  This option only changes the "DateTimeOriginal"  (tar  0x9003)
       field,  but leaves the "DateTimeDigitized" (tag 0x9004) field alone.  Time
       must be specified as: yyyy:mm:dd-hh:mm:ss
```
So, I would assume that gThumb is reading the "DateTimeDigitized" field and since you used -ts, you updated "DateTimeOriginal". The -ta and -da options will update both fields, but require using an offset as opposed to an absolute date.

---

### Post by finite9 on 2007-06-14
> **mitch.c said:**
> From the jhead man page:

So, I would assume that gThumb is reading the "DateTimeDigitized" field and since you used -ts, you updated "DateTimeOriginal". The -ta and -da options will update both fields, but require using an offset as opposed to an absolute date.

No, I view the EXIF properties tab of the image and all 3 date/time fields are the same as they were before running jhead.

---

