---
title: "Convert OGV to FLV"
date: 2010-06-02
forum: Multimedia Software
---

### Post by zone z5 on 2010-06-02
I need to know how **_exactly_** to use FFmpeg to convert OGV to FLV.

EDIT: I don't understand a bit of coding.

---

### Post by FakeOutdoorsman on 2010-06-03
> **zone z5 said:**
> I need to know how **_exactly_** to use FFmpeg to convert OGV to FLV.

EDIT: I don't understand a bit of coding.

I'll assume you're using Ubuntu Lucid Lynx 10.04.

1. Open a terminal. You can find this at *Applications > Accessories > Terminal*.

2. Install FFmpeg.  In *terminal*, type the following (note that each line is a new command):
```
sudo apt-get update
sudo apt-get install ffmpeg libavcodec-extra-52
```
The **libavcodec-extra-52** package is required to enable encoders (such as *libmp3lame* and *libx264*) that are not enabled in the default FFmpeg package.  For more details, see: [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).

3. My *.ogv* is named *input.ogv* and is in */home/vidiot/videos*.  I'll navigate there.  Terminal will open in the home directory, so I only need to type:
```
cd videos
```

4. Now for the FFmpeg command. FLV is a container format that can handle several audio and video formats.  This example will use MP3 audio and H.264 video:
```
ffmpeg -i input.ogv -acodec libmp3lame -aq 4 -vcodec libx264 -vpre hq -crf 26 -wpredp 0 -threads 0 output.flv
```
This will create *output.flv*.  The *-wpredp 0* option is required to avoid a bug in Adobe Flash Player if you wanted to use this video in a Flash web player. For more info on the other options, see the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

---

### Post by zone z5 on 2010-06-04
Thank you, FakeOutdoorsman. Your help is much appreciated.

---

### Post by lisati on 2010-06-04
> **zone z5 said:**
>  I don't understand a bit of coding.
Don't sweat it: you don't need to know a lot of coding (i.e. programming) to use the command line/terminal. You might want to think of it as  just another way of using programs, that uses the keyboard instead of the mouse.

All the best with your adventures.

Edit: by the way, if memory serves correctly, on Kubuntu, the terminal is sometimes referred to as "Konsole".

---

