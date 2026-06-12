---
title: "Identify image by text on image and move?"
date: 2008-12-04
forum: Multimedia Software
---

### Post by danweaver on 2008-12-04
I have about 5 million images on a disk that went bad. I used photorec to recover them, but that doesn't retain original file folder structure. Even if I have to pay for something, I need to identify an image based on the date time stamp on the top left of the image and move those files to another folder ideally.

I'm very technically inclined, but don't readily know how to accomplish this.

Another option is a software application that can recover files from a drive where the files have been deleted, but with naming intact, as I know how to get what I need if this is the case.

Here is a sample image. Note that the time stamp would remain identical in the date area, so I imagine that even the simplest of software with some sort of batch procedure would suffice.

[IMG]http://logmykeys.com/f4968920.jpg[/IMG]

If you know of any application or procedure to do this I would be greatly appreciative.

---

### Post by kaibob on 2008-12-04
I'm not familiar with photorec or what it recovers, but if these are digital photos, you may want to look into recovering the exif information:

[http://en.wikipedia.org/wiki/Exchangeable_image_file_format](http://en.wikipedia.org/wiki/Exchangeable_image_file_format)

If the exif information is available, you could use a command-line utility (such as exiv2) to rename the files.

[http://www.exiv2.org/](http://www.exiv2.org/)

I don't know how to extract the date/time information printed in the corner of the image.

---

### Post by danweaver on 2008-12-04
Exiv2 unfortunatly will not work for this purpose. I had already tried to see if any metadata was written to the image files at creation, unfortunatly it is not. The images were taken through the use of zoneminder, which does not write metadata, or at least that is not recovered by photorec.

---

### Post by xzero1 on 2008-12-04
The metadata may not be there but what about the file creation and/or modification dates? I take it these are individual files, right?

---

### Post by danweaver on 2008-12-04
The file creation dates were not retained by photorec. I have however found a free application that runs in windows. I had to begrudgingly boot windows, but it is keeping the directory structure. This is going to save me a lot of time. The application is called R-Linux.

Thanks for the help both of you. I still think I want to figure out some sort of means to recognize part of the image, but thats a pet project I'll have to mess with later.

Some backstory in case you're interested. Cash register was pilfered. On the same day, the DVR system conveniently opened itself up and the hard disk removed itself and slammed itself into the floor. I replaced the controller on the hard disk with one from an identical drive and it actually worked. Only problem was that there were tons of bad sectors and the drive would not boot and would not clone. That is how I arrived at my current situation. It is great that I'm likely going to be able to pin down the thief. Unfortunately it is probably an employee.

---

