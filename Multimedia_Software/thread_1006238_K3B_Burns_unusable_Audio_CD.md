---
title: "K3B Burns unusable Audio CD"
date: 2008-12-09
forum: Multimedia Software
---

### Post by Colin@oxford on 2008-12-09
My first attempt at burning an Audio CD appears to have resulted in absolute failure.

I have K3B and a pile of OGG files.  I created a new "Audio CD" project in K3B and dragged my OGG files into it.  Checked that the titles all appeared OK.  Inserted a blank Audio CD-RW (I had one lying around) and pressed "Burn".  It took the expected time (20 mins at 4x). Tried playing in a CD player but got "Disk error".  Put it back into the computer and even K3B does not recognise it.

What have I done wrong?  Can I recover the CD to make it writeable again?

---

### Post by philetus on 2008-12-09
[http://ubuntuforums.org/archive/index.php/t-468271.html](http://ubuntuforums.org/archive/index.php/t-468271.html)

starcraft.man
June 8th, 2007, 04:03 PM
Open up a terminal (Applications Accessories > Terminal) and paste this in:

sudo aptitude install libk3b2-mp3

---

### Post by philetus on 2008-12-09
Possibly a bug affecting K3b

[https://bugs.launchpad.net/ubuntu/+bug/295795](https://bugs.launchpad.net/ubuntu/+bug/295795)

---

### Post by Colin@oxford on 2008-12-09
Not using MP3, so do not see how loading that is going to help. 


[https://bugs.launchpad.net/ubuntu/+bug/295795](https://bugs.launchpad.net/ubuntu/+bug/295795) might have relevance, although I do not know how - I am on Hardy.

Problem fixed since when I rebooted, K3B did recognise the disc and was able to delete everything and start again - this time with success.

---

