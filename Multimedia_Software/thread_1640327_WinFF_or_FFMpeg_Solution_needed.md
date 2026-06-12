---
title: "WinFF or FFMpeg Solution needed"
date: 2010-12-07
forum: Multimedia Software
---

### Post by jlabomb on 2010-12-07
I am posting this here since the WinFF forum is down. 

At work I can use winff to convert files to be compatible with our video playback servers. There is a 3 step process to do it though. First the file must be converted to a mpg file if it is not already one(Use DVD HQ FullScreen). Then it must be converted to a DV file(Use NTSC FullScreen). Then Convert to a custom preset that gives it a avi wrapper. 

Here is that preset.
```
<?xml version="1.0"?>

<presets>

  <CopytoAVI>

    <label>Copy Video Audio to AVI Wrapper</label>

    <params>-acodec copy -vcodec copy -ab 192kb -b 25000kb -s 720x480 -ar 48000</params>

    <extension>avi</extension>

    <category>AVI</category>

  </CopytoAVI>

</presets>
```


Is there a way to make a preset to run this conversion to end up with a working file? I had thought about making a java program with a watch folder then execute ffmepg using the command line to run the three conversions. I just wasn't sure what is the best way to approach this.

The final video file will have these specifications.

File Type: AVI

Video Compression: DV25 (SMPTE 314)

Encoder Type: Type 1 or Type 2 (interleaved or non-interleaved)

Color Sampling 4:1:1 525 Line NTSC

Resolution: 720x480

Frame Rate: 29.97 Hz

Audio Sampling 16 bit PCM, 48Khz sample rate

VLC shows the video codec to be DV Video(dvsd) 720 x 480  at 29.97fps and audio to be PCM S16LE(araw) stereo 48000Hz and 16 bit.


There may be a better way to end up with the file I need. Any Ideas?

---

### Post by FakeOutdoorsman on 2010-12-07
> **jlabomb said:**
> At work I can use winff to convert files to be compatible with our video playback servers.
What type of servers? What are you using for playback?

> **jlabomb said:**
> There is a 3 step process to do it though. First the file must be converted to a mpg file if it is not already one(Use DVD HQ FullScreen). Then it must be converted to a DV file(Use NTSC FullScreen). Then Convert to a custom preset that gives it a avi wrapper.

Why do you need .avi? Will .dv do? Do you need both mpg and dv outputs, or are you encoding to mpg as an intermediate file for some reason?

> **jlabomb said:**
> ```
-acodec copy -vcodec copy -ab 192kb -b 25000kb -s 720x480 -ar 48000
```

The **-acodec copy -vcodec copy** options are not compatible with the rest of your options, and therefore the -ab, -b, -s and -ar options are probably being ignored by FFmpeg.  Also, you should get in the habit of using "k" instead of "kb" (as in *-ab 192k*) because if you eventually use a more recent version of FFmpeg it will complain:
```
[NULL @ 0x1228480] [Eval @ 0x7fffcdd54140] Invalid chars 'b' at the end of expression '192kb'
[NULL @ 0x1228480] Unable to parse option value "192kb"
```

> **jlabomb said:**
> Is there a way to make a preset to run this conversion to end up with a working file? I had thought about making a java program with a watch folder then execute ffmepg using the command line to run the three conversions. I just wasn't sure what is the best way to approach this.
JAVA? I'm not a fan. I would just make a simple bash script with a cronjob to check the directory every *n* seconds/minutes/hours/whatever. Might not be elegant, but it would work.

---

### Post by jlabomb on 2010-12-07
> **FakeOutdoorsman said:**
> What type of servers? What are you using for playback?

They are Grass Valley M-series IVDR


> **FakeOutdoorsman said:**
> 
Why do you need .avi? Will .dv do? Do you need both mpg and dv outputs, or are you encoding to mpg as an intermediate file for some reason?


The server will only import two types of files AVI with the specifications I listed or a .gfx file which I am not sure of the specs. For some reason the conversion process only works if it is a Mpeg2 file. Don't know why.


> **FakeOutdoorsman said:**
> 
JAVA? I'm not a fan. I would just make a simple bash script with a cronjob to check the directory every *n* seconds/minutes/hours/whatever. Might not be elegant, but it would work.

I only choose JAVA cause its something I know and has a built in folder watch option. I will look into the bash script.

---

### Post by FakeOutdoorsman on 2010-12-08
> **jlabomb said:**
> The server will only import two types of files AVI with the specifications I listed or a .gfx file which I am not sure of the specs. For some reason the conversion process only works if it is a Mpeg2 file. Don't know why.
You shouldn't need to create the intermediate file. Try these:

Raw DV. Your device might be picky, but it's worth a try because it's the easiest command:
```
ffmpeg -i input -t 60 -target ntsc-dv output.dv
```
This next command attempts to emulate *-target ntsc-dv*, but outputs an avi container. We can't simply change the extension to "avi" and expect to actually be an AVI because of a hidden *-f dv* that I assume is being applied when *-target ntsc-dv* is used:
```
ffmpeg -i input -t 60 -vcodec dvvideo -s 720x480 -pix_fmt yuv411p -r ntsc -acodec pcm_s16le -ar 48000 -ac 2 output.avi
```
Yet another workaround. FFmpeg piping the output to itself. I used to use this with an old version of Adobe Premiere because it didn't like Raw DV and because it liked to re-encode my inputs too often even if they were DV AVI (if I remember correctly):
```
ffmpeg -i input -t 60 -target ntsc-dv - | ffmpeg -i - -acodec copy -vcodec copy output2.avi
```
Each of these examples uses the *-t 60* option which will create a 60 second file so you can test without having to encode a long video. You can remove it once you find a working command.

> **jlabomb said:**
> I only choose JAVA cause its something I know and has a built in folder watch option. I will look into the bash script.
Use JAVA if that's what you're comfortable with. I shouldn't say much about JAVA because I've hardly used it.

---

### Post by jlabomb on 2010-12-09
The 2nd and third options work perfect in ffmpeg. I used the second to build a preset for WinFF so it will be easy for the users to run. 


```
<?xml version="1.0"?>

<presets>

  <dvntscavi>

    <label>Raw DV AVI for Grassvalley</label>

    <params>-vcodec dvvideo -s 720x480 -pix_fmt yuv411p -r ntsc -acodec pcm_s16le -ar 48000 -ac 2</params>

    <extension>avi</extension>

    <category>Grassvalley</category>

  </dvntscavi>

</presets>
```


Thanks again that was just the help I was looking for. One more quick question is there a way to adjust audio levels in ffmpeg? I did not see one in the documentation. Would be sweet if so but not necessary.

---

### Post by FakeOutdoorsman on 2010-12-09
> **jlabomb said:**
> One more quick question is there a way to adjust audio levels in ffmpeg?

What type of adjustment are you wanting to perform? There's the **-vol** option in FFmpeg, but I've never found it very useful. SoX is the "Swiss Army knife of audio manipulation" and would be worth investigating.  See the sox examples in: [FFmpeg and 'Fist of Fury'](http://www.andrews-corner.org/fist.html).

---

### Post by jlabomb on 2010-12-10
Videos come in from different sources and some have loud audio. So to have a good level we have to load a seperate program and adjust the audio. Would be easier in this same step if it works. Do you use + = - signs and a number? I will give it a try.

---

