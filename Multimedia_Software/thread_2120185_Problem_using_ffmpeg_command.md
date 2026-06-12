---
title: "Problem using ffmpeg command"
date: 2013-02-25
forum: Multimedia Software
---

### Post by Arun Krishnan on 2013-02-25
I am using a Creative Webcam NX Ultra(Model No-PD1120) . I tried using the following command to capture the webcam video to an avi file.
ffmpeg -f video4linux2 -s 640x480 -i /dev/video0 -y sample.avi 

I am getting the following error message:
ffmpeg version N-50294-gbb7bc34 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 25 2013 12:06:20 with gcc 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
  configuration: 
  libavutil      52. 17.103 / 52. 17.103
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 41.100 /  3. 41.100
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
[video4linux2,v4l2 @ 0x2d300e0] Cannot find a proper format for codec 'none' (id 0), pixel format 'none' (id -1)
Assertion *codec_id != AV_CODEC_ID_NONE failed at libavdevice/v4l2.c:824
Aborted


Can anyone help me with this please, my situation is very critical. I expect some help very soon. Thank you in advance.

---

### Post by evilsoup on 2013-02-26
Hmm... it's almost a shot in the dark, but try:

```

ffmpeg -y -f video4linux2 -c:v rawvideo -s 640x480 -i /dev/video0 sample.avi

```

Also, just to check, the webcam is turned on in your BIOS? Can you use it in other applications, like cheese or skype?

---

### Post by FakeOutdoorsman on 2013-02-26
Please show the output of:
```
ffmpeg -f video4linux2 -list_formats all -i /dev/video0
```

---

### Post by Arun Krishnan on 2013-02-27
Thanks to both of you for your support, i have listed the output of the commands you listed:

output of the command requested by FakeOutdoorsman:
ffmpeg -f video4linux2 -list_formats all -i /dev/video0

ffmpeg version N-50294-gbb7bc34 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 25 2013 12:06:20 with gcc 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
  configuration: 
  libavutil      52. 17.103 / 52. 17.103
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 41.100 /  3. 41.100
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
[video4linux2,v4l2 @ 0x28c8c20] Raw       : Unsupported :                 S505 : 160x120 176x144 320x240 352x288 640x480
/dev/video0: Immediate exit requested

@evilsoup: tried out the comman you requested, am getting the error
ffmpeg -y -f video4linux2 -c:v rawvideo -s 640x480 -i /dev/video0 sample.avi


ffmpeg version N-50294-gbb7bc34 Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 25 2013 12:06:20 with gcc 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
  configuration: 
  libavutil      52. 17.103 / 52. 17.103
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 41.100 /  3. 41.100
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
[video4linux2,v4l2 @ 0x30b5180] Cannot find a proper format for codec 'rawvideo' (id 14), pixel format 'none' (id -1)
Assertion *codec_id != AV_CODEC_ID_NONE failed at libavdevice/v4l2.c:824
Aborted

---

### Post by Arun Krishnan on 2013-03-04
No reply yet :(

---

### Post by FakeOutdoorsman on 2013-03-06
Also show the output of:
```
v4l2-ctl --list-formats-ext
```
Please use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code) for the console outputs. It makes reading your posts easier.

---

### Post by Arun Krishnan on 2013-03-11
Thank you for your reply, i got the output using a Phillips Webcam. It seems the webcam i used never had v4l2-compatibility.

---

