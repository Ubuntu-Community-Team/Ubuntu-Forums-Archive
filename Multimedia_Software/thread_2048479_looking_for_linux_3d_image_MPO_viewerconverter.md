---
title: "looking for linux 3d image MPO viewer/converter"
date: 2012-08-26
forum: Multimedia Software
---

### Post by rebeltaz on 2012-08-26
I just got a Fujifilm REAL 3D W3 camera. It takes two images and stores them in an MPO file. The software that comes with it is of course Windoze and it refuses to run under WINE or under VirtualBox. 

I have tried Bino 3d as well as plascolin, but I could not get neither to compile under Ubuntu 10.04. Bino is available as a repository, but that is an older version that does not support MPO files. I also tried with gimp, but while it will load an MPO file, it only loads the left image. 

I can use mposplit, combined with gimp and the stereo-anaglyph script I believe, but that is a lot of trouble to go through for each image! 

I need one program that can take an MPO image file, allow you to view the two images as an anaglyph stereo image and/or convert it into a standard 2d image. 

Thanks...

---

### Post by rebeltaz on 2012-09-02
I'm always glad to see when I'm not the only one who doesn't know an answer to a problem... makes me feel not quite so dense :)

---

### Post by karlkoch23 on 2012-09-10
Hi,

finally I hopefully can help someone after having received help myself many times before....

I use StereoPhoto Maker with the mpo files my Sony NEX produces.
I runs very well with wine:

[http://stereo.jpn.org/eng/stphmkr/]("http://stereo.jpn.org/eng/stphmkr/")

Hope this works,
karlkoch23

---

### Post by rebeltaz on 2012-09-10
:) and :( 

I really do appreciate the help... it was starting to feel like a ghost town in this thread! :D

But.... unfortunately that seems to only run under Windoze. While I do have VirtualBox and wine installed, I would really like a native Linux program. 

I will try this under wine and if that doesn't work I'll give it a shot under VirtualBox. It's gotta be better than my current solution :D 

Thank you again and I will update with the results...

---

### Post by rebeltaz on 2012-09-10
Again... Thank You... 

While StereoPhoto Maker isn't a Linux app, it seems to work just fine under wine, so I am as happy a camper as I can be :D

---

### Post by drevorubec on 2013-06-02
For viewing stereo images in many formats (and of course MPO) try Geeqie. Here are testing versions for many distributions [http://download.opensuse.org/repositories/home:/nadvornik:/geeqie:/testing/](http://download.opensuse.org/repositories/home:/nadvornik:/geeqie:/testing/)
I don't know when it will be in official version.
For stereo alignment on Linux try Hugin:
[http://vndlinuxphoto.blogspot.cz/2011/01/stereo-image-alignment-in-hugin.html](http://vndlinuxphoto.blogspot.cz/2011/01/stereo-image-alignment-in-hugin.html)
But this don't work with MPO, only with two jpeg/tiff, so you need StereoPhoto Maker for convert MPO. Maybe imagemagic can help...

---

### Post by rebeltaz on 2013-06-02
> **drevorubec said:**
> For viewing stereo images in many formats (and of course MPO) try Geeqie. Here are testing versions for many distributions [http://download.opensuse.org/repositories/home:/nadvornik:/geeqie:/testing/](http://download.opensuse.org/repositories/home:/nadvornik:/geeqie:/testing/)
I don't know when it will be in official version.
For stereo alignment on Linux try Hugin:
[http://vndlinuxphoto.blogspot.cz/2011/01/stereo-image-alignment-in-hugin.html](http://vndlinuxphoto.blogspot.cz/2011/01/stereo-image-alignment-in-hugin.html)
But this don't work with MPO, only with two jpeg/tiff, so you need StereoPhoto Maker for convert MPO. Maybe imagemagic can help...

Geeqie seems to be a nice program, and while the version on the website (which for some reason is reported as older then the version in the Ubuntu Repositories even though it is newer) does support mpo, it does do (apparently) in side-by-side crosseye format. I would really rather 3d anaglyph - much less eye strain.

StereoPhoto Maker is what I currently have installed under Wine and it works (relatively) well. I would still like a Linux-native program. 

Thank you, though...

---

