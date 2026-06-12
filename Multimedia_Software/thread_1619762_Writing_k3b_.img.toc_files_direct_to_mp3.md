---
title: "Writing k3b .img/.toc files direct to mp3"
date: 2010-11-12
forum: Multimedia Software
---

### Post by elp99jcm on 2010-11-12
I had a set of CDs (audio, Spanish lessons) which a while ago I stored as images on my hard disk using k3b. I now have .img and .toc files stored.

I now want to create mp3 versions of these audio tracks but do not know how to do this. The only option through k3b is to burn a complete CD and then rip the wavs. I have around 10 CDs and do not want to burn 10, just so I can create the mp3s.

Any idea how to do this? I wondered about trying to create a virtual CD drive and writing to that but not sure how.

Any ideas appreciated.

Thanks.

------------------
Some details:
Ubuntu 10.10, k3b v 2.01

---

### Post by Chronon on 2010-11-12
I believe you can use something like acetoneISO (search for acetoneiso in the repos) to mount the image file as a virtual CD and then rip straight from that.

---

### Post by elp99jcm on 2010-11-16
Thanks for the advice, I downloaded acetone iso (now in the ubuntu repo - apt-get install acetoneiso).

However, if I try to do anything with the .img file it is not recognised.

For example, the Image Conversion produces the error "/home/k3b_0.img: The file format is invalid or unsupported."

I have used a few tools to try and convert this .img format, it seems to be that the files produced by k3b are in some proprietary format.

---

### Post by Chronon on 2010-11-16
Apparently some media players can open certain image formats directly: 
[http://ubuntuforums.org/showthread.php?t=149197](http://ubuntuforums.org/showthread.php?t=149197)

You could try opening it directly with mplayer or vlc.  That topic also mentions the possibility of using iat (it's in the repos) to convert the image to a standard ISO.

---

### Post by bulletxt on 2010-11-19
You can't mount those type of images. The only option you have is to burn it with k3b or AcetoneISO (latest 2.3 release).

AcetoneISO warns you about this when creating an image of a CD-Audio...

---

### Post by Chronon on 2010-11-19
That might be true, but AcetoneISO certainly markets itself as being able to mount IMG:
> AcetoneISO will let You mount typical proprietary images formats of the Windows world such as ISO BIN NRG MDF IMG and do plenty of other things. 

Perhaps it can open IMG made from certain sources and not others?

---

### Post by elp99jcm on 2010-11-21
I suspect this refers to the .img (and associated .cue) files produced by CloneCD, rather than k3b.

There are various tools available to work with .img files in Linux, I think this is for cross platform support.

Looks like my only choice is to burn to CD and rip from that, unless, as I suggested before, I can create a virtual CD device (on the filesystem) and write to that, then rip from this file. There is no reason why this would not be possible, I guess it's just not that useful so no body has bothered to write anything to let you do this.

---

### Post by bulletxt on 2010-11-22
You can't mount a CD-Audio image simply because it does not have a filesystem.

That is why you must burn it passing the TOC/CUE file. It's the TOC file that tells cdrdao how to "read" the image and burn it.


So there you go, you can't mount that image because it technically doesn't make any sense :)

---

