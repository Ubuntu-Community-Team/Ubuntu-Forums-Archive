---
title: "Convert videos in high quality for Nokia 5800 using ffmpeg"
date: 2009-04-14
forum: Multimedia Software
---

### Post by speakman on 2009-04-14
I just found out a perfect working settings with ffmpeg to convert movies into a Nokia 5800 compatible format:

```
ffmpeg -i input.avi -f mp4 -vcodec mpeg4 -b 2200k -r 30 -s 640x360 -acodec libfaac -ar 32000 -ab 128k -ac 2 -threads 8 output.mp4

```

I'm using a quad core CPU, and therefore -threads 8 (which still won't utilize the CPU fully).

Hopefully a real ffmpeg guru could complement this into a more optimal way, but this works perfectly and a 2 hour movie generates an below 2GB high quality video suitable for the Nokia 5800.

I hope this will help people trying to accomplish the same thing.

---

### Post by FakeOutdoorsman on 2009-04-14
Looks like this phone can play MPEG4-AVC ([specifications](http://www.nokia.co.uk/find-products/all-phones/nokia-5800/specifications)).  This means that you can use the libx264 presets which can result in some excellent quality video:

**One-Pass CRF**
One-pass CRF lets you specify a quality to encode at, but the file size will be unknown:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -vcodec libx264 -vpre hq -vpre baseline -s 320x240 -threads 0 -crf 26 output.mp4
```
Perhaps the phone doesn't need the baseline limitation:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -vcodec libx264 -vpre hq -s 320x240 -threads 0 -crf 26 output.mp4
```
You may want to just encode a set amount of time to test this video instead of the whole thing.  You can do that with the "-t" option.  This example will encode the first 10 seconds:
```
ffmpeg -t 10 -i input.avi -acodec libfaac -ab 128k -vcodec libx264 -vpre hq -vpre baseline -s 320x240 -threads 0 -crf 26 output.mp4
```
The most important option is crf.  The lower the number, the higher the quality, and 18-30 is a sane range.

Unfortunately, to take advantage of the presets you will need to compile FFmpeg yourself, although it isn't hard:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

See the above thread for some two-pass examples.  Two-pass encoding lets you specify a bitrate (and thus a final file size), but the quality can vary.

---

### Post by speakman on 2009-04-14
Thanks alot for your additions. I never got it working with libx264, but I'll test your settings soon and report.

And thanks for the HOWTO link which I used myself but forgot to tell about.

---

### Post by m3topaz on 2009-04-14
Here's a quick and dirty one if you want a fast (~30mins) rip of an 2.35:1 anamorphic DVD for the 5800:
$ HandBrakeCLI -i /dev/cdrom -t 2 -w 640 -l 360 --crop 17:17:0:0 -o /home/me/<filename>.mp4

Use the t switch to choose the right track off the DVD; the crop setting will chop if it's not 2.35

The bits I liked are that the ripping is direct, takes about half an hour, produces pretty good mp4, and cuts about a 1.2GB output file. Half a dozen DVDs on an 8GB micro SD - enough for an intercontinental flight!

You need to install HandBrakeCLI, of course but it's a good option for the 5800, IMHO.

---

### Post by speakman on 2009-04-14
Great!

One thing left; do subtitles has to be embedded in the video or is there any way to attach them into movies?

Else; is it possible through ffmpeg/HandBrakeCLI to embedd it in the video?

---

### Post by speakman on 2009-04-15
@FakeOutdoorsman

I just tried your suggestions but none did work. It says either sound or video is not working, and then it starts playen the sound alone. No video. :(

Any ideas how to bring the file size down using mpeg4 as in my first post?

---

### Post by FakeOutdoorsman on 2009-04-15
I rarely encode with *-vcodec mpeg4*, but I suppose you could simply decrease the bitrate:
```
ffmpeg -i input.avi -vcodec mpeg4 -b 512k -s 640x360 -acodec libfaac -ab 128k -ac 2 -threads 8 output.mp4
```
I also changed *-threads* to 0 to let FFmpeg automatically choose the correct number of threads.  You can add additional quality parameters, but they will slow your encode and your device may not play the resulting video:

[FFmpeg FAQ: Which are good parameters for encoding high quality MPEG-4?](http://ffmpeg.mplayerhq.hu/faq.html#SEC26)

If you follow the above link make sure to change *4mv* to *mv4* if you are using SVN FFmpeg as the documentation is out of date.

**Update**:  I still think H.264 videos are possible.  Try this 1 minute example:
```
ffmpeg -t 00:01:00:00 -i input.avi -acodec libfaac -ab 96k -vcodec libx264 -vpre hq -vpre ipod320 -r 30 -s 320x240 -threads 0 -b 512k -bt 512k -f ipod output.mp4
```

---

### Post by gpmelendez on 2009-05-01
I can convert to h264 and play on my device.
```
ffmpeg -i "input.avi" -f mp4 -vcodec libx264 -b 1000k -r 30 -s 320x240 -acodec libfaac -ar 32000 -ab 128k -ac 2 -threads 0 -async 1 "output.mp4" -crf 26
```

if found it [here]("http://www.blastingvolume.com/2009/05/convert-video-to-h264-for-nokia-5800.html")

---

### Post by FakeOutdoorsman on 2009-05-01
> **gpmelendez said:**
> I can convert to h264 and play on my device.
```
ffmpeg -i "input.avi" -f mp4 -vcodec libx264 -b 1000k -r 30 -s 320x240 -acodec libfaac -ar 32000 -ab 128k -ac 2 -threads 0 -async 1 "output.mp4" -crf 26
```

if found it [here]("http://www.blastingvolume.com/2009/05/convert-video-to-h264-for-nokia-5800.html")

The syntax of the command is incorrect.  FFmpeg will ignore any options declared after the output file, so *-crf 26* isn't being applied.  This is probably a good thing because using *-b* **and** *-crf* is contradictory.  It is recommended to either use one of the other, but not both at the same time.  See [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more details.

---

### Post by gpmelendez on 2009-05-02
> **FakeOutdoorsman said:**
> The syntax of the command is incorrect.  FFmpeg will ignore any options declared after the output file, so *-crf 26* isn't being applied.  This is probably a good thing because using *-b* **and** *-crf* is contradictory.  It is recommended to either use one of the other, but not both at the same time.  See [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more details.

I also noticed that ffmpeg forces 16:9 if the input is 16:9, leading to resolutions higher than 320x240 that won't play on the device. 16:9 videos will shrink to 4:3 but the device will stretch it out again, and still looks great. here's the corrected code.

```
ffmpeg -i "input.avi" -f mp4 -vcodec libx264 -r 30 -s 320x240 -acodec libfaac -ar 32000 -ab 128k -ac 2 -threads 0 -async 1  -crf 26 -aspect 4:3 "output.mp4"
```

i have a question, should i still include -ar ?

---

### Post by ronthedon on 2009-06-04
Another way to convert. Get Avidemux. Open the file in Avidemux to be converted. Goto Auto tab, choose IPOD. Select Target type for 640x480. Goto Video tab, and select Filters. Under filter, remove add black border. Under MPlayer Reseize, set the width to 360. You are done. Just save the file.

---

### Post by laserburn on 2009-06-17
> **ronthedon said:**
> Another way to convert. Get Avidemux. Open the file in Avidemux to be converted. Goto Auto tab, choose IPOD. Select Target type for 640x480. Goto Video tab, and select Filters. Under filter, remove add black border. Under MPlayer Reseize, set the width to 360. You are done. Just save the file.

You, sir, are full of win. It works great. Takes a lot of time to encode, but it plays flawlessly.

---

### Post by robinl on 2009-06-17
Or use Handbrake; change container to MP4, resize it if it's bigger than 640×360 (otherwise it won't play, but smaller resolution there's no point in upscaling), change video codec to "MPEG4 (FFMPEG"), disable 2-pass encoding (or Handbrake crashes on me), change bitrate, change the audio codec to AAC and bitrate to 128, and press start!

---

### Post by cmistake on 2009-07-02
I've tried pretty much everything here but libx264 just doesn't work. I think the problem is with the phones firmware, and although it should play H264 it doesn't. 
While googling around I found out that H264 files play on N95 flawlessly, but the same files don't play on 5800XM, though they both have the same video support in the official specs.

After encoding with about 20 different settings I'm pretty sure this is the case

---

### Post by ddalex on 2009-07-10
I managed to finally convert videos for 5800 using h264. My best command line is:

```
ffmpeg -i "$FILE.avi" -f mp4 -vcodec libx264 -r 30 -s 320x240 -qcomp 0.6 -qmin 11 -qmax 51 -qdiff 4 -flags +loop -cmp +chroma -subq 7 -refs 6 -g 250 -keyint_min 25 -rc_eq 'blurCplx^(1-qComp)' -sc_threshold 40 -me_range 12 -i_qfactor 0.71 -directpred 3 -f mp4 -threads 4 -acodec libfaac -ar 22050 -ab 64k -ac 2 -async 1 -crf 26 -aspect 4:3 "$FILE.mp4"

```

Put simply, it has to be 30 fps, 320x240 (other resolutions will fail to play), if you're having 16:9 content resize it with 4:3 aspect ration, and use the 5800's "stretch" display to view it in 16:9 format. 
The command above will yield about 230kbit/sec bitrate, with satisfying quality (it was watchable on video out, very nice on the phone display). 

However I can't get the mp4 file to stream (it must be fully downloaded before playing), can anybody suggest a solution?

---

### Post by FakeOutdoorsman on 2009-07-10
> **ddalex said:**
> However I can't get the mp4 file to stream (it must be fully downloaded before playing), can anybody suggest a solution?

Try running it through qt-faststart (part of the FFmpeg package).  This will re-arrange some data in the video file so it can start playing before being downloaded:
```
qt-faststart input.mp4 output.mp4
```

If your version of FFmpeg doesn't have qt-faststart, then try MP4Box from the gpac package:
```
MP4Box -add input.mp4 output.mp4
```

---

### Post by kamikazeee on 2009-07-13
> **ddalex said:**
> I managed to finally convert videos for 5800 using h264. My best command line is:

```
ffmpeg -i "$FILE.avi" -f mp4 -vcodec libx264 -r 30 -s 320x240 -qcomp 0.6 -qmin 11 -qmax 51 -qdiff 4 -flags +loop -cmp +chroma -subq 7 -refs 6 -g 250 -keyint_min 25 -rc_eq 'blurCplx^(1-qComp)' -sc_threshold 40 -me_range 12 -i_qfactor 0.71 -directpred 3 -f mp4 -threads 4 -acodec libfaac -ar 22050 -ab 64k -ac 2 -async 1 -crf 26 -aspect 4:3 "$FILE.mp4"

```

Put simply, it has to be 30 fps, 320x240 (other resolutions will fail to play), if you're having 16:9 content resize it with 4:3 aspect ration, and use the 5800's "stretch" display to view it in 16:9 format. 
The command above will yield about 230kbit/sec bitrate, with satisfying quality (it was watchable on video out, very nice on the phone display). 


Thanks, it worked!

---

### Post by LaLLi on 2009-08-16
After trying all the methods I finally found one that works best for me. As a bonus it has a GUI and it's easy.
[http://ubuntuforums.org/showthread.php?p=7796515#post7796515](http://ubuntuforums.org/showthread.php?p=7796515#post7796515)

---

### Post by orbisonitrum on 2009-10-03
Mediacoder in Wine works perfectly for me. I encode 640x360 videos, add subtitles (when needed).

I use the following preset for nokia 5800:

```

<?xml version="1.0" encoding="UTF-8"?>
<MediaCoderPrefs><node key="overall.ui.optionTab">4</node><node key="overall.ui.param">680,640,986,369</node><node key="overall.video.bitrate">512</node><node key="overall.video.format">MPEG4</node><node key="videofilter.scale.enabled">true</node><node key="videofilter.scale.width">640</node><node key="videofilter.scale.height">360</node></MediaCoderPrefs>

```

Settings: 

Video: 
Format: MPEG4
Mode: Bitrate-based (512)

Audio:
Encoder: LAME mp3 (bitrate 128)

Container: MP4

Picture: 
Resize: 640x360
Crop: Disabled

---

### Post by LivingSouL on 2010-11-17
This one seems to work for me...

```
ffmpeg -i "file.avi" -f mp4 -vcodec mpeg4 -b 768k -r 30 -s 640x360 -acodec libfaac -ar 32000 -ab 128k -ac 2 -threads 8 file.mp4
```

---

### Post by wingnux on 2010-11-17
Works like a charm, thanks!

---

### Post by kiran.tambe08 on 2011-04-08
ive tried all these settings but they just dont work on my nokia 5230. unable to play clip is the error i get. it works on the pc :(

---

### Post by Cyr4x on 2011-07-27
Avidemux settings:

Video:
codec Mpeg4 (XviD)
bitrate 1500-2000 (gives a good compromise between quality and file size)
the rest of settings can be default
resize to 640x360 using Mplayer resize filter with biupic resize method (gives sharper image than default bilinear)

Audio:
codec AAC
bitrate 128

Container:
mp4

---

### Post by stefmorp on 2011-10-19
Kiran,

I have been able to convert videos for Nokia 5230. I am using winff, a friendly graphical front end for ffmpeg. You can install winff from Ubuntu software center. winff allows you to create "presets" that is, predefined conversion setups that are then passed on to ffmpeg. Once you have installed winff, you will find the presets file in a subdirectory of your home named .winff. If for example your home is /home/kiran, the presets file will be:

/home/kiran/.winff/presets.xml

Open the presets with an editor of your choice, and append at the end, just before the </presets> tag, the following preset:

 <S5230>
    <label>Nokia 5230 mplayer 16:9</label>
    <params>-f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2</params>
    <extension>mp4</extension>
    <category>Nokia</category>
  </S5230>

When you launch winff, you will find in the Nokia section of the presets a new preset aptly named Nokia 5230 that converts any video to perfectly fill your phone screen.

Enjoy!
Stefano

---

