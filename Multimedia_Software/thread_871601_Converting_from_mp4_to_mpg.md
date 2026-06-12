---
title: "Converting from mp4 to mpg"
date: 2008-07-27
forum: Multimedia Software
---

### Post by vinooj on 2008-07-27
Help required to convert .mp4 to .mpg file format to play on my Palm tx. 

I found a hint to use ffmpeg by googling,
ffmpeg -i video.mp4 -ab 56 -ar 22050 -b 500 -s 320x240 javamm.mpg

The above command generated the .mpg file. however the resulting file size is almost double that of the original file. In my case it came to around 257M for a original file of size 150M. How can I reduce the reduce the filesize to easily fit in my Palm Tx?

Note: I also saw a suggestion to use mencode as follows,
mencoder video.mp4 -of mpeg -mpegopts format=mpeg1 -o javamm.mpg -oac lavc -ovc lavc -lavcopts vcodec=mpeg1video

Running the above command I got the following error,
Could not open codec.
FATAL: Cannot initialize video driver.
Exiting...

Thansk for your help.

---

### Post by CryptSphinx on 2008-07-27
if you dont mind using gui tools audacity and/or soundkonverter should be able to do the conversion

---

### Post by FakeOutdoorsman on 2008-07-27
> **vinooj said:**
> ...How can I reduce the reduce the filesize to easily fit in my Palm Tx? ...MPEG-4 is a much more efficient codec than MPEG-1/MPEG-2, so a video needs a higher bitrate and bigger filesize to be of similar quality.  Since your resulting file is large you can decrease the bitrate low enough to get the file size that you want.  You can use a [bitrate calculator]("http://www.3ivx.com/support/calculator/index.html") to get a rough idea of what bitrate you need.  Your command is telling FFmpeg to encode at 500 bits/second, which is incredibly low.  You need to use "k" after your bitrate:
```
ffmpeg -i video.mp4 -ab 56k -ar 22050 -b 500k -s 320x240 javamm.mpg
```
You can also add additional parameters to potentially increase the quality: [FFmpeg FAQ 3.16 Which are good parameters for encoding high quality MPEG-1/MPEG-2?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC28")

---

### Post by vinooj on 2008-07-31
Thanks for you help FakeOutdoorsman. Based on your suggestion, played around with the parameters and finally got the mpg file to a managible size using the following command.

ffmpeg -i video.mp4 -ab 56k -ar 22050 -b 200k -s 320x240 javamm.mpg

-b option seems to be the prominent one that effects the file size. There is  very fine line between and quality and size. 

Thanks.
vinoo

---

