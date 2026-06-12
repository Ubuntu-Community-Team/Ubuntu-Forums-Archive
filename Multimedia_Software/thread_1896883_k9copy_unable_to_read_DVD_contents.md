---
title: "k9copy unable to read DVD contents"
date: 2011-12-18
forum: Multimedia Software
---

### Post by CaptinGoogle on 2011-12-18
I bought a copy of Pirates of the Caribbean 4 and am now trying to make a backup copy and encode it. However, whenever I try to use k9copy it crashes and gives me this error; "Executable: k9copy PID: 2304 Signal: Segmentation fault (11)".

I would assume this has something to do with Disney movies because I am able to make an ISO image of the DVD using Brasero and can encode other movies that are encrypted.

I've tried using DVDFab on Windows, which worked but put an annoying water mark in the movie.

---

### Post by hansdown on 2011-12-18
Welcome to the forum, CaptinGoogle.

Post #5 of this link, seems to be helpful.

[http://ubuntuforums.org/showthread.php?t=1711961](http://ubuntuforums.org/showthread.php?t=1711961)

---

### Post by CaptinGoogle on 2011-12-18
Thank you hansdown. I did an extensive search and found that as well. It sadly has not helped.

---

### Post by hansdown on 2011-12-18
> **CaptinGoogle said:**
> Thank you hansdown. I did an extensive search and found that as well. It sadly has not helped.

Thanks for your patience, CaptinGoogle.

Also, for the feedback.

There have been some bug reports filed so, maybe something soon?

---

### Post by CaptinGoogle on 2011-12-18
Well I'm not in a rush because it is Pirates of the Caribbean 4 so it's probably not worth my disk space. :p

Regardless I did try this on Dvd::rip as well so I believe, in my limited understanding of Linux, that the error resides somewhere in the libdvdcss2 library. However, I could be very far off.

I wonder how one would go about fixing this on their own. That's why I migrated to Linux so I no longer have to be dependent on people for support as much and can help out the community more than just making money donations.

---

### Post by hansdown on 2011-12-18
:D> **CaptinGoogle said:**
> Well I'm not in a rush because it is Pirates of the Caribbean 4 so it's probably not worth my disk space. 

Regardless I did try this on Dvd::rip as well so I believe, in my limited understanding of Linux, that the error resides somewhere in the libdvdcss2 library. However, I could be very far off.

I wonder how one would go about fixing this on their own. That's why I migrated to Linux so I no longer have to be dependent on people for support as much and can help out the community more than just making money donations.

You speak wisdom, my friend. :D

If you have the libdvdcss2 library installed, you have no worry, as it is very well maintained.

---

### Post by CaptinGoogle on 2011-12-18
Actually I take back what I said about the error being in the libdvdcss2 library. Going over the DVD::rip error again it says; "Job 'Read TOC (lsdvd)' failed..." So now I believe it's actually in the lsdvd library.

---

### Post by hansdown on 2011-12-18
> **CaptinGoogle said:**
> Actually I take back what I said about the error being in the libdvdcss2 library. Going over the DVD::rip error again it says; "Job 'Read TOC (lsdvd)' failed..." So now I believe it's actually in the lsdvd library.

There is a recurring bug, that escapes a fix.

[https://bugs.launchpad.net/ubuntu/+source/dvdrip/+bug/357614](https://bugs.launchpad.net/ubuntu/+source/dvdrip/+bug/357614)

---

### Post by CaptinGoogle on 2011-12-18
Pitty. Well thank you for replying and making suggestions.

---

### Post by inobe on 2011-12-18
i think it's the app and not the libs.

if you want to encode to a certain format later, why not try handbrake.

if you wish to just extract the content and create an .iso, your onboard apps can do that.

---

### Post by CaptinGoogle on 2011-12-18
> **inobe said:**
> i think it's the app and not the libs.

if you want to encode to a certain format later, why not try handbrake.

if you wish to just extract the content and create an .iso, your onboard apps can do that.
Thank you for that suggestion, however, as I mentioned above I'm not having trouble making an ISO image of the DVD. When I use either k9copy or DVD::Rip they both have trouble reading the contents of the either DVD or ISO.

Also I tried to install Handbrake as per your suggestion and it seems when trying to add the repository some links in it have gone dead.

EDIT: I found this page: [http://ubuntuforums.org/showthread.php?t=1876100](http://ubuntuforums.org/showthread.php?t=1876100) and was able to install Handbrake. At present it seems somewhat able to read the ISO. I'll keep updating as progress continues.

Update: I attempted to encode the movie straight from the ISO image and that failed. Next I tried to encode straight from the DVD, which has worked to some extent. Right now the output is of extremely poor quality (very pixelated). The video also includes the number of the title on the video which is rather annoying. I believe I made in error in allowing the "QP" being set to twenty instead of something between 0 and 8 as was recommended.

---

### Post by CaptinGoogle on 2011-12-19
I got it working! Thank you very much inobe your suggestion was of great help and greatly appreciated. Thank you hansdown for making suggestions and trying to help.

Here was my process to get it encoded properly.

After installing Handbrake with help from this thread; [http://ubuntuforums.org/showthread.php?t=1876100](http://ubuntuforums.org/showthread.php?t=1876100) , I used these settings:
I used MPEG-4 (FFmpeg) for the video encoder.

I used 23.967 (NTSC FILM) for the framrate.

I set the QP to 7.

I used lame for an mp3 audio encoder. I don't think that was necessary though.

I made sure the chapters marker was unchecked.

I made the video output .mkv

That's it. I hope this helps anyone else who has had issues like mine.

As a side note my opinion of Handbrake isn't that high. It is a bit buggy and it was slightly bothersome that it could not read well directly from the ISO, although anyone could always use Gmount-iso and then proceed that way.
Also the quality of the video isn't that fantastic, however, my screen resolution is 1920*1080 so it should look fine on my old cathode-ray television. I also looked at some other videos that I encoded with k9copy and they have the same amount of video quality decay.

---

### Post by inobe on 2011-12-19
what are your system specs?

a side note: handbrake is a 3rd party app, they'll appreciate a bug report.

[https://forum.handbrake.fr/viewtopic.php?f=12&t=18906](https://forum.handbrake.fr/viewtopic.php?f=12&t=18906)

they also have a forum loaded with information, more than enough that'll get you excellent quality jobs.

[https://forum.handbrake.fr/](https://forum.handbrake.fr/)

the manual is a great start.

[https://trac.handbrake.fr/wiki/HandBrakeGuide](https://trac.handbrake.fr/wiki/HandBrakeGuide)

finally the ubuntu docs on restricted formats.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by CaptinGoogle on 2011-12-19
I have an 3x AMD Athlon(tm) II X3 450 processor with a Geforce 9500 GT video card and 8 gigabytes of RAM. So I don't think the problems are because of my computer; I would think.

I am bit reluctant to file a bug report because the install didn't go very nicely when I did. The repositories I added had trouble because some of the links have since gone dead.

Thank you for the links though especially with the manual. That should come in handy.

---

