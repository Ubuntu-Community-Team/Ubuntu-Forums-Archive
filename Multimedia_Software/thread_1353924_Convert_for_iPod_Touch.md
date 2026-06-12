---
title: "Convert for iPod Touch"
date: 2009-12-13
forum: Multimedia Software
---

### Post by Willn21 on 2009-12-13
Hi,

I have some movies encoded with divx, for example:  spiderman2.avi .  I want to be able to send them to my ubuntu server and have them converted for my ipod touch.

I have tried some commands but cannot seem to get it to work.  Right now I have spiderman2.avi on my server.  I just tried a generic command ```
ffmpeg -i spiderman2.avi   spiderman2.mp4
``` I get this error ```
Unsupported codec for output stream #0.0
```  I know that probably wouldn't play on my ipod but can anyone tell me what command I need to type in to convert it for my ipod touch.  Or even better can someone explain how to set up a profile.  thanks

---

### Post by Willn21 on 2009-12-13
bump

---

### Post by FakeOutdoorsman on 2009-12-13
> **Willn21 said:**
> Hi,

I have some movies encoded with divx, for example:  spiderman2.avi .  I want to be able to send them to my ubuntu server and have them converted for my ipod touch.

I have tried some commands but cannot seem to get it to work.  Right now I have spiderman2.avi on my server.  I just tried a generic command ```
ffmpeg -i spiderman2.avi   spiderman2.mp4
``` I get this error ```
Unsupported codec for output stream #0.0
```
What Ubuntu version are you using?  You get this error because Ubuntu does not enable "restricted" encoders in FFmpeg by default.  The user must enable these encoders, but it is easy to do:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

However, if you are using Ubuntu Karmic, you will need to compile FFmpeg yourself because FFmpeg from the repository can not encode to AAC audio which I believe the iPod Touch uses (this may change soon if or when Medibuntu releases their version of the *libavcodec-extra-52* package).  I created a tutorial on how to compile FFmpeg, so if you can cut and paste, you can also compile:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Compiling FFmpeg gives you the advantages of some additional encoders, bugfixes, and important quality improvements that are lacking in FFmpeg from the repository.

Now for the command.  I'm not sure if it will work because I don't have an iPod Touch, but the quality will be very good:
```
ffmpeg -t 30 -i spiderman2.avi -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod640 -crf 26 -s 640x480 -threads 0 spiderman2.mp4
```
This command will create a 30 second test video so you won't have to encode the whole thing.  If it works, then remove the **-t 30** option to encode the whole video.  If it does not work then I will come up with an alternative command.

---

### Post by issih on 2009-12-13
Can I recomend you install handbrake:

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

It has ipod touch presets built in and the cli version is very easy to use.

Hope that helps

---

### Post by Mesqueeb on 2010-11-27
Hi! terminal code works perfect for me and my iPodT! ^^

However! How to add audio layer 2 instead of 1? And not add the sub layers?
I have an avi and multiple mkv's I want to convert with multiple audio layers.
Thanks!

-Mesqueeb

---

