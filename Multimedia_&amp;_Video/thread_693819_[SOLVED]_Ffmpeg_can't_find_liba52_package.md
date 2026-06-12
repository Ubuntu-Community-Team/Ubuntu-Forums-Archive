---
title: "[SOLVED] Ffmpeg can't find liba52 package"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by jan de beuker on 2008-02-11
Hello all

I'am trying to compress a VOB file to AVI using ffmpeg
At first I got the error 

Unsupported codec (id=86020) for input stream #0.1"

So I recompilled ffmpeg "./configure --enable-a52 --enable-gpl"

I also installed the liba52 package

Now ffmpeg give's

liba52.so.0: cannot open shared object file: No such file or directory
Error while opening codec for input stream #0.2

This file doesn't exist when I search fore it with the command "whereis"

It can find however "liba52.so: /usr/lib/liba52.so. /usr/lib/liba52.doc"

Can someone get me started because I'am going in circle's

Thanks in advance

Jan

---

### Post by disturbedite on 2008-02-11
i think you're doing something wrong, cuz as long as you have liba52 & liba52-dev, ffmpeg should work with ac3 since the ffmpeg ubuntu package & libs in the ubuntu repo are compiled with liba52 support already.

i wouldn't know what to tell you to resolve this tho, since its always worked for me.

---

### Post by cor2y on 2008-02-11
where did you get the version of ffmpeg you compiled?
If its svn there were changes made now its --enable-liba52 to have it enabled when configuring ffmpeg also like disturbedite said you need both liba52 and liba52-dev (which can be found via synaptic or apt-get) in order to compile with liba52 support for ffmpeg.
If you did all this then try running in the terminal
```
 sudo ldconfig
```
See if that helps. Sometimes after compiling software that gets installed in /usr/local/ instead of /usr/ you have to run that command.

---

### Post by disturbedite on 2008-02-12
well technically, you prolly only need liba52.  but if you're going to compile ffmpeg you'd need liba52-dev to be able to enable liba52 support.

---

### Post by philc on 2008-02-12
> **jan de beuker said:**
> 

So I recompilled ffmpeg "./configure --enable-a52 --enable-gpl"


Try --enable-liba52 rather than --enable-a52

Here's a How-To I wrote for installing FFmpeg from SVN on Gutsy.

[http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html](http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html)

---

### Post by jan de beuker on 2008-02-17
Hello all

Thanks for the reply but I still couldn't get it to work so a let it be for a while.
Today i followed the how to again no success.
I removed with synaptic ffmpeg  and tried the how to again no succes
After did i removad ffmpeg again and also with the terminal and also used de command --purge 
A reinstalled ffmpeg using the above mentioned how to and it worked .
The only explination i can think of is that a file is left behind from a previous installation and used if you try to run ffmpeg 

Thanks a lot for the advise and help 

Jan

---

