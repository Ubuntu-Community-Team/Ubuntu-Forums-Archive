---
title: "[SOLVED] PSP video convertion, what I am missing ?"
date: 2007-12-17
forum: Multimedia Production
---

### Post by frodon on 2007-12-17
I bought lately a PSP and enjoy it. However i have some difficulties to encode videos in the psp format under linux.
What i'm looking for is a solution_ which use only the packages of the official repositories_.

I tried ffmpeg with commands like :
```
ffmpeg -i video.avi -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4
```
Or mencoder with commands like :
```
mencoder INPUT -sws 9 -vf scale=480:-10,harddup,unsharp=l3x3:0.7,expand=480:272 -oac faac -faacopts br=128:mpeg=4:object=2:raw -ovc x264 -x264encopts bitrate=650:global_header:partitions=all:trellis=1:vbv_maxrate=768:vbv_bufsize=2000:level_idc=30 -of lavf -lavfopts format=psp -o OUTPUT
```

However it always fails saying that i'm using an unsupported output format or that i don't have the needed library to encode it.

I'm pretty sure i'm missing a library but can't find which one, i believe that some users here got this working without using external repositories.

If anyone have an idea or experience on this it is welcome :)

Thanks

---

### Post by lgambett on 2007-12-17
Tried this ?
[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

---

### Post by frodon on 2007-12-17
> **lgambett said:**
> Tried this ?
[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)Sorry but when i said things in the official repositories that mean things in the ubuntu repositories. I know pspvc and i don't want it on my computer as i always avoid the use of third party apps when they are not needed. So i would rather explore all the possibilities i have inside the ubuntu repositories before considering any third party stuff.

---

### Post by philc on 2007-12-17
I think you'll need to enable extra libraries when you configure FFMPEG.

See here for how I did it:
[http://slashdot.org/~PhillC/journal/190344](http://slashdot.org/~PhillC/journal/190344)

I can see from your Mencoder command that you're trying to use AAC audio and X264 for the video.

Things like libxvidcore4-dev, libx264-dev and libfaac-dev are in Multiverse.

I used an SVN build of FFMPEG, but if you want to use the one in the Ubuntu repository, then you may need to enable libraries in a slightly different way.

Try this link for a tutorial on installing FFMPEG on Feisty:

[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

It shows x264 being enabled with --enable-x264, whereas I had to --enable-libx264. Xvid was --enable-xvid, whereas I needed --enable-xvidcore4

---

### Post by frodon on 2007-12-17
I know but my wish is to use only things present in the ubuntu repositories as i know that some get it to work without going outside the ubuntu repositories so if it's possible i would prefer to avoid using an svn version of ffmpeg.
However if there's really no way to get this to work without recompiling ffmpeg then maybe i will do this, i will check my x264 libraries.

---

### Post by philc on 2007-12-17
OK, I'm not sure what's enabled by default with the FFMPEG already in the repository. Apologies for not reading your message in enough detail.

One thing that might be worth trying is to have a look at PiTiVi. I'm not sure if it's part of the standard Ubuntu 7.10, but it is part of Ubuntu Studio 7.10 and I'm pretty sure you can install through Synaptic.

Open PiTiVi, then select the Render option and Modify. In the Export To section at the bottom you will have a number of options for container, audio codec and video codec. This should show you what's available on your system. If x264 and aac is in there, you're good to go I guess.

I've not actually used PiTiVi to export files as some bugs prevented me getting the quality and options I needed. However, I do recall the Render option list being greatly enhanced after I'd installed FFMPEG from SVN, so there is a correlation for sure.

---

### Post by frodon on 2007-12-17
Avidemux 2.4 will be great too, i know they have implemented better x264 support and even advanced PSP profile, unfortunately they are still working on it and only a preview package is available.
Never heard of PiTiVi, i will check this too.

Thanks ;)

---

### Post by Creative2 on 2007-12-17
ffmpeg -i video.avi -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

too errors

768k
32k

---

### Post by frodon on 2007-12-17
Is the command working for you with ubuntu ffmpeg version ?

---

### Post by Creative2 on 2007-12-17
i don t know if it works or not but with ffmpeg  2007 you have  to write k

---

### Post by philc on 2007-12-17
> **Creative2 said:**
> i don t know if it works or not but with ffmpeg  2007 you have  to write k

Right. So Frodon's 768 is only 768 bits/s. If you want 768 kilobits/second write 768k or 786432

---

### Post by frodon on 2007-12-17
I tried but that's not the problem, ffmpeg just have no x264 support in the gutsy ubuntu repository.
Anyway i installed the preview of avidemux 2.4 available on getdeb and the psp option is working great so i consider the problem solved even if i had to use a getdeb package.

Thanls a lot for your inputs :)

---

