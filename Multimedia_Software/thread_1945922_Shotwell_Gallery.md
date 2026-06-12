---
title: "Shotwell Gallery"
date: 2012-03-23
forum: Multimedia Software
---

### Post by tazz4vr on 2012-03-23
After performing updates via 'Update Manager' I now have an issue importing images from a device into the Shotwell Gallery, basically it starts to upload the images and then after the third or fourth image it just freezes up my puter.  Anyone else have similar issue?

---

### Post by eric-yorba on 2012-03-26
What version of Shotwell did it update to?

You can find the version in Help->About

---

### Post by tazz4vr on 2012-03-26
The version is 0.11.6

---

### Post by eric-yorba on 2012-03-26
Hmm. What type of device are you importing photos from?  Do you have enough free disk space?

---

### Post by tazz4vr on 2012-03-26
The device used was a card reader, after two failed attempts, I booted puter in Windows and was able to get photos without problems, so no disk space issue.

Also, just hooked up the camera and puter froze up in Shotwell, booted back into Windows, again, no problem getting photos.

---

### Post by eric-yorba on 2012-03-26
How long does it freeze for?  Shotwell (and most other Linux photo apps) relies on GPhoto for grabbing photos from a camera or card reader.  It is known to make apps freeze for a short period of time while it initially accesses the device.

It might be worth your time to run the gphoto command line tool and see if you can mount and access your camera with that.  If you can, it's a Shotwell bug and you should file it [here]("http://redmine.yorba.org/projects/shotwell/issues/new").  Or if it also locks up with the gphoto command line tool, that would make it a GPhoto bug which you can file with the GPhoto folks [here]("http://sourceforge.net/tracker/?group_id=8874").

---

### Post by tazz4vr on 2012-03-30
Not sure why, didn't do any additional updates, but it works fine now.

At this time, as the problem doesn't seem to be occuring anymore, I am going to mark this thread as 'Solved'.

---

