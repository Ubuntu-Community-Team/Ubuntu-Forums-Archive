---
title: "I am a linux noob trying to make an mkv from a series of PNG in avconv"
date: 2012-06-16
forum: Multimedia Software
---

### Post by VdubVidiot on 2012-06-16
Before anyone says it cant be done, read this from the avconv manual:

[I]" For creating a video from many images:

                   avconv -f image2 -i foo-%03d.jpeg -r 12 -s WxH foo.avi

           The syntax "foo-%03d.jpeg" specifies to use a decimal number
           composed of three digits padded with zeroes to express the sequence
           number. It is the same syntax supported by the C printf function,
           but only formats accepting a normal integer are suitable."[/I]

I have already had success with making an MKV with no audio out of 1 .png using the command below:

[I]"avconv -i /home/brandon/Downloads/480/sintel_trailer_2k_0001.png attempt.mkv"

 [/I]Now I need to make a full length MKV out of 1253 PNG files and here is the last command I tried that failed again:

"avconv -i /home/brandon/Downloads/480/sintel_trailer_2k_0001.png -f /home/brandon/Downloads/480/sintel_trailer_2k_foo-%03d.png attempt32.mkv

avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
Input #0, image2, from '/home/brandon/Downloads/480/sintel_trailer_2k_0001.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: png, rgb24, 854x480, 25 tbr, 25 tbn, 25 tbc
_[COLOR=Red]Requested output format '/home/brandon/Downloads/480/sintel_trailer_2k_foo-%03d.png' is not a suitable output format[/COLOR]_"

 Did I mention that I am a noob and I am not really sure how the syntax *"foo-%03d.jpeg"  *works so I have been trying various changes in syntax like [I]"/home/brandon/Downloads/480/sintel_trailer_2k_-%03d.jpeg" .

 [/I]I think I either can't figure out how the syntax in *"foo-%03d.jpeg"  (printf) *works*, *or else there is some command I can't seem to locate in the extensive avconv manual which would prevent avconv from mistaking the end of my PNG sequence for the output.

*Dear Friends*  h-e-l-p? :shock:

---

### Post by FakeOutdoorsman on 2012-06-16
I don't use avconv from the repository, but ffmpeg syntax is similar. Assuming you have images such as **sintel_trailer_2k_0001.png** to **sintel_trailer_2k_1253.png**:

```
ffmpeg -r 30 -i sintel_trailer_2k_%04d.png -qscale 3 output.mkv
```

Note that I added *-r 30* as an input option. By default the input images will be read at 25 fps, but if you add this option as I did you can change it to whatever value you want for the input and output frame rate. The output frame rate should then derive from the input frame rate.

I also added *-qscale 3*. This is to control the output quality for the "mpeg4" encoder which is the default encoder for MKV output. A higher value is a lower quality and therefore lower output file size. A good range to try is 2-5. A value of 2 can be considered "visually lossless".

---

### Post by VdubVidiot on 2012-06-17
> **FakeOutdoorsman said:**
> I don't use avconv from the repository, but ffmpeg syntax is similar. Assuming you have images such as **sintel_trailer_2k_0001.png** to **sintel_trailer_2k_1253.png**:

```
ffmpeg -r 30 -i sintel_trailer_2k_%04d.png -qscale 3 output.mkv
```Note that I added *-r 30* as an input option. By default the input images will be read at 25 fps, but if you add this option as I did you can change it to whatever value you want for the input and output frame rate. The output frame rate should then derive from the input frame rate.

I also added *-qscale 3*. This is to control the output quality for the "mpeg4" encoder which is the default encoder for MKV output. A higher value is a lower quality and therefore lower output file size. A good range to try is 2-5. A value of 2 can be considered "visually lossless".

Thank you so much for your help, your suggestions worked beautifully=D>

---

