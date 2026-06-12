---
title: "Handbrake and encoding a phone 720p video"
date: 2016-05-23
forum: Multimedia Software
---

### Post by mastablasta on 2016-05-23
The smartphone made a 720p video. The quality is not really that good, but it is in the OK range. 

anyway the mp4 file from the phone for 2 minute video was 414 Mb big. this seems a bit excessive to me as i know that there are 720p movies that are in the 700, 800 mb range. so i went to encode and since the linux PC has stronger CPU that my old XP pc i used Kubutnu with latest **Handbrake** installed to do the encoding.

i checked some online guides on how to use hanbrake and to reduce the video size without loosing much quality (swtich to x264, set reference frames to 4 and reduce audio bitrate). after encoding the file was about 50 Mb size with descent quality. however this still seems a lot for a 2 minute video.

should't the file be less than 10 Mb in size? what else could i do to get small size and keep a descent quality?

how do they manage to compress movies to such small size and keep the quality good and compression method simple enough for RPi to be able to decode the video.

---

### Post by Rob Sayer on 2016-05-23
RPi?  You mean raspberry pi?  I don't know anything about its decoding capabilities.

Video encoding is complicated, and there is no good way to simplify it because there aren't any magic quality settings that will work for any video.  They didn't design those formats/codecs/parameters for average users.  They were written for professionals.

It's hard to say if the video output size is small enough.  You say the input video is lower quality.  Low quality video actually will not compress as well as high quality.  And if there is a lot of motion, which is hard to avoid with phone videos because it's hard to hold it still, that will mean it won't compress as well as static video.

One thing I will say is that setting it to x264 output (which is all Handbrake supports AFAIK in the repo versions) and setting the reference frames to 4 is just a beginning.  It's a lot more complicated than that.  Most people who do a lot of encoding in x264 don't bother with target file size or target bit rate (which is really the same thing).  They use CRF encoding, which I think Handbrake calls constant quality.  It gives you the same quality as 2 pass target bit rate if not better with a lot more speed but you can't predict what the file size will be exactly.

I don't know what sources you used but many if not most of those blog articles are rubbish.

---

### Post by shantiq on 2016-05-23
[COLOR=#DD4814]**mastablasta**[/COLOR] something like this should make it really light ..   see how you get on



```
 time HandBrakeCLI -i yourinputfile -o outfile.mkv -e ffmpeg2 -w 1080 -l 720 -b 1000 -E mp3 -B 64 -r 25
```




**EDIT:**   just tested here with a 579MB 3 minute vid from iphone and ended up with 28MB   and decent [took 6 mn] i add time before command to see how long it takes

---

### Post by mc4man on 2016-05-23
I'd just use ffmpeg directly, pretty straightforward. I sorta doubt you'll get them down near 10MB  though you could try & see what's your best size vs. quality point. Basically bitrate x time equals size.
ffmpeg x264 guide here, try using  slowest preset you can handle with highest crf before quality is not good enough. Maybe start with preset of slow & crf of 28 or 30 or  32 .. ect.
[https://trac.ffmpeg.org/wiki/Encode/H.264](https://trac.ffmpeg.org/wiki/Encode/H.264)
If you were to use ffmpeg w/ x265 then you should get lower filesize at same quality, basic guide here though your rpi would have to be able to use hevc
[https://trac.ffmpeg.org/wiki/Encode/H.265](https://trac.ffmpeg.org/wiki/Encode/H.265)

---

### Post by mastablasta on 2016-05-24
i guess i have my weekend cut out for me :) thanks for all the advice. i will try it out see if i can compress it a bti more or not. otherwise i guess i need ot start thinking baotu new hard drive as well as the backup drive.

perhaps phones and such should make better compression ratio videos. i mean my bro has an HD video cam with DVD's and with constant recording it can fit about 30 min 1080p HD video on that small DVD which is 2.1 GB size or something like that. the way these phones record and encode, one couldn't get more than 6 minutes on it. terrible. and i bet they have better CPU and GPU that that old video cam.

---

### Post by mc4man on 2016-05-25
Not sure what phones do except use fairly high bitrate & realtime encoding, on my nexus it's default app is  17Mbps to avc Baseline.
The default nexus app just allows setting rez, (720p, 1080p, 4k), a 3rd party app I have allows a number of video settings.
In screen is an ex. of 36 sec with the 3rd party app at it's default - (720p, 37.2Mbps), I re-encoded with both x264 & x265 using basic parameters & veryslow preset (which is in fact very slow..
The size reduction was quite a lot & quality is very good, maybe a little softer in spots & some very fine detail gone.

lowering the crf to 25 for x265 makes for a slightly bigger file, maybe a little better but nothing that jumps out in casual viewing on my laptop, 2nd scr.

You should just take several 15-30 sec vids, then try some various  encodings & see what suits your use case & time/size/quality concerns.

---

### Post by Rob Sayer on 2016-05-28
Another suggestion: some of the best advice I've ever seen for getting decent compression and quality:

If you're going to reduce the bit rate (inevitable if you want to shrink the file size) downsample the resolution eg. resize from 1080p to 720p or smaller.

When you resize make sure the height is evenly divisible by 16.  Video encoding and decoding is basically matrix processing and this will just work better.

---

