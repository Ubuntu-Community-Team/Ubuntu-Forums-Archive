---
title: "Editing Canon .CR2 RAW files"
date: 2008-12-13
forum: Multimedia Software
---

### Post by lift_test on 2008-12-13
Is there a package that can edit  Canon (EOS 450D) files?  F-Spot View can display them but obviously no good for editing.

---

### Post by Route490 on 2008-12-13
Hey,

UFRAW is probably your best bet, can be used as a plugin for GIMP.

[http://ufraw.sourceforge.net/]("http://ufraw.sourceforge.net/")

Or can be installed through the package manager.

Enjoi

Route490

---

### Post by lift_test on 2008-12-13
Thanks, I'll try that.

---

### Post by lift_test on 2008-12-13
Works, but colours are no good and haven't been able to correct so far.

---

### Post by Route490 on 2008-12-14
Yeah, I had problems getting used to it as well.  Unfortunately not as easy to use as photoshop, It does work but there may be better/easier software out there...

Route490

---

### Post by woodbrick on 2009-01-14
I have major problem with UFRaw and my new Canon EOs 450D (Rebel Xsi in some countries). I installed UFR from repositories no problem (started with the GIMP plugin, then tried stand alone). .CR2 images open no problem, but they look awful. Most with normal exposure are at least 50% over-exposed when opened with UFRaw. Most of my images are just one ugly shade of pink when viewed in UFRaw, yet they look complely normal in Canon's software in windows. I even tried importing RAW files with EOS Utility (Canons supplied software)in Windows, then viewing with UFRaw in Linux, same result. Finally I installed Bibble pro (trial vers) to see what it did: it works fine, but does not interface with GIMP as well as UFR does. This is way beyond any minor colour balance issue. UFR just does not seem to be interpreting my CR2 files at all properly. Is anyone else having a similar issue?

I am using Intrpid i386 Desktop with AMD Athlon 64.

Any help apppreciated, as I had nearly walked away from Windows completely, now it is reeling me back in...

---

### Post by hiethan592 on 2009-01-14
Been a while since I have done this but somewhere in there is a setting for the format.  Tinker with that and it might solve your problem.  That program does not automatically recognize the color format.  Only a few options if I remember right so it shouldn't be to hard to try

---

### Post by woodbrick on 2009-01-16
I couldn't find anything to do with "Format." There is a settings button with a "log" tab. This contained a (possibly) insightful piece of infromation: 


ufraw_open: w:4312 h:2876 curvesize:0
Reseting Exif.Image.Orientation from '1'  to '1'
EXIF data read using exiv2, buflen 18733
Warning: Size 12108 of Exif.Canon.0x4002 exceeds 4096 bytes limit. Not decoded.
Warning: Size 15988 of Exif.Canon.0x4005 exceeds 4096 bytes limit. Not decoded.


I did find another post 
[http://staffwww.itn.liu.se/~karlu/div/howto/ufraw_with_canonSLR.php](http://staffwww.itn.liu.se/~karlu/div/howto/ufraw_with_canonSLR.php) 

with instructions for loading my camera's colour profile into the "input color profile" section of UFRaw. 

I couldn't find the .icc file on my disk, but I managed to download the file elsewhere. 

This has helped a little, but the images are still far from usable. 

The other option I have is to install Canons software using wine. This is not a preferred option though. There just *must* be an open source solltion for loading RAW files from this very popular camera...??

---

### Post by skao on 2009-03-08
Hi Everyone

I have the same problem with most of you before. The ufRaw come from ubuntu is an old version which gave you a pink overcast when you open the canon CR2 file. Try the latest from the ufRaw web site (0.15), look like it fix that problem. ufRaw provides ubuntu install package. 

The problem I have now is that the image display in ufRaw is more orange and darker than the JPGE version of the same image (I use L + RAW when I took that photo). But this could be the colour profile problem. I will load the ICC for my 450D in to ufRaw and see what happen. I think if you use ufRaw 0.13 (the one from ubuntu) even you load the colour profile it may not help much, I think you still will have that pink overcast.

One more thing. if you are using Ubuntu 8.10, ufRaw may will complain that it cannot find a old version of the require library (This happen to me but I did a upgrade from 8.04 to 8.10 through Synaptic, not quite sure this will happen with fresh install). Ubuntu 8.10 install the version 3 of the library but ufRaw require version 2. Just ask google and you will find the version 2 of the library for Ubuntu 8.10. Just install it and ufRaw will work (from memory that package also come form ubuntu as well).

Regards,
Stephen

---

### Post by cotcot on 2009-03-08
Couple of alternatives for ufraw : [[COLOR="Red"]rawtherapee[/COLOR]]("http://www.rawtherapee.com/?mitem=3") and [[COLOR="Red"]rawstudio[/COLOR]]("http://rawstudio.org/")

---

### Post by woodbrick on 2009-03-09
Hi thanks for reply. 

skao:

I completely removed UFR 0.13 and installed 0.15 deb package. This did improve the results, but the images are still unusable. They are now underexposed and 'green' rather then over-exposed and red! No trouble installing or running though.

cotcot: 

I have tried rawstudio, but it does not seem to interface with Gimp. When I click file > export to gimp I get these messsages from Gimp:

Execution error for procedure 'file-tiff-load':
Could not open '/tmp/.rawstudio_6416.tif' for reading: No such file or directory

Opening '/tmp/.rawstudio_6416.tif' failed: Could not open '/tmp/.rawstudio_6416.tif' for reading: No such file or directory. 

In any case, ufraw looks to be the more comprehensive "pre-editing" software. If only it worked!!! 


I will try rawtherapee and report back.

Cheers,

-Woody

---

### Post by RichardCL on 2009-03-09
Hi,

My setup is working fine I'm using the following setup:

EOS 40D saving in RAW +L
Colour map in camera: sRGB

Ubuntu 8.10 x64 desktop edition
Three different computers, core4quad, netbook and Cytron laptop
Always installed the vendor monitor driver when asked

GIMP 2.6.1 with all possible plugins (from the standard repositories)
UFRAW 0.13 as a plugin (also from the respository)

I've not pre-set any colour pallet

I'm opening the images with open with and GIMP from Nautilus.

UFRAW also used DCRaw for the conversion. You'll need to check that it is installed and up to date.


A strange pink colour could be a wrong white balance or green level setting. It may also be worth checking the colour profile in the camera is set to sRGB and not Adobe.

Let me know if I can help by reading out any of my settings.


Richard

---

### Post by woodbrick on 2009-03-19
Hello again and sorry for the late reply (life!) 

[QUOTE=RichardCL;6866188]Hi,

My setup is working fine I'm using the following setup:

EOS 40D saving in RAW +L
Colour map in camera: sRGB

Ubuntu 8.10 x64 desktop edition
Three different computers, core4quad, netbook and Cytron laptop
Always installed the vendor monitor driver when asked

I am using i386 edition,and a different model camera, but otherwise the same. Definitely sRGB on the (EOS450) camera. My processor is AMD 64, but I have no problem viewing the .CR2 file in nautilus (perfect "out of the box!":)). When I come to open/edit any .CR2 file in GIMP or Rawstudio (with GIMP 2.6.1,UFRaw 0.15, DCRAW 8.80-1, RAW studio 1.1-1 or RAW therapy ), all of them have problems with a capital P. 

The interesting thing is: RAWTherapy produces exactly the same results as did GIMP/UFRAW before I took skao's advice and installed UFRAW vers 0.15. Pink and overexposed. I am encouraged to hear that it's working for RichardCL on his 40D though. That means there must be an answer.....

PLEASE let me know if I can supply more info and once again apologies for taking a week. 

-Woody

---

### Post by zubrug on 2009-03-21
digikam has support for raw

---

### Post by woodbrick on 2009-03-26
Thanks to all. I have tried all suggestions, and the only positive step I have made is that *most* have the same results. **UFRaw ** (stand alone vers 0.13, from repositories), **Raw Therapee** (vers 2.3 from repositories) and **DigiCam** (from repositories) all decode my .CR2 files with the same overexposed, pinkish tone.

As per Skao's suggestion, I tried UfRAw vers 0.15 (as a gimp plugin, from UFRaw website). This produces different colour tone results, but they are still a long way off. 

Finally there is Raw Studio. The colour results in Raw Studio are much better, but with Raw Studio there are problems exporting images to GIMP, as noted above. 

I am slightly encouraged that most programs are having the same trouble; to my mind that means there must be a color setting "deeper" inside ubuntu that is just not readiing my camera'a RAW data correctly. But I am at a loss as to guess where to look for the problem. 

Any suggestions are greatly appreciated.

---

### Post by dtakamori on 2009-04-07
UFRaw 0.15 on Hardy from getdeb worked fine for me with my Canon 450D (XSi). :)  Hope the rest of you are able to work things out!

---

### Post by amoun on 2009-07-17
Using hardy I have the same. All the earlier mentioned gui's UFRAW etc use the dcraw engine.

I am unistalling my versions as they are too old maybe. ufraw was 1.3 not 1.5 etc.

Will get back with update :)

---

### Post by woodbrick on 2009-07-19
Hi  Amoun,

Thanks for posting. I had just about given up on photo-editing in Ubuntu. I upgraded to 9.04, but this has not changed the situation. Are you saying you have the same bad colour/tone results as I have described above? Cheers.


-

---

### Post by graphguru on 2009-09-07
Raw Therapee 2.4 works with my Canon t1i cr2 files. Not available from Ubuntu or Debian resources so you have to install from [http://www.rawtherapee.com/?mitem=3](http://www.rawtherapee.com/?mitem=3) as a .tgz file. I too was about to give up on Ubuntu and Gimp. Lost a lot of time figuring a way around it.

Unfortunately, as it installs outside the package manager, the desktop environment is not aware of it. Furthermore, you have to save the file from Raw Therapee and reopen it in Gimp.

Graphguru

---

### Post by stafio on 2009-10-21
There is a .deb of Raw Therapee 2.3 [on their site]("http://www.rawtherapee.com/?mitem=3&artid=3"). It's a version behind the newest, but at least you get the benefits of installing a .deb.

---

### Post by graphguru on 2010-01-27
> **stafio said:**
> There is a .deb of Raw Therapee 2.3 [on their site]("http://www.rawtherapee.com/?mitem=3&artid=3"). It's a version behind the newest, but at least you get the benefits of installing a .deb.

I can't get it to work for me. This mess has been dragging on for far too long. Let me post a picture from the Canon t1i  in the raw (cr2) format and see if someone can help. I upgraded to 9.10 and am reduced to translating a cr2 to a dng then opening that. That's a lossy process.

Graphguru

---

### Post by no2498 on 2010-01-27
you may need to report a bug
the colors on my webcam's are backwards on 910
they have  set them to grb
not rgb
so this may be what your getting
on 804 there good

---

### Post by graphguru on 2010-01-29
> **no2498 said:**
> you may need to report a bug
the colors on my webcam's are backwards on 910
they have  set them to grb
not rgb
so this may be what your getting
on 804 there good

Don't think so, Had the same problem with 9.04 with all the raw converters except rawtherapee 2.4 (2.3 doesn't work, haven't tried 2.41) Both 2.4 and 2.41 were/are available as .tgz and do not export directly to gimp. You have to save the file and reopen it.

Graphguru

---

### Post by hotani on 2010-03-12
I just successfully converted some CR2 images I got from my friend who has a Canon camera. I use a Nikon D40 and jpg - never knew the headaches involved with raw images on linux till now!

Anyway. I was able to convert a few test images from CR2 to JPG via batch processing in digiKam.

1- select the pics to convert in digiKam, right-click and choose "batch queue manager" -> "add to current queue" (or new, existing, whatever...)
2- open batch queue manager from 'tools' menu
3- in 'queues' box, you should see all the images you selected. Choose a target dir in the lower left box, then choose "convert to JPEG" from the lower right box and drag it into the "assigned tools" box
4- click "Run" and wait....

This worked well for me after trying and failing to use all the other tools listed in this and many other threads on the same topic. Hope this helps.

BTW: the original CR2 images were 25MB EACH. The converted JPEG (85% compression or so) came out to 2MB. Exactly what I was looking for.

---

### Post by graphguru on 2010-03-17
I think the problem is particular to the Canon t1i, I don't know about the t2i.

I'll attempt to attach an image, both as a jpg (converted in Windows XP) and the original cr2, I'll have to put the cr2 file up as a tar.gz, but that shouldn't be a problem.

Graphguru

---

### Post by graphguru on 2010-03-17
I can't get past the file size limit.

Graphguru

---

