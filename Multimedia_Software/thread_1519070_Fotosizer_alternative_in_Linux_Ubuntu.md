---
title: "Fotosizer alternative in Linux Ubuntu"
date: 2010-06-27
forum: Multimedia Software
---

### Post by Abu Azzubair on 2010-06-27
Does anyone know of an alternative to a program that resizes images called "Fotosizer"?

I've been using Ubuntu 10.04 for about 2 months now

But when I was using Windows XP, I always used Fotosizer to enlarge or minimize images, because when I logged into a YouTube account it always wouldn't allow more than 200 KB (Kilo Bytes) for an Icon pic. So I used to use Fotosizer quite often you see

And I just need an alternative, because I depend on Linux Ubuntu 10.04 a lot now

Thanks a lot in advance :)

---

### Post by dv3500ea on 2010-06-27
You can use [GIMP]("apt:gimp") and its 'scale' tool to resize an image. Save it as a jpg file and reduce the quality to make the image take up less space.

---

### Post by Abu Azzubair on 2010-06-27
> **dv3500ea said:**
> You can use [GIMP]("apt:gimp") and its 'scale' tool to resize an image. Save it as a jpg file and reduce the quality to make the image take up less space.
Thanks a million. Honestly that was very helpful, and I will start learning how to use GIMP, because it's already in my mind, I just never knew where to start off from Lol :)

---

### Post by dotpointer on 2011-03-13
Old thread but anyway...

Fotosizer can be run in Ubuntu 10.10 with wine if installing vbrun60sp6.exe (wine vbrun60sp6.exe, also ran it with winetricks... but don't think thats needed).

The runtimes gives error when installing, but Fotosizer will be able to start after that.

It does not look good, select boxes are rendered all black, but it can be used if you know how the program works in Windows.

---

### Post by rubylaser on 2011-03-13
I'd do this with imagemagick, so I didn't have to bother opening a graphics program to resize.  I'd just use imagemagick, and it's convert command.

```
sudo apt-get install imagemagick
```

I'd grab the downsize script...
[http://www.fmwconcepts.com/imagemagick/downloadcounter.php?scriptname=downsize&dirname=downsize]("http://www.fmwconcepts.com/imagemagick/downloadcounter.php?scriptname=downsize&dirname=downsize")

You can see how it works here...
[http://www.fmwconcepts.com/imagemagick/downsize/index.php]("http://www.fmwconcepts.com/imagemagick/downsize/index.php")

That way you can resize to the filesize you'd like exactly.  Scripts are great for repetitive tasks.

---

