---
title: "Mplayer &amp; FFMPEG fail on Ver 10.04 LTS"
date: 2012-02-21
forum: Multimedia Software
---

### Post by jjrjr1 on 2012-02-21
Hi
 
I am looking to find out if FFMPEG and Mplayer work in 10.04
 
I just upgraded from 9.04
 
FFMPEG & Mplayer worked fine in 9.04
 
FFMPEG fails in the make command claiming some x264 objects are missing.
 
Mplayer gets a FATAL error and says it cannot initialize the video driver.
 
All ffmpeg souce is current as well as the x264 codec.
 
Mplayer is also the current version and the video card is a geForce cts 450.
 
I have also installed the most current Nvidia drivers.
 
Any thoughts would be appreciated.
 
Thanks
 
John

---

### Post by SeijiSensei on 2012-02-21
Did you run "sudo apt-get build-dep mplayer" before running configure?

You might want to look at the build of **mplayer2** at this [PPA]("http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html").  I used to build mplayer and later mplayer2 from source, but now I just use that PPA.  I also install **smplayer** for the front-end.

---

### Post by jjrjr1 on 2012-02-22
Hi Seiji

Thanks the apt-get build-dep mplayer resolved the problem with Mplayer.

I am still unable to get a clean compile in FFMPEG.

It is related to libx264.

I have tried compiling many different versions of that encoder and am using the latest FFMPEG source.

No matter what I do I get this error when compiling FFMPEG.

LD    ffmpeg_g
/root/src/ffmpeg/libavcodec/libavcodec.so: undefined reference to `x264_picture_init'
/root/src/ffmpeg/libavcodec/libavcodec.so: undefined reference to `x264_encoder_open_116'
collect2: ld returned 1 exit status
make: *** [ffmpeg_g] Error 1

I had no problems on Ver 9.4 or 9.10

Do you or anyone have an idea how I can resolve this issue?

Thanks

John

---

### Post by ron999 on 2012-02-22
> **jjrjr1 said:**
> 
Do you or anyone have an idea how I can resolve this issue?

Try using the tutorial here ---> [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289")

---

### Post by jjrjr1 on 2012-02-22
Hi all

Thanks for the help.

I solved the ffmpeg compile error.

It seems that compiling the libx264 source does not place the library or create a link for the library to /usr/lib.  It only places it into /usr/local/lib

By making a copy in /usr/lib solved the problem

Probably not the cleanest way to deal with it but it worked and I am tired of messing with it.

Thank you all for your help and suggestions.

I now have ffmpeg compiled as a SUPER video converter.  It can convert every video format to another including HD (h264)

Also Mplayer is now up and running

Thanks again

John

---

### Post by SeijiSensei on 2012-02-23
On my 10.10 system, the file /etc/ld.so.conf.d/libc.conf contains the reference to /usr/local/lib as a library source.  Sometimes you need to run "sudo ldconfig" after installing libraries to have them incorporated into the system.  You'll notice that apt-get often runs ldconfig after installation.

By the way, if you want to give mplayer2 a whirl, the source code is [here](http://www.mplayer2.org/).  Since you already installed the dependencies for mplayer, mplayer2 should probably compile without incident as well, if I recall correctly.

I have media files that use some unusual Matroska features like ordered chapters that aren't well supported in stock mplayer.  Support for multithreading is also welcome.

---

