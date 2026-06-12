---
title: "Convert mp4 to aac or mp3"
date: 2009-04-27
forum: Multimedia Software
---

### Post by xmattxjacksonx on 2009-04-27
I am trying to convert my encrypted m4p files I purchased in Itunes when I was running Windows. 

Is there any way to convert the files or play them using Ubuntu 9.04?

---

### Post by Lylepalooza on 2009-04-27
I don't have an answer but I would suggest changing the title of your question as it says mp4, though you actually want to convert an m4p, the encrypted Itunes extension. It might help you get more replies.

---

### Post by xmattxjacksonx on 2009-04-27
> **Lylepalooza said:**
> I don't have an answer but I would suggest changing the title of your question as it says mp4, though you actually want to convert an m4p, the encrypted Itunes extension. It might help you get more replies.

Thanks.

---

### Post by logos34 on 2009-04-27
EDIT:

there are workarounds, it appears, but some run on windows and cost $:

[http://ubuntuforums.org/showthread.php?t=996284&highlight=convert+.m4p](http://ubuntuforums.org/showthread.php?t=996284&highlight=convert+.m4p)
[http://ubuntuforums.org/showthread.php?t=1080099&highlight=convert+.m4p](http://ubuntuforums.org/showthread.php?t=1080099&highlight=convert+.m4p)

you could also burn and re-rip the songs in another format

---

### Post by robertrej on 2009-04-28
I found that oggconvert can convert MP4 file to ogv and
than just use ffmpeg to convert that to mp3.

How:
 Goto add/remove and in search type oggconvert and install.
Install ffmpeg the same as above. 
Run oggconvert from Applications/Sound&Video.
Than goto terminal and type ffmpeg -i YOURFILENAME.ogv  newfile.mp3
This should produce a mp3 file.
Of course make sure your MP4 file is in the same directory 
that you run ffmpeg in.

 Any questions send a E-mail to      [email]bjohnson1394@yahoo.ca[/email]

                        good day
                        Bob

---

### Post by xmattxjacksonx on 2009-04-29
> **robertrej said:**
> I found that oggconvert can convert MP4 file to ogv and
than just use ffmpeg to convert that to mp3.

How:
 Goto add/remove and in search type oggconvert and install.
Install ffmpeg the same as above. 
Run oggconvert from Applications/Sound&Video.
Than goto terminal and type ffmpeg -i YOURFILENAME.ogv  newfile.mp3
This should produce a mp3 file.
Of course make sure your MP4 file is in the same directory 
that you run ffmpeg in.

 Any questions send a E-mail to      [email]bjohnson1394@yahoo.ca[/email]

                        good day
                        Bob

WOW! Thanks.

EDIT:
But, it didn't work.

---

### Post by logos34 on 2009-04-29
> **robertrej said:**
> I found that oggconvert can convert MP4 file to ogv and
than just use ffmpeg to convert that to mp3.

it can convert DRM-protected .m4p files?

I thought that was the issue

---

### Post by robertrej on 2009-04-30
All the science video's I download from Youtube are in mp4
via keepvid so maybe there are various types of mp4 files
(not my area of expertise )I perfer wav and ac3 myself.
If you want send me a sample file and I will try to convert it
for you to see what the issue maybe.
E-mail      [email]bjohnson1394@yahoo.ca[/email]

(  JUST 1 PLEASE! )

                            GOOD DAY
                            Bob

---

### Post by xmattxjacksonx on 2009-04-30
> **robertrej said:**
> All the science video's I download from Youtube are in mp4
via keepvid so maybe there are various types of mp4 files
(not my area of expertise )I perfer wav and ac3 myself.
If you want send me a sample file and I will try to convert it
for you to see what the issue maybe.
E-mail      [email]bjohnson1394@yahoo.ca[/email]

(  JUST 1 PLEASE! )

                            GOOD DAY
                            Bob

There is no need.  An m4p file is totally different from an mp4 file.  An m4p file is an Apple encrypted audio file that you get when you buy a song off of iTunes.  It looks like I am going to have to use Windows and buy some software to convert the files.  But, thank you anyways.

---

### Post by robertrej on 2009-04-30
Never under estimate the power of Ubuntu and these forums!

Here are two ideas found on google you may want to look at.


[http://media-convert.com](http://media-convert.com)



[http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm](http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm)


(or here a bit of code you can try in terminal)

Hi, I found the ffmpeg package works really well (search google). Then
use a shell script like the one below to batch convert all files in a
folder to mp3 (I know, proprietry again). Probably also works for ogg:

#!/bin/sh

for i in *.m4a; do \
ffmpeg -i "$i" -acodec mp3 -ac 2 -ab 128 "${i%m4a}mp3"; \
done



                             good day
                             bob

---

### Post by sonicseaweed on 2010-10-12
I made a couple of modifications to make the script snippet work for me

> 
for i in *.m4a; do \
ffmpeg -i "$i" -acodec libmp3lame -ac 2 -ab 128000 "${i%m4a}mp3"; \
done


the bitrate is in bits not kilobits and I have lame installed as my mp3 codec so I changed the acodec to libmp3lame.

---

