---
title: "Is there a known problem video rendering in Xubuntu?"
date: 2016-01-22
forum: Multimedia Software
---

### Post by RangerK on 2016-01-22
I can't seem to add a picture as the visual component of my video.  I've tried .jpg's and .png's.  I've tried OpenShot and Kdenlive.  I've tried simple black-and-white images.  One image.  No animation.  Just one image for the whole of the video.

No matter what I do, the result has this sort of color distortion like this:

[IMG]http://i.imgur.com/0x6CkJu.png[/IMG]

Is there a known problem?  Perhaps something related to this bug: [https://bugs.launchpad.net/openshot/+bug/440128](https://bugs.launchpad.net/openshot/+bug/440128)

---

### Post by RangerK on 2016-01-23
Apparently, there was a problem with video drivers.

The clue was that sometimes a video would play normally, and sometimes it would look like what you see above -- those symptoms seems to imply a video overlay problem.  I've seen been told on IRC that ATI has a checkered relationship with linux.  (I have an ATI RADEON 7870 graphics card.)

Installing these drivers worked for me:

[http://askubuntu.com/questions/660900/xubuntu-14-04-ati-amd-driver-problem](http://askubuntu.com/questions/660900/xubuntu-14-04-ati-amd-driver-problem)

---

