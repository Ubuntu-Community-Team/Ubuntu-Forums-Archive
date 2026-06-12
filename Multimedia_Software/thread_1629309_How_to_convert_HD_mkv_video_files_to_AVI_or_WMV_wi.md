---
title: "How to convert HD mkv video files to AVI or WMV without loss of quality"
date: 2010-11-23
forum: Multimedia Software
---

### Post by sir_robert007 on 2010-11-23
Hey does anyone know of any FOSS program I can use to convert HD X.264 MKV video files to AVI or WMV without loss of quality. I wish to stream these videos from my linux box (yes u can do that via ushare)to my xbox 360 but unfortunaly it wont play MKV files.

thanks

---

### Post by sir_robert007 on 2010-11-24
still awaiting a reply

---

### Post by brk3 on 2010-11-25
You're mentioning two different topics -  X.264 being a codec and MKV, AVI, and WMV just being containers. 
(Think WMV may also be a codec, not 100%).

You won't be able to convert X.264 to AVI(xvid/divx/etc/) without loss of quality.

Fastest way you'll get help would be to post exactly why you're looking to convert, i.e. to play mkv's on a xbox360/ps3 etc.

Also, there's a lot of other threads around this so have a read of those also.

---

### Post by sir_robert007 on 2010-11-26
> **brk3 said:**
> You're mentioning two different topics -  X.264 being a codec and MKV, AVI, and WMV just being containers. 
(Think WMV may also be a codec, not 100%).

You won't be able to convert X.264 to AVI(xvid/divx/etc/) without loss of quality.

Fastest way you'll get help would be to post exactly why you're looking to convert, i.e. to play mkv's on a xbox360/ps3 etc.

Also, there's a lot of other threads around this so have a read of those also.

Ok I browsed the forums and came across a tutorial for Fuppes, a program similar to ushare except that it offers on the fly transcoding of media files. Also I gave WinFF a try and converted an mkv file in Xvid format, however I didnt do it right as I converted it to Xvid Fullscreen instead of Xvid Widescreen so now the video has a smashed appearance when it plays. 

Now correct me if im wrong but ive also heard that if you convert a mkv file to mp4 that it will retain its HD quality. 

Will give Fuppes a try and will also run WinFF again to try to convert a mkv file to mp4. Will let you know of the results.

---

### Post by coffeecat on 2010-11-26
Try DeVeDe. It's in the repos. Yes, that's right - DeVeDe. It might seem odd to recommend DVD authoring software for what you want, but when you first open it the last choice is for creating 'DivX/MPEG-4' which actually creates an Xvid AVI. It will cope with HD resolution.

---

### Post by Bone Down on 2010-11-26
Have a look at handbrake see if that will do what you like as well.

---

### Post by sir_robert007 on 2010-11-27
> **Bone Down said:**
> Have a look at handbrake see if that will do what you like as well.

Ok i gave handbrake a try. I set it so that it would encode with the .m4v file extension in mp4 format with H.264 video codec. Finally finished after three long hours of encoding, however when tried to play it with totem movie player I get an error saying the file is invalid and cannot be played. Did I miss something in the encoding process?

I shall give DeVeDe a try see if that works.

---

### Post by Bone Down on 2010-11-28
> **sir_robert007 said:**
> Ok i gave handbrake a try. I set it so that it would encode with the .m4v file extension in mp4 format with H.264 video codec. Finally finished after three long hours of encoding, however when tried to play it with totem movie player I get an error saying the file is invalid and cannot be played. Did I miss something in the encoding process?

I shall give DeVeDe a try see if that works.

make sure to select universal in the settings. I use it all the time, in fact i am using this very moment in the background. I access the completed files via my BDC6500 wifi bluray.

edit: [I followed this guide.]("http://www.winsupersite.com/digitalmedia/dmc_video_convert.asp")

---

### Post by MrWES on 2010-11-28
> **sir_robert007 said:**
> Hey does anyone know of any FOSS program I can use to convert HD X.264 MKV video files to AVI or WMV without loss of quality. I wish to stream these videos from my linux box (yes u can do that via ushare)to my xbox 360 but unfortunaly it wont play MKV files.

thanks

Here's  a link for extracting the audio and video from an mkv file and re-containerizing it into an mp4 -- no quality loss. It's from the command line, but powerful and fast.

[http://ubuntuforums.org/showthread.php?p=9370090#post9370090]("http://ubuntuforums.org/showthread.php?p=9370090#post9370090")

Bill

---

### Post by sir_robert007 on 2010-12-05
> **Bone Down said:**
> make sure to select universal in the settings. I use it all the time, in fact i am using this very moment in the background. I access the completed files via my BDC6500 wifi bluray.

edit: [I followed this guide.]("http://www.winsupersite.com/digitalmedia/dmc_video_convert.asp")

Ok I followed your suggestion and it worked!! It also took a lot less time to encode, bout an hour. Unfortunately i have run into problems with ushare so I'm gonna create a new thread to get help on that. 

Oh hey also would a wifi blu-ray player be capable of playing MKV files without having to transcode them?

---

### Post by MrWES on 2010-12-05
FYI...if you follow the guide my previous post you can have the mp4 in about 10 mintues. MKV is only a container and really there is no need to transcode. All you need to do is extract the audio and video files from the MKV and put them back together in the MP4 container. It's that simple.

Bill

---

