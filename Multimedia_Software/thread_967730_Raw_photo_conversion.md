---
title: "Raw photo conversion"
date: 2008-11-02
forum: Multimedia Software
---

### Post by nomad421 on 2008-11-02
Hello,

  I'm using ubuntu 8.10 (64-bit), though it shouldn't really matter since I compiled dcraw from source.  I shot in RAW for the first time yesterday on my Canon EOS 50D (actually, I used sRAW1). The 50D is on the supported list of cameras in the latest version of DCRAW (and all of tools that use it like UFRaw and the latest digikam). Anyway, long story short, I can't convert or view my raw files. The latest version of dcraw gives the following message:
"Cannot decode file"

followed by the filename. I tried using the -i -v option to get just the photo info and I get the following:
Filename: /home/rob/Pictures/50D_Test_Album/CentennialPark2/IMG_0340.CR2
Timestamp: Sat Nov 1 14:28:39 2008
Camera: Canon EOS 50D
ISO speed: 400
Shutter: 1/128.0 sec
Aperture: f/25.8
Focal length: 65.0 mm
Embedded ICC profile: no
Number of raw images: 0
Thumb size: 4752 x 3168
Full size: 596 x 396

This looks very wrong, as it says there are 0 raw images, and the thumb size is larger than the full size! Also, the aperture of f/25.8 is clearly incorrect (maybe it should read f/2-5.8 ?). Anyway, I'd really like to get a look at these pictures, so any input you have would be very helpful.

Thanks,
Rob

---

### Post by Idefix82 on 2008-11-02
I seem to remember that I also had problems with dcraw. Try ufraw. I don't know about Intrepid but in Hardy it's in the repositories. There is also a plugin based on ufraw for GIMP - very handy!

---

### Post by nomad421 on 2008-11-02
I actually tried ufraw as well.  However, it's based on dcraw, so no cigar :(.

---

### Post by Idefix82 on 2008-11-02
So it is and you even wrote in your first post, sorry! I am afraid, I haven't experienced this problem before and have no idea how to handle it. However, reading the image information should really be quite straightforward so I am wondering if the camera is saving the image correctly. Have you got software for this camera? You could try to run it in WINE.

---

### Post by civetta on 2008-11-10
Hey,

You can run cannon digital photo pro on wine. It works reasonably well. I got some problems with windows wanting to move to the edge of the screen when I didn't want them to!

Otherwise, the latest version of ufraw 0.14.1 is out. Maybe see if that does it?

---

### Post by Jindro on 2008-11-10
same problem here.
Ufraw 1.4.1 (dcraw?) works for RAW but not for SRAW1

---

### Post by Jindro on 2009-01-05
problerm solved by [http://ufraw.sourceforge.net/](http://ufraw.sourceforge.net/) 24/12/2008 - UFRaw-0.15 released, based on DCRaw v 8.89.

---

### Post by woodbrick on 2009-01-14
I have major problem with UFRaw and my new Canon EOs 450D (Rebel Xsi in some countries). I installed UFR from repositories no problem (started with the GIMP plugin, then tried stand alone). .CR2 images open no problem, but they look awful. Most with normal exposure are at least 50% over-exposed when opened with UFRaw. Most of my images are just one ugly shade of pink when viewed in UFRaw, yet they look complely normal in Canon's software in windows. I even tried importing RAW files with EOS Utility (Canons supplied software)in Windows, then viewing with UFRaw in Linux, same result. Finally I installed Bibble pro (trial vers) to see what it did: it works fine, but does not interface with GIMP as well as UFR does. This is way beyond any minor colour balance issue. UFR just does not seem to be interpreting my CR2 files at all properly. Is anyone else having a similar issue?

I am using Intrpid i386 Desktop with AMD Athlon 64. 

Any help apppreciated, as I had nearly walked away from Windows completely, now it is reeling me back in...

---

### Post by Hraefn on 2009-04-20
I can't seem to find it in the repositories, but RawTherapee is a decent program for photo manipulation and RAW formating.  It will also let you convert RAW.

I'm just getting used to it myself, so I don't have a lot more than that to offer, but you can find it here: [http://www.rawtherapee.com/]("http://www.rawtherapee.com/")

Good Luck!

---

