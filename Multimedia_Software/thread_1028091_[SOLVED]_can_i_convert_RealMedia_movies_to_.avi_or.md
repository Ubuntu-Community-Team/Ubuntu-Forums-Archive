---
title: "[SOLVED] can i convert RealMedia movies to .avi or .mpg?"
date: 2009-01-02
forum: Multimedia Software
---

### Post by jmd9qs on 2009-01-02
hi,

i recently downloaded some physics course lectures from MIT's website and i wanted to burn them to a dvd using ffmpeg and dvdauthor. however, the files are in .rm format. i've searched google up and down for this and haven't found a relavent post on how i might convert this to a .mpg, or worst-case-scenario an .avi file. 

i frequently use ffmpeg and dvdauthor to make dvd's from .mpg movies, so i don't need pointers on that, just on how to convert from .rm to .mpg/.avi

also, i wanted to merge the files (say from lecture 1 - lecture 6), so i tried using cat:

```
cat PhysII_Lec01.rm PhysII_Lec02.rm (etc etc etc) > PhysII_Lec01-06.rm
```

afterwards, there was a file in the directory i specified, and it was about 500MB, which was expected... however, when i played it (w/ totem cause vlc wouldn't work for some reason), i only got the first lecture and the video stops. any pointers on this??

thanks

---

### Post by FakeOutdoorsman on 2009-01-02
I think ffmpeg should be able to handle Real Media files, but to combine I think they have to be converted to a cat friendly format.  Refer to: [How can I join video files?](http://ffmpeg.mplayerhq.hu/faq.html#SEC30) [FFmpeg FAQ].  The resulting file will be quite large, but it can be used as the new combined input video for ffmpeg.

---

### Post by jmd9qs on 2009-01-02
would i just set it up like i was converting an mp4 to avi? for example:

```
ffmpeg -i original_file.rm /media/disk/new_file.avi
```

is that what you're saying? or is there a different way to do it? thanks

(btw, i read over the link you showed me, nothing in there about the conversion from .rm to .avi/.mpg, but it explained very well how i should join it after conversion... thanks a bunch!)

---

### Post by FakeOutdoorsman on 2009-01-02
You should join the files first and then convert to your final format.  First you will convert the rm to a joinable format such as mpg with the -sameq option to help preserve quality as explained in the link above.  This will be a big file.  You can then use ffmpeg to convert this resulting large file, unless of course you don't mind the size.

---

### Post by jmd9qs on 2009-01-03
thanks for the help! ffmpeg successfully converted from .rm to .avi with the -sameq option... however, about halfway through the video the quality gets really really crappy (very pixelated and 'colorfull snow' if you know what i mean) and stays crappy throughout the rest of the video.

the audio quality is, however, excellent throughout the whole video. i am not familiar with many of the ffmpeg options dealing with frame-rates and whatnot, can you perhaps suggest some settings i might use to improve this?

---

### Post by jmd9qs on 2009-01-03
update: 

i have about 20 of these .rm files, and have so far successfully converted 1 good copy to .avi. all the others are completely useless. the website that i'm downloading these from has a streaming option which takes you to a seperate url where you watch the video in mp4 format... is there any way to download these films using that url? if that fails i don't know what else to try. basically, i want to convert these to a dvd-compatible format so i don't have to store them on my already full drive... is there any other way for me to do this??? any help is, of course, very appreciated

---

### Post by jmd9qs on 2009-01-04
update #2:

i did find a website that works well, it is however a tad on the slow side. it can convert pretty much anything you throw at it, and will download content by url or you can upload files off of your machine. here is the url, if anyone is interested:


[http://media-convert.com/convert/](http://media-convert.com/convert/)

thanks all

---

