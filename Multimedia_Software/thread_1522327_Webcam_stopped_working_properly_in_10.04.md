---
title: "Webcam stopped working properly in 10.04"
date: 2010-07-02
forum: Multimedia Software
---

### Post by temporos on 2010-07-02
I'm using the 10.04 Netbook Edition on an ASUS EeePC 1005HA.  Earlier, I had 9.10 Netbook Remix installed.  Under 9.10NR, the webcam worked wonderfully in *Cheese*.  Once I upgraded to 10.04NE, the webcam became sluggish to the point where it is now unusable.  In video mode it captures about 1 frame per five seconds.  Under 9.10NR, it regularly captured 60 fps.

Did the driver package for webcams change significantly between 9.10 and 10.04?  I can't think of anything else that would cause this issue due to an OS upgrade.

---

### Post by YannBuntu on 2010-07-03
Please report a bug on Launchpad : [https://bugs.launchpad.net/ubuntu/+source/cheese/+filebug](https://bugs.launchpad.net/ubuntu/+source/cheese/+filebug)

As it is a regression, I am sure it can be solved :)

---

### Post by no2498 on 2010-07-05
look in the cheese help faq's
see if changing the plugin helps

---

### Post by temporos on 2010-07-05
I changed the video output plugin, and now I get smooth video recording, but only after about 45 seconds.  For the first 45 seconds of a recording, I have the same problem: one frame per five seconds.  I've also discovered that I cannot record audio no matter which plugin I select.

Again, all this worked perfectly in 9.10...

---

### Post by no2498 on 2010-07-06
try this program wacam
read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

it also comes in a deb file

hope this works for you as good as it does for me

---

