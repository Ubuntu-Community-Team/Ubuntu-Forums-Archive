---
title: "Convert amr to mp3 with ffmpeg - possible?"
date: 2011-02-13
forum: Multimedia Software
---

### Post by smarmytime on 2011-02-13
Hi - I've been recording one of my classes with my android phone, and the file it gives me is an .amr file. I'd like to convert that to .mp3, and I was hoping I could use ffmpeg to do it via the command line. Here's what I did, and the output that I got:

> roger@KarmaLaptop:~/Desktop$ ffmpeg -i Net202-week6.amr Net202-week6.mp3
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[amr @ 0x1fa7420]max_analyze_duration reached
[amr @ 0x1fa7420]Estimating duration from bitrate, this may be inaccurate
Input #0, amr, from 'Net202-week6.amr':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Audio: amrnb, 8000 Hz, 1 channels, flt
Output #0, mp3, to 'Net202-week6.mp3':
    Stream #0.0: Audio: 0x0000, 8000 Hz, 1 channels, flt, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Encoder (codec id 86017) not found for output stream #0.0
roger@KarmaLaptop:~/Desktop$ 



It gives me an .mp3 file, but it's 0 bits, and obviously isn't containing any information. The last line of the output looked like I may be missing something, so I installed lame, but that didn't seem to make any difference. Can anybody point me in the right direction?

---

### Post by Mia1990 on 2011-02-13
it looks like your missing --enable-libopencore-amrnb  --enable-libopencore-amrwb and --enable-libmp3lame i think you said you added the lame.But install the needed files of these and recompile ffmpeg then try it again.I think this will convert them for you

---

### Post by andrew.46 on 2011-02-13
Mind you it looks like it is the codec missing for the *output* (mp3) stream:

```
Encoder (codec id 86017) not found for output stream #0.0
```

rather than the *input* (amr) stream, from memory native AMR-NB decoding arrived with FFmpeg 0.6. So hopefully a quick trip to FakeOutdoorsman's guide will quickly rectify the problem:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by linuxsyst on 2011-02-13
1. Go to the Miksoft website, and download and install Mobile Media       Converter to your computer. This is a freeware program so you do not have to pay for it.

2. Launch Mobile Media Converter. You will see a large white area on the screen that is for files to be converted.

3. Locate the AMR files you want to convert. Drag and drop those files onto the large white area of the screen. Alternately, you can click the "+" button to add the files.

4. Select "MP3" as your output file type where it reads "Conversion." For the output file location, you can select a place on your computer you want the new MP3 file to be saved to.

5. Click "Convert Now" when you are ready to convert. When the conversion completes, a pop-up screen will appear to let you know. Close the screen and you will be able to use the new MP3 file.

Please answer i tried my best!

---

### Post by linuxsyst on 2011-02-13
The website [http://www.miksoft.net/](http://www.miksoft.net/)

---

### Post by aeiah on 2011-02-13
the miksoft program uses ffmpeg and mencoder do to the actual work, so if this software solves the problem, you can do it on the command line. maybe its worth a look just for that purpose

---

### Post by jnihil on 2012-09-22
Somwhat sceptical of this miksoft people.
Where is the source code? Searching for 'miksoft' and 'malware' has returned some suspicious results.

You're better off staying with ffmpeg.

---

### Post by RottNKorpse on 2012-10-17
I know this is somewhat old but there is actually an online converter that can do this so you don't need to install anything.

I don't know what they do with the files once they are converted but if it is audio files that arent sensitive in nature then it shouldn't really matter...if they are then nevermind this.

The site is [**http://media.io**]("http://media.io")

It supports a lot of audio formats for input and the **most common** formats for output.

---

### Post by andrew.46 on 2012-11-19
> **RottNKorpse said:**
> 

The site is [**http://media.io**]("http://media.io")

It supports a lot of audio formats for input and the **most common** formats for output.

I took a look at this: very nicely done! At least for the conversions I tried looks like he is using FFmpeg but the site is very, very nicely done.

---

### Post by frankcm3 on 2013-06-03
Excellent program in the Software Center simple called "Sound Converter". Just make sure to install the *optional add ons. *They aren't that optional.

---

