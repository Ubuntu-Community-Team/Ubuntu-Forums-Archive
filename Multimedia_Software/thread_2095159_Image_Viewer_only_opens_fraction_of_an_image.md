---
title: "Image Viewer only opens fraction of an image"
date: 2012-12-16
forum: Multimedia Software
---

### Post by leigel3 on 2012-12-16
Many images are only partially loading in the default Image Viewer  application.  All of the problematic files seem to be .jpg's and they  all open in Gimp just fine.

I've looked around for similar threads and launchpad entries, but I can't seem to find anything.  I'm running 12.04 LTS.

I attached an image demonstrating the issue.

Any ideas?

Thanks,
Leighton

---

### Post by royph on 2012-12-16
I had the same problem and couldn't seem to fix it either so I installed Shotwell from Software Center and that works just fine.

---

### Post by leigel3 on 2013-01-17
anyone else experiencing this?  i've been using *shotwell*, as suggested, but i don't like it as much for simply viewing images.

---

### Post by ManamiVixen on 2013-01-17
Do you have libjpegturbo9 installed?

---

### Post by leigel3 on 2013-01-18
> **ManamiVixen said:**
> Do you have libjpegturbo9 installed?

Never heard of that, but:

```

leighton@gelderbury:~$ sudo apt-get install libjpegturbo9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libjpegturbo9

```Do you think that could be the issue?

---

### Post by ManamiVixen on 2013-01-18
No, thats a good thing. Libjpeg-turbo9 is causing compatibility problems. But you don't have it. Good. 

You should have libjpeg-turbo8 installed though. The current release. 

Try renaming the .jpg to .png :) Sometimes they are saved with the wrong suffix.

---

### Post by eric-yorba on 2013-01-18
> **ManamiVixen said:**
> Try renaming the .jpg to .png :) Sometimes they are saved with the wrong suffix.

Facebook doesn't store images as PNG, it's definitely a JPEG.

(By the way, when posting a screenshot of a Facebook photo, it's best not to have the filename in the photo since it contains your profile ID!)

---

