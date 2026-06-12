---
title: "Convert MTS/M2TS(AVCHD) to AVI"
date: 2008-08-23
forum: Multimedia Software
---

### Post by Inquisitive Alex on 2008-08-23
Hello. I installed m2tstoavi as described here ([http://wesleybailey.com/articles/m2tstoavi-avch](http://wesleybailey.com/articles/m2tstoavi-avch)). When I try to run m2tstoavi, I get the following message:
```
using:
/usr/local/bin/xporthdmv
ldecod: Command not found.

```
How can I get ldecod? Thank you for answer.

---

### Post by Inquisitive Alex on 2008-09-11
Please, help...](*,)

---

### Post by Erlander on 2008-09-12
I had the same problem and had several attempts at the procedure in the tutorial.

Unfortunately I did not keep any notes on the extra things I had to do to get it to work so I am going from memory.

In step 2 I saw an error message about packages that were not available in Hardy and had to find equivalent packages that Hardy would install.

In step 4 you need to go to [http://iphome.hhi.de/suehring/tml/]("http://iphome.hhi.de/suehring/tml/")  to check the version.  Its 14.2 at the moment and the link is there as "h.64/avc"

That's all I can remember so I hope it helps.

Rob

---

### Post by Inquisitive Alex on 2008-09-12
Thank you for answer. I should just change version in "download" file to 14.2. Now it works on my 32-bit laptop. However, it does not work on my 64-bit desktop. The following error occurs during compilation:
```

inc/quant.h:32: error: conflicting types for ‘qmatrix’
inc/global.h:76: error: previous declaration of ‘qmatrix’ was here
src/quant.c:226: error: conflicting types for ‘qmatrix’
inc/global.h:76: error: previous declaration of ‘qmatrix’ was here
src/quant.c: In function ‘init_qp_process’
src/quant.c:242: warning: implicit declaration of function ‘malloc’
src/quant.c:242: warning: incompatible implicit declaration of built-in function ‘malloc’
src/quant.c:245: warning: incompatible implicit declaration of built-in function ‘malloc’
make: *** [obj/quant.o] Error 1

```
Please, help again :-k

---

### Post by Erlander on 2008-09-12
Good that you have it working on your laptop.

Although I'm running an AMD 64 chip I'm still using the 32 bit Ubuntu.  I don't know what your Qmatrix problem could be.

Maybe someone else can help with that or perhaps a personal message to Wes Bailey on this forum.

Rob

---

### Post by Inquisitive Alex on 2008-09-13
I cannot find such user on this forum. What is his nickname?

---

### Post by xc3RnbFO8P on 2008-09-13
You can try here:
[http://wesleybailey.com/articles/m2tstoavi-avchd]("http://wesleybailey.com/articles/m2tstoavi-avchd")

---

### Post by Erlander on 2008-09-13
> **Inquisitive Alex said:**
> I cannot find such user on this forum. What is his nickname?

[http://ubuntuforums.org/showthread.php?t=529871&highlight=AVCHD]("http://ubuntuforums.org/showthread.php?t=529871&highlight=AVCHD") 

See Post #7

Rob

---

### Post by Inquisitive Alex on 2008-09-14
My joy was premature... The script works fine on test m2ts file. But when I tried to encode my m2ts files result was awful (see attachments).

---

### Post by Erlander on 2008-09-14
Yes,  I've had that too.

I think it is caused by the AVCHD file being at a different frame rate or a different resolution to what the script expects.

I have changed the frame rate to 25 in mine to allow for PAL but changing the 1440 x 1024 doesn't seem to help.  Unfortunately I haven't had time to experiment much with this so for now my camera is set to only take standard definition video.

Rob

---

### Post by Inquisitive Alex on 2008-09-15
> **Erlander said:**
> 
Yes,  I've had that too.

So you did not managed to get this script working properly?

---

### Post by Erlander on 2008-09-15
I had it working on 1440 x 1080 video although I was not impressed with the quality.  On Full HD video I had the same result as you.

I suspect its in the settings but do not have time at present to sort it out.

Rob

---

### Post by Inquisitive Alex on 2008-09-16
Thank you anyway. Do you know other way to convert m2ts files to playable format (avi, mpeg, ...)?

---

### Post by Erlander on 2008-09-16
You could have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

Rob

---

### Post by cotcot on 2008-09-16
I used [[COLOR="Red"]this site[/COLOR]]("http://wesleybailey.com/articles/m2tstoavi-avchd") to install everything needed to convert. Ldecod is in the script.

and use this script to executed the conversion :

> #/bin/bash
xporthdmv -nh 00161.MTS 1 1 1 
ldecod -i bits0001.mpv -o /tmp/samplevideo.yuv 
mv bits0001.mpa /tmp/samplevideo.ac3 
ffmpeg -r 25 -s 1440x1080 -i 00161.MTS -acodec ac3 -ab 256k -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -b 15000k -deinterlace -copyts 00161.avi

This works fine on my 64 bit desktop. (specs in sig)

---

### Post by rubycin on 2008-09-18
For Mac users:
You can use [video converter for mac to convert MTS/M2TS to AVI on Mac.]("http://www.moviesmac.com/video-converter-mac/index.html")

---

### Post by amckenny on 2008-12-03
I actually found a quite nice program that is fairly user friendly (in a linux sense) and handled AVCHD nicely. At least the video worked... I have a request for help out for my sound as my sound card stopped working with the upgrade to intrepid...

The program is called Handbrake and can be found at [http://handbrake.fr/](http://handbrake.fr/)

Hope this helps

---

### Post by Erlander on 2008-12-04
amckenny

Thank you for the Handbrake details.

It looks very good.

I'm no good with command line interfaces and have only had poor quality conversions up till now.

I have used it on some clips that are 1920 x 1080 and got excellent quality.

I've played with the settings a bit and wound up the bitrate etc and left the AC3 sound as pass through.

This looks like the beginning of Linux being able to use HD video for me.

One less reason to use M$ Windows and no need to buy Sony Vegas!!!

Rob

---

### Post by luwen on 2009-01-06
Yes, you can try [Handbrake]("http://www.moviesmac.com/tutorial/how-to-use-handbrake-convert-videos-on-mac.html#119"), it works well at converting M2TS to AVI.

And you [iSquint ]("http://www.moviesmac.com/news/free-mac-video-converter-discontinued.html#119")is also a awesome tool for converting MTS/M2TS to AVI, MKV...

---

### Post by Erlander on 2009-01-06
> **luwen said:**
> Yes, you can try [Handbrake]("http://www.moviesmac.com/tutorial/how-to-use-handbrake-convert-videos-on-mac.html#119"), it works well at converting M2TS to AVI.

And you [iSquint ]("http://www.moviesmac.com/news/free-mac-video-converter-discontinued.html#119")is also a awesome tool for converting MTS/M2TS to AVI, MKV...
Will iSquint work in Ubuntu?

Rob

---

