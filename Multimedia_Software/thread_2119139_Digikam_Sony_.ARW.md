---
title: "Digikam Sony .ARW"
date: 2013-02-23
forum: Multimedia Software
---

### Post by abhaysahai on 2013-02-23
Hi, 
I am returning to Ubuntu after a long time and it simply feels great. 
Loved the entire experince, right from the Live CD. Still taking my time to adjust from  and get used to the corresponding software. 
One major issue I have is with my Raw files. 

I used to process them in lightroom and know that Digikam is a very good alternative. 
However, it cannot read Sony .ARW files.   Dolphin cannot even display the thumnails of .ARW files. 

Any help would be great in taking me away from mandatory Lightroom access.

---

### Post by csillva on 2013-02-23
Can Lightroom convert those arw files to dng? That should solve both problems.

---

### Post by schragge on 2013-02-23
A quick *axi-cache search raw* gives me 310 results. At the top are:
> 
100% ufraw - standalone importer for raw camera images
98% rawstudio - RAW image converter
96% ufraw-batch - batch importer for raw camera images
96% rawtherapee - Free RAW converter and digital photo processing software
96% gimp-ufraw - gimp importer for raw camera images
95% libraw-bin - raw image decoder library (tools)


[highlight]Update 1.[/highlight]
Just to be sure, do you have *kipi-plugins* installed?

[highlight]Update 2.[/highlight]
Be aware that by converting ARW to DNG you'll lose some metadata as described [here](http://www.dyxum.com/dforum/forum_posts.asp?TID=48936&PID=538748&title=dng-vs-arw#538748).

---

### Post by abhaysahai on 2013-02-23
> **csillva said:**
> Can Lightroom convert those arw files to dng? That should solve both problems.

I do not want to first login to windows and use lightroom to convert to raw and later login to Ubuntu.  :p

Thanks schragge. Now I am using RawStudio to convert my Raw files. and later manage them with digikam. Not a very good solution, but its workable. Apprecite the help:D

---

### Post by schragge on 2013-02-23
Well, AFAIK, digikam makes use of kipi-plugins. There's definitely a RAW-to-DNG converter in kipi-plugins:

[CENTER][[IMG]http://farm4.staticflickr.com/3248/3106260869_c8f9186199_m.jpg[/IMG]]("http://www.flickr.com/photos/digikam/3106260869/sizes/o/")
[/CENTER]

---

### Post by abhaysahai on 2013-02-23
Thanks schragge. 
You are right Mate. kipi-plugins simply works. 

All it took was to reboot and now my Digikam can process all new RAW images that I am importing from the camera.  Actually I had rebooted to Windows to process and export the RAW files. On reboot I was greated with the ability in DigiKam to read and process RAW Files. 

I always thought that in Linux I do not reboot untill a new Kernel install  :D. 

I have an 5 year old Sony Vaio and lightroom was very sluggish on it. DigiKam simply flies in comparison. Alwasy knew Linux is faster, but the reality blew me away. Happy to be back.

---

