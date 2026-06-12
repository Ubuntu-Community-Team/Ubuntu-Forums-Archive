---
title: "Reformat video file for InnoTab"
date: 2012-05-02
forum: Multimedia Software
---

### Post by DavidVS on 2012-05-02
My son loves those little five-minute *Thomas the Train* movies.  I have used AcidRip to make a bunch of them AVI files so he can watch them on the laptop by clicking on file icons, without needing to deal with DVDs and menus.

Now he has an InnoTab toy.  It can play video files but only of a specific format.

How do I make a new copy of these files having the new format?  I do not trust my understanding of audio/video jargon enough to try to decipher the FFMPEG help myself.

What the InnoTab manual says we want:

File Type AVI
Video Encoder MJPEG
Display Size 480 x 272
Frame Rate 15 fps
Bit Rate 2,400 kbps
Audio Encoder PCM
Audio Channel Mono
Sampling Rate 20.05 kHz

What file properties says we have:

File Type AVI
Codec FFmpeg MPEG-4
Display Size 720 x 480
Frame Rate 30 fps
Audio Codec MPEG 1 Audio, Layer 3 (MP3)
Channels Stereo
Sampling Rate 48 kHz
Audio Bit Rate 129 kbps

Thanks!

---

### Post by ron999 on 2012-05-02
> **DavidVS said:**
> How do I make a new copy of these files having the new format? I do not trust my understanding of audio/video jargon enough to try to decipher the FFMPEG help myself. 

What the InnoTab manual says we want:

File Type AVI
Video Encoder MJPEG
Display Size 480 x 272
Frame Rate 15 fps
Bit Rate 2,400 kbps
Audio Encoder PCM
Audio Channel Mono
Sampling Rate 20.05 kHz

Hi
This FFmpeg command:-
```
ffmpeg -i input.avi -vf "scale=480:trunc(ow/a/2)*2" -vcodec mjpeg -b 1800k -r 15 -acodec pcm_s16le -ar 20050 -ac 1 output.avi
```

Gives me this result:-

```
General
Complete name               : output.avi
Format                      : AVI
Format/Info                 : Audio Video Interleave
File size                   : 7.85 MiB
Duration                    : 30s 133ms
Overall bit rate            : 2 185 Kbps
Writing application         : Lavf54.3.100

Video
ID                          : 0
Format                      : JPEG
Codec ID                    : MJPG
Duration                    : 30s 133ms
Bit rate                    : 1 853 Kbps
Width                       : 480 pixels
Height                      : 270 pixels
Display aspect ratio        : 16:9
Frame rate                  : 15.000 fps
Color space                 : YUV
Chroma subsampling          : 4:2:0
Bit depth                   : 8 bits
Compression mode            : Lossy
Bits/(Pixel*Frame)          : 0.953
Stream size                 : 6.66 MiB (85%)

Audio
ID                          : 1
Format                      : PCM
Format settings, Endianness : Little
Format settings, Sign       : Signed
Codec ID                    : 1
Duration                    : 30s 16ms
Bit rate mode               : Constant
Bit rate                    : 321 Kbps
Channel(s)                  : 1 channel
Sampling rate               : 20.0 KHz
Bit depth                   : 16 bits
Stream size                 : 1.15 MiB (15%)
Interleave, duration        : 32 ms (0.48 video frame)
```

---

### Post by DavidVS on 2012-05-02
[COLOR="DarkRed"]ffmpeg -i input.avi -vf "scale=480:trunc(ow/a/2)*2" -vcodec mjpeg -b 1800k -r 15 -acodec pcm_s16le -ar 20050 -ac 1 output.avi
[/COLOR]

It works perfectly.  Thank you, ron999.

Also, I found on [this website]("http://www.tools4movies.com/2012/01/dvd-to-vtech-innotab-media-format-converter/") that the SD Card needs the nested folders **LLN** with **MOVIE** inside.  Simply drag the files into the MOVIE folder and they are available next the InnoTab is turned on.

---

### Post by DavidVS on 2012-05-02
Actually, one more question...

Is there any way to neatly have the command line do this to all files in the directory?

Something like [COLOR="DarkRed"]Change *.avi into *-small.avi[/COLOR]?

---

### Post by ron999 on 2012-05-02
> **DavidVS said:**
> 
Is there any way to neatly have the command line do this to all files in the directory?

Hi
I suppose you would use something like...
for f in *.avi; do [your FFmpeg command]; done

But I think it's easiest to write a preset for **WinFF** then set it running to convert the batch.
Also it will be available to use again when you have other videos to convert.
Information here ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")

---

### Post by DavidVS on 2012-05-02
> **ron999 said:**
> But I think it's easiest to write a preset for **WinFF** then set it running to convert the batch.
Also it will be available to use again when you have other videos to convert.
Information here ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")

Wonderful!  Thank you again.

---

### Post by toddbmobile on 2013-01-06
This is great, but videos are about 630mb for a 44 minute kids film. Any way to get the file size down a bit? Thank you for your efforts.

---

### Post by evilsoup on 2013-01-06
You can set the quality with -q:v (or -qscale on older versions of ffmpeg). Lower number=higher quality, but larger filesize; the maximum (i.e. lowest quality) it goes to for mjpeg is 32. Use it like this:

```

ffmpeg -i input.avi -vf "scale=480:trunc(ow/a/2)*2" -c:v mjpeg  -r 15 -q:v 12 \
-c:a pcm_s16le -ar 20050 -ac 1 output.avi

```

Note that I've adapted the command that worked for the OP; if you have a different output requirement it may be preferable to change the command slightly.

Also, mjpeg will pretty much always produce bigger files than other codecs, it's pretty much the least efficient lossy codec out there in terms of filesize.

---

### Post by millsy2010 on 2013-03-15
Hi Ron999, I've been trawling the 'net for help on this topic and came across this thread.

However, as a computer user with fairly standard knowledge, I am struggling how to implement the command you have recommended here to get my mpeg files to convert for play in the Innotab.

I have downloaded some conversion software which enables me to convert to MJPEG, but when I drop the converted file into the relevant folder, it still won't play afterwards.

Are you able to help at all please?

Many thanks!

---

### Post by scotsha12 on 2013-06-20
I'm putting this one down here for my own reference and hopefully others.  I found that this works for me on my son's innotab2s.

Widescreen:
ffmpeg -i <input_file> -vcodec libx264 -profile:v baseline -b:v 600k -r 24 -s 480x272 -aspect 16:9 -acodec libmp3lame -af volume=<gain> -b:a 96k -ar 22050 <output_file>.avi

Fullscreen:
ffmpeg -i <input_file> -vcodec libx264 -profile:v  baseline -b:v 600k -r 24 -s 320x240 -aspect 4:3 -acodec libmp3lame -af  volume=<gain> -b:a 96k -ar 22050 <output_file>.avi

---

### Post by drjomy on 2014-01-20
I have found a solution to the problem the basic issue was innotab videos previously which was encoded with xvid codecs were much easy to use,but when innotab vtech upgraded the software they dont give money to xvid company and do not have the right s for it and so this is not included in the new firmware if you have updated the firmware to new you will have this problem ,,now in there site they have mentioned to convert to h264 format with tencorder but they have not mentioned the exact specifications and there are more than 60 formats ...now dont worry just watch this video from youtube ,get a tencorder software download for free and follow exactly as what it says ,,,believe me it was a success i have now more than 200 stories for my son on his tab now ,,,conversion is also very  fast link is
[http://www.youtube.com/watch?v=x_ZLTfVKg7w](http://www.youtube.com/watch?v=x_ZLTfVKg7w)  hope you find this useful

---

