---
title: "best encoding program for mpeg video"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by amonsul on 2007-04-02
Hi guys,

we're working on macintosh and ubuntu machines for multimedia and video projects. we've got to compress dv videos for a videoinstallation. as video player we have to use the stumpfl video player ([http://www.avstumpfl.com)](http://www.avstumpfl.com)). They have special videoplayers and a proprietary software for encoding. Basically you need to save on a CF card mpeg2 videos. Obviously no problem with their software. Now, we don't have that software (windows and money!). We tried with the mac, but the player specifications are so narrow that it's not possible to get out the right format. We then tried with the program ffmpex on os x. It finally worked, but the quality we get is definitely not satisfying. I wonder if in the linux world there is a program to encode dv videos (which come from fcp). It should be a mpeg2 video, the data rate can be as high as 8000. Audio specs are mp2, 224 kbit/s, 48000kHz stereo. Audio and video have to be muxed into one .mpg file.

Thanks for any suggestions

Andrea

---

### Post by reclusivemonkey on 2007-04-02
> **amonsul said:**
> Hi guys,

I wonder if in the linux world there is a program to encode dv videos (which come from fcp). It should be a mpeg2 video, the data rate can be as high as 8000. Audio specs are mp2, 224 kbit/s, 48000kHz stereo. Audio and video have to be muxed into one .mpg file.

Thanks for any suggestions

Andrea

Did you tinker with the ffmpeg settings? Other than ffmpeg, mencoder and mjpeg tools are possibilities. I'm afraid I don't know which will yeild the best results;

[http://mjpeg.sourceforge.net/](http://mjpeg.sourceforge.net/)
[http://www.mplayerhq.hu/](http://www.mplayerhq.hu/)

---

