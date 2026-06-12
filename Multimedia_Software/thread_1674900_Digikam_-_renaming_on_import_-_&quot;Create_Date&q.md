---
title: "Digikam - renaming on import - &quot;Create Date&quot; versus &quot;File Modification Date&quot;"
date: 2011-01-24
forum: Multimedia Software
---

### Post by nielsholgerson on 2011-01-24
Hi,

I just switched from a basic digital camera to a more advanced one that stores both Jpeg and Raw (.Nef - it's a Nikon) files for me.

When importing files in Digikam, I rename the files so that they start with Date and Time.  Example: 20110121-223748.JPG  for a photo taken on Jan 21st 2011 at 22:37:48.

I was a bit surprised when importing both the JPEG and the Raw version of the same photo, that the filename is different by a few seconds (no constant offset, sometimes they are the same):
20110121-223748.JPG 
20110121-223750.NEF

I did some "research" by looking at the exif data of both files (using "exiftool 20110121-223748.JPG" from the command line).  Here is what I got back (amongst other data):[INDENT]20110121-223748.JPG[FONT=Courier New]
File Modification Date/Time     : 2011:01:21 22:37:**[COLOR=Red]48[/COLOR]**+01:00[/FONT]
[FONT=Courier New]Modify Date                     : 2011:01:21 22:37:48
Date/Time Original              : 2011:01:21 22:37:48[/FONT]
[FONT=Courier New]Create Date                     : 2011:01:21 22:37:48[/FONT]
[FONT=Courier New]Create Date                     : 2011:01:21 22:37:48.00[/FONT]
[FONT=Courier New]Date/Time Original              : 2011:01:21 22:37:48.00[/FONT]
[FONT=Courier New]Modify Date                     : 2011:01:21 22:37:48.00[/FONT]
[/INDENT][INDENT]20110121-223750.NEF[FONT=Courier New]
File Modification Date/Time     : 2011:01:21 22:37:**[COLOR=Red]50[/COLOR]**+01:00[/FONT]
[FONT=Courier New]Modify Date                     : 2011:01:21 22:37:48[/FONT]
[FONT=Courier New]Create Date                     : 2011:01:21 22:37:48[/FONT]
[FONT=Courier New]Date/Time Original              : 2011:01:21 22:37:48[/FONT]
[FONT=Courier New]Create Date                     : 2011:01:21 22:37:48.00[/FONT]
[FONT=Courier New]Date/Time Original              : 2011:01:21 22:37:48.00[/FONT]
[FONT=Courier New]Modify Date                     : 2011:01:21 22:37:48.00[/FONT]

[/INDENT]So it seems that Digikam is using the "File Modification Date/Time" (different in the Jpeg's and Raw's of my camera) rather than the "Create Date" (the same for both Jpeg and Raw).  

[SIZE=1](The few seconds difference in "File Modification Date/Time" between the two versions of the same photo is probably due to the time that my camera needs to write away the data on the SD memory card.  I guess.)[/SIZE]

**==> Is there a way to have Digikam use the Create Date?  (Or the Date/Time Original?)**

Thank you for your help!

PS: I'm on Ubuntu 10.04LTS, using DigiKam 1.2.0

---

### Post by AlphaLexman on 2011-01-24
I would look at the filesize of the .jpg vs the .raw file, the larger (.raw) file will take longer to transfer from your camera, and will have a different file time!

I would suggest NOT using the .jpg mode of your camera and just use .raw, you can convert .raw to .jpg with programs like 'ufraw'

---

