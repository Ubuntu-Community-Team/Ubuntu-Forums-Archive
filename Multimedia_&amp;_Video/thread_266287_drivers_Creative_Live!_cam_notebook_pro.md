---
title: "drivers Creative Live! cam notebook pro"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by infinityAdm on 2006-09-27
Does anyone know what driver do I need for this webcam?
I tried spca50xx and pwc, but it seems that they don't work.
the product id is 0x4051 if it can be useful.
I looked at some howto but with no help and I didn't find this model on nay lists of supported webcams.

---

### Post by ddoxey on 2007-01-06
I have same model camera.
I would be interested to know if you've managed to get this webcam working.

---

### Post by spyrakos on 2007-02-06
Camera is supposed to work according to compatibility list here --> [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

However, mine is being recognized by the system as a Bluetooth device :confused: 

I suppose that a udev rule should be able to fix that, however I have no idea how to make one, and I would greatly appreciate any advice.

---

### Post by Marvin on 2007-02-11
Hello,

I have a creative Live! Cam Notebook Pro working. 
Vendor Id: 041e Product Id: 4051 
Haven't tested much but got an image out of it with camE.

Have you the right modules compiled and loaded?
It needs the gspca kernel module loaded. Not the spca5xx from
the same package.

---

### Post by cookiefreak on 2007-05-01
What exacly i have to do to make the camera work?

---

### Post by sdb2028 on 2007-10-07
Anyone still working this thread?
I have downloaded the tarball for gspca, howevwer am having difuculty installing it. Are there insallation instructions somewhere? Any help would be appreciated. Thanks

---

### Post by sdb2028 on 2007-10-07
I have found the answer to my question. If anyone else ends up here, Go to [http://ubuntuforums.org/showthread.php?t=322218](http://ubuntuforums.org/showthread.php?t=322218) and check message #1. I followed the directions exactly, except to uncompress the tarball use - tar zxvf gspcav1-20070508.tar.gz as a typo occured and inserted an extra g in the initial insructions. I used this for a Creative Live! Notebook Pro VF0250 and it works fine.

---

