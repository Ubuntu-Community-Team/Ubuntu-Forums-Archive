---
title: "fix exif date in pics?"
date: 2010-07-09
forum: Multimedia Software
---

### Post by shane2peru on 2010-07-09
Does anyone know of a good tool for quickly and efficiently editing exif data on digital pictures?  I don't mind if it is command line, as I find cli more efficient most of the time.  If there is a way of batching this job out, even better.  What tools can I use?  Thanks in advance!

Shane

---

### Post by kolibri on 2010-07-09
Digikam has a command to adjust date and time in exif.  I don't know if it's flexible enough for what you need to do or not, but you can apply it to multiple images, say if you need to change the date on 10 images to July 2010 instead of 1910 or something like that.

---

### Post by shane2peru on 2010-07-09
> **kolibri said:**
> Digikam has a command to adjust date and time in exif.  I don't know if it's flexible enough for what you need to do or not, but you can apply it to multiple images, say if you need to change the date on 10 images to July 2010 instead of 1910 or something like that.

Thanks for the info, changing multiple pictures would be very helpful!  I just got all my pics imported into f-spot, so I will have to see if it can do something similar to avoid installing Digikam with all the kde dependencies.  Thanks for the tip though.

Shane

**EDIT:**  Hey f-spot can do that too!  That is great to be able to do several pics at once!  Thanks a bundle.

---

### Post by shane2peru on 2010-10-26
After importing my data from f-spot to shotwell, I found out that f-spot DID NOT really edit the exif data.  But rather 'pretended to edit it' so now shot well doesn't show any pictures.  Digikam is importing all my photos now, to see if I can truly edit the date the picture was taken.  What frustration.  There seems to be no good way to do this in Linux that I know of.  Not even command line.  Searches turn up very shallow results, irc no one responds.  Please, if you konw of a way to do this, it would be very helpful to let us know!  Thanks!!!

Shane

---

### Post by dez93_2000 on 2010-11-14
looking into this currently as well. One option might be to install attributemagic pro (free trial) in wine, depending on your need. I've got a load of my mate's pics and i need to sync our camera clocks so the slideshows work, thus i need to move all of his an hour earlier on the exif time stamp. Suspect it'll turn into a massive pain in the bottom...

---

### Post by jetpeach on 2011-01-03
my research has shown two possibilities i'm going to try:
exiftool
[http://www.tectonic.co.za/2007/12/time-shift-photo-dates-with-exiftool/](http://www.tectonic.co.za/2007/12/time-shift-photo-dates-with-exiftool/)
or
jhead
[http://www.sentex.net/~mwandel/jhead/](http://www.sentex.net/~mwandel/jhead/)

it seems both are in the repos, although exiftool is a perl library that might take more work trying to figure out how to use, so i'll try jhead first and see how it goes.

---

