---
title: "Picture recovery program on Karmic Koala 9.10"
date: 2010-11-19
forum: Multimedia Software
---

### Post by Newbie_777 on 2010-11-19
[SIZE=2]I am looking for a program that would be able to recover some of  my pictures. They seem to be corrupt. I know that there are several  programs, really quite simple to use, to download from the web such as "[/SIZE][SIZE=2]Art Plus Digital Photo Recovery" and "PixRecovery". I was wondering if there are similar programs out there that can be installed on Ubuntu? Also, I have to mention it, when I try to open them with the "Image Viewer" an error message pops out which says : Could not load image 'picture.JPG'. Beneath that there is also this : Error interpreting JPEG image file (Improper call to JPEG library in state 200). Can someone help me out?
[/SIZE]

---

### Post by mikewhatever on 2010-11-20
A quick scan of the repositories revealed 'recoverjpeg', a "tool to recover jpeg images". Not really sure it will suit you, as it's a command line program, but there it is.

---

### Post by Newbie_777 on 2010-11-20
Thank you. I found it. But after the installation was complete I couldn't find it anywhere.

---

### Post by Backharlow on 2010-11-20
recoverjpeg is a terminal app.
```
man recoverjpeg
```
does offer a decent manual for using it.

---

### Post by Newbie_777 on 2010-11-20
Oh, I figured it out. Thanks, but it didn't specify which command to use to recover images which are already located in a folder, on the desktop.

---

### Post by wilee-nilee on 2010-11-21
Check out photorec it is in testdisc it is in the repos I think you just have to have the universal repo ticked to get it, I forget which one as I op[en all of them basically. here is a link to get you started for info.
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

