---
title: "Kino export audio to AC3"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by dad311 on 2007-01-22
Hello!

I have just started using Kino to transfer my home VHS moives to DVD.  I would like to encode my audio with AC3 encoding and I have set my audio encoding to ffmpeg.  However when I try to export my project I get the error "Error writing to KINO/MJPEG audio filter - aborting.

Has anyone experienced this issue and have a fix?


thanks.

---

### Post by 4ebees on 2007-01-22
Hiya,

If you start kino from the command line (open a terminal and type 

kino 

then hit 

enter

It will give you quite a bit of information in the background about what is happening.

Can you let me know what other options you are choosing when trying to export the video.

Is there a particular reason you want to use AC3 encoding? I'm not sure if Kino supports it, but you'd be better off asking on the Kino forum or in the mailing group - though you could strike it lucky and someone here happens to have an intimate knowledge of Kino :)

Does ffmpeg support AC3?


> **dad311 said:**
> Hello!

I have just started using Kino to transfer my home VHS moives to DVD.  I would like to encode my audio with AC3 encoding and I have set my audio encoding to ffmpeg.  However when I try to export my project I get the error "Error writing to KINO/MJPEG audio filter - aborting.

Has anyone experienced this issue and have a fix?


thanks.

---

### Post by dad311 on 2007-01-22
The error message is :

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:08:26, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
[COLOR="Black"]ffmpeg: unrecognized option '-o'[/COLOR]



Also, the kino user guide stated AC3 was supported.  Just insert "ffmpeg" into the Audio Encoding field.  Guess its not the easy.

---

### Post by dad311 on 2007-01-22
Looks like a issue with Kino 9.0. I installed 9.2 using the thread below and the probelm is fixed.

[http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2361&mesg_id=2361&page=2#2362](http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2361&mesg_id=2361&page=2#2362)

---

### Post by 4ebees on 2007-01-26
Well done... good find.

Thanks for also posting the link to the answer :)


> **dad311 said:**
> Looks like a issue with Kino 9.0. I installed 9.2 using the thread below and the probelm is fixed.

[http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2361&mesg_id=2361&page=2#2362](http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2361&mesg_id=2361&page=2#2362)

---

