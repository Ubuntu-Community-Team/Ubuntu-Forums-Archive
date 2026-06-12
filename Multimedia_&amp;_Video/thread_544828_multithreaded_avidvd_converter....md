---
title: "multithreaded avi/dvd converter..."
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by freefall235 on 2007-09-06
hey all, 

have used DeVeDe to convert a divx file to dvd iso, however it does not appear to be multi-threaded... (hour n 25 mins to do what ConvertXToDvd does in about 15 mins...)... I have a Q6600 (quad core), and want to use it to its potential...

so, what im wondering is, does Tovid support multi threading? I will give this a try tonight...also, is there a way to convert the video file straight to dvd, without a menu?? and then have the output as a dvd iso file (like DeVeDe?), but willing to settle for auto splitting of files, and placment into VIDEO_TS folder...

Cheers

EDIT: does not have to be gui based, can be command line, as long as above, multithreaded, no menu and dvd-iso preferable, but willing to settle for auto splitting of files, and placment into VIDEO_TS folder...

---

### Post by distroman on 2007-09-07
[http://ubuntuforums.org/showthread.php?t=337268](http://ubuntuforums.org/showthread.php?t=337268)

15 min is fast but then Q6600 is sweet. :)

I mostly use avidemux gives you lots of choice, can do a dvd in ~30 min with 2 passes. AMD +5200 X2.

[http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/](http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/)
For vob files or/and iso.

gl

---

### Post by freefall235 on 2007-09-07
> **distroman said:**
> [http://ubuntuforums.org/showthread.php?t=337268](http://ubuntuforums.org/showthread.php?t=337268)

15 min is fast but then Q6600 is sweet. :)

I mostly use avidemux gives you lots of choice, can do a dvd in ~30 min with 2 passes. AMD +5200 X2.

[http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/](http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/)
For vob files or/and iso.

gl


you sir, are a legend...i will be trying that walkthrough out tonight...

now i just need to learn to shell script to automate!!!

thanks..

---

### Post by lhaeh on 2008-04-08
You can make DeVeDe multithreaded pretty easily, just change the parameters it sends to Mencoder under the advanced options.

This gives you two threads:
-lavcopts threads=2

---

