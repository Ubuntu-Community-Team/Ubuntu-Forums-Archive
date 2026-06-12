---
title: "Shotwell - not detecting duplicate images"
date: 2012-10-06
forum: Multimedia Software
---

### Post by tenbones79 on 2012-10-06
Shotwell is not detecting many of my duplicate images. The reason for this is that the metadata is different. I have imported about 4000 images that have the exposure date set to one hour earlier that their duplicates. (I believe the reason for this is that some photo program some years ago must have adjusted the metadata to correspond to daylight saving time.) In some cases the reason might be that image tags has been saved to the metadata.

See file attachment for example.

I guess the MD5 cheksum that shotwell takes of the images includes the metadata-information of the file.

Does anybody know if there is a way of ignoring the metadata when Shotwell is looking for duplicate images?

Altarnatively: Do you know of any other software that detects duplicates by only comparing MD5 checksums of the imagedata of the file?

Regards 
Trond

---

### Post by eric-yorba on 2012-10-08
Shotwell only matches image data, not metadata.

What version of Shotwell are you running?

---

### Post by tenbones79 on 2012-10-09
I use version 0.12.3 of Shotwell. Are you sure it only matches image data?

I filed a support case at yorba.org ([http://redmine.yorba.org/issues/5971#change-19217](http://redmine.yorba.org/issues/5971#change-19217)). It has now been marked as duplicate of this issue: [http://redmine.yorba.org/issues/1857](http://redmine.yorba.org/issues/1857)

The functionality of ignoring meta data is targeted for the next version (0.14) - according to the issue tracker at yorba.org.

---

### Post by eric-yorba on 2012-10-10
It actually depends how you import the photo; Shotwell is quite a bit smarter when you import from a camera.  I'm guessing you imported these photos from the file system?

---

### Post by tenbones79 on 2012-10-10
Yes, I imported most of my images from the file system.

---

