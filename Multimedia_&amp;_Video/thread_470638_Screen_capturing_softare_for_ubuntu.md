---
title: "Screen capturing softare for ubuntu"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by shivantha17 on 2007-06-11
pls anyone can tel me,screen capturing program for UBUNTU 7.04.
**capturing the scren when u are working on window**:popcorn::popcorn::popcorn::KS:KS:KS:KS

---

### Post by andrewtst on 2007-06-11
goto Applications - Add/Remove
Select all avalable applications
and keying Ksnapshot in search

This Ksnapshot working well. :KS

---

### Post by timcredible on 2007-06-11
print screen and alt-print screen don't do what you want?

---

### Post by odiseo77 on 2007-06-11
@shivantha17: If you mean to capture videos of your screen while you're working on it, that's what I'm looking for as well... installed instanbul a couple of days ago but it doesn't record all what I what; besides, it records in .ogg format and I need it to be compatible with windows formats (need to record  my beryl sessions to show them to my friends using windows :D ). Anyway, if I manage to configure fine istanbul and fine a .ogg --> .mpeg encoder, I'll let you know.

Greetings.

---

### Post by eye208 on 2007-06-11
Install gtk-recordMyDesktop from the "universe" repository.

---

### Post by odiseo77 on 2007-06-11
> **eye208 said:**
> Install gtk-recordMyDesktop from the "universe" repository.

Cool, thank you eye208!! gtk-recordmydesktop works like a charm; records my desktop in high quality, which is one of the things I'm looking for. I only have one question: the resulting video is in .ogg format, but I need it to be in .mpeg format in order to upload it to youtube or simply share it with my friends who are using windows, so is there a special tool to convert .ogg videos to .mpeg? (I tried with fame, but I don't know what I'm doing wrong, since it won't convert the file).

Thanks in advance.

---

### Post by shivantha17 on 2007-06-12
thanx guys,what a grt world

---

### Post by Prefader on 2007-06-12
> **odiseo77 said:**
> I only have one question: the resulting video is in .ogg format, but I need it to be in .mpeg format in order to upload it to youtube or simply share it with my friends who are using windows, so is there a special tool to convert .ogg videos to .mpeg? (I tried with fame, but I don't know what I'm doing wrong, since it won't convert the file).

Thanks in advance.

In a terminal, try :

```
ffmpeg -i filename.ogg -target ntsc-dvd filename.mpg
```

Seemed to work fine for me for making a standard 720x480 mpeg file for use on a DVD - although it should work just about anywhere.  There are a few other options for the -target switch.  For example, if you want a PAL mpeg file, try "-target pal-dvd".  I believe you can also specify "film", rather than pal or ntsc, and formats like vcd, svcd, dv and dv50, rather than dvd.  I think that's about it, though.

Hope that helps!

---

### Post by odiseo77 on 2007-06-12
Hi Prefader, thanks for your reply; I installed ffmpeg, but when I run ***ffmpeg -i out.ogg -target ntsc-dvd out.mpg***, I get this error:

```
ffmpeg -i out.ogg -target ntsc-dvd out.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
out.ogg: Unknown format
```

So I guess either I'm missing some library or there's a bug with ffmpeg; I think it's rather the last one, since as I can see in the output, ffmpeg was configured/compiled with the '--enable-libogg' option and even so, it tells me *.ogg is an unknown format, so I'm gonna report it to [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs) (or take a look at the site to see if I can find an answer). In the meantime, I will try from debian to see what's the result. 

Thanks for your help anyway :)

Greetings.

---

### Post by videocheez on 2007-06-12
Check out the forums at [www.videohelp.com](www.videohelp.com).  They even have a linux section and there are guys there who know video and will be able to tell you exactly how to make the conversion.

---

### Post by odiseo77 on 2007-06-13
@videocheez: Thank you I'll try videohelp.com the next time I have problems with videos ;)  (I'm not much into video editing/converting; or to say it better, I'm totally green at it :D )

@Prefader: I tried ffmpeg on debian etch and it converted the video perfectly, gonna upload it to youtube to make my friends using windows envy me :p :D Thanks again for your help :D

---

### Post by Prefader on 2007-06-13
I *thought* I was running a stock Kubuntu ffmpeg build, but I must have compiled my own at some point, and forgotten.  Ah well, glad to see you got it working!

*EDIT*

My build has --enable-libvorbis set, which must be what's needed here - just in case anyone wants to know if their particular build can work with these files.

---

### Post by lamadredelsapo on 2007-07-09
Hi there I'm running Dapper and was wondering if gtk-recordmydesktop is anywhere to be found in the repos because I found Istanbul but it doesn't work very well. I'm quite in a hurry so help would be greatly appreciated...

---

### Post by iamaqbot on 2007-07-09
I've got Istanbul downloaded and also got the gtk-recordmydesktop file. It seems to be working as when i click it i get a record icon in my tray. When i right click it again, the icon changes to a stop icon, then if i click it one more time, the save file thing starts to open and quickly closes.

any ideas
thanks

---

### Post by lamadredelsapo on 2007-07-10
You have to select the record area before clicking the record button, after that when you click stop it will encode the video, and ask you for a location to save it.

---

