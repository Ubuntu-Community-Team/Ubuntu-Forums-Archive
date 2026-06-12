---
title: "mencoder skipping frames"
date: 2015-10-18
forum: Multimedia Software
---

### Post by podlomar on 2015-10-18
Hi, I am really struggeling to record a video on my HP notebook from my web camera using command line tools. I have tried several command-line programs such as streamer, avconv and finally mencoder which seems most capable. However, even in quite low reseolution such as 800x600 I still get dropped frames. Here is my command. I am trying minimal settings, just 10 seconds of raw video for demonstration

```

mencoder tv:// -tv driver=v4l2:width=800:height=600:device=/dev/video1:fps=30 -nosound -ovc raw -frames 300 -o output.avi 

```

The output is:

```

MEncoder 1.1-4.8 (C) 2000-2012 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: HD Pro Webcam C920
 Capabilities:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Inappropriate ioctl for device
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
[V] filefmt:9  fourcc:0x32595559  size:800x600  fps:30.000  ftime:=0.0333
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
Writing header...
ODML: vprp aspect is 4:3.
Writing header...
ODML: vprp aspect is 4:3.
Pos:   0.3s      9f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]


1 duplicate frame(s)!
Pos:   0.6s     18f ( 0%) 17.19fps Trem:   0min   0mb  A-V:0.000 [0:0]


1 duplicate frame(s)!
Pos:   0.9s     26f ( 0%) 18.77fps Trem:   0min   0mb  A-V:0.000 [0:0]


6 duplicate frame(s)!
Pos:   1.0s     27f ( 0%) 19.04fps Trem:   0min   0mb  A-V:0.000 [0:0]


2 duplicate frame(s)!
Pos:   1.3s     30f ( 0%) 19.49fps Trem:   0min   0mb  A-V:0.000 [172800:0]


1 duplicate frame(s)!
Pos:   1.7s     40f ( 0%) 20.40fps Trem:   0min   0mb  A-V:0.000 [180705:0]


1 duplicate frame(s)!
Pos:   2.0s     49f ( 0%) 21.01fps Trem:   0min   0mb  A-V:0.000 [185075:0]


1 duplicate frame(s)!
Pos:   2.4s     58f ( 0%) 21.39fps Trem:   0min   0mb  A-V:0.000 [188214:0]


1 duplicate frame(s)!
Pos:   2.7s     67f ( 0%) 21.68fps Trem:   0min   0mb  A-V:0.000 [190577:0]


1 duplicate frame(s)!
Pos:   3.1s     77f ( 0%) 21.97fps Trem:   0min   0mb  A-V:0.000 [192834:0]


1 duplicate frame(s)!
Pos:   3.2s     80f ( 0%) 22.06fps Trem:   0min   0mb  A-V:0.000 [192000:0]


8 duplicate frame(s)!
Pos:   3.8s     89f ( 0%) 22.21fps Trem:   0min   0mb  A-V:0.000 [181465:0]


1 duplicate frame(s)!
Pos:   4.1s     98f ( 0%) 22.38fps Trem:   0min   0mb  A-V:0.000 [183570:0]


1 duplicate frame(s)!
Pos:   4.5s    108f ( 0%) 22.54fps Trem:   0min   0mb  A-V:0.000 [185695:0]


1 duplicate frame(s)!
Pos:   4.8s    117f ( 0%) 22.63fps Trem:   0min   0mb  A-V:0.000 [187200:0]


1 duplicate frame(s)!
Pos:   5.1s    126f ( 0%) 22.71fps Trem:   0min   0mb  A-V:0.000 [188509:0]


1 duplicate frame(s)!
Pos:   5.4s    134f ( 0%) 22.56fps Trem:   0min   0mb  A-V:0.000 [189408:0]


6 duplicate frame(s)!
Pos:   5.5s    135f ( 0%) 22.72fps Trem:   0min   0mb  A-V:0.000 [189658:0]


2 duplicate frame(s)!
Pos:   5.8s    138f ( 0%) 22.84fps Trem:   0min   0mb  A-V:0.000 [181686:0]


1 duplicate frame(s)!
Pos:   6.2s    148f ( 0%) 22.90fps Trem:   0min   0mb  A-V:0.000 [183329:0]


1 duplicate frame(s)!
Pos:   6.5s    157f ( 0%) 22.98fps Trem:   0min   0mb  A-V:0.000 [184555:0]


1 duplicate frame(s)!
Pos:   6.9s    166f ( 0%) 23.02fps Trem:   0min   0mb  A-V:0.000 [185662:0]


1 duplicate frame(s)!
Pos:   7.2s    175f ( 0%) 23.05fps Trem:   0min   0mb  A-V:0.000 [186666:0]


1 duplicate frame(s)!
Pos:   7.6s    185f ( 0%) 23.11fps Trem:   0min   0mb  A-V:0.000 [187770:0]


1 duplicate frame(s)!
Pos:   7.7s    188f ( 0%) 23.14fps Trem:   0min   0mb  A-V:0.000 [187511:0]


8 duplicate frame(s)!
Pos:   8.3s    197f ( 0%) 23.16fps Trem:   0min   0mb  A-V:0.000 [183019:0]


1 duplicate frame(s)!
Pos:   8.6s    206f ( 0%) 23.21fps Trem:   0min   0mb  A-V:0.000 [183962:0]


1 duplicate frame(s)!
Pos:   8.9s    215f ( 0%) 23.23fps Trem:   0min   0mb  A-V:0.000 [184835:0]


1 duplicate frame(s)!
Pos:   9.3s    225f ( 0%) 23.27fps Trem:   0min   0mb  A-V:0.000 [185806:0]


1 duplicate frame(s)!
Pos:   9.3s    226f ( 0%) 23.22fps Trem:   0min   0mb  A-V:0.000 [185965:0]


1 duplicate frame(s)!
Pos:   9.4s    227f ( 0%) 23.14fps Trem:   0min   0mb  A-V:0.000 [185463:0]


1 duplicate frame(s)!
Pos:   9.5s    228f ( 0%) 23.10fps Trem:   0min   0mb  A-V:0.000 [184969:0]


1 duplicate frame(s)!
Pos:   9.6s    230f ( 0%) 22.98fps Trem:   0min   0mb  A-V:0.000 [184000:0]


1 duplicate frame(s)!
Pos:   9.6s    231f ( 0%) 22.93fps Trem:   0min   0mb  A-V:0.000 [184160:0]


1 duplicate frame(s)!
Pos:   9.7s    232f ( 0%) 22.89fps Trem:   0min   0mb  A-V:0.000 [183686:0]


1 duplicate frame(s)!
Pos:   9.8s    234f ( 0%) 22.78fps Trem:   0min   0mb  A-V:0.000 [182757:0]


1 duplicate frame(s)!
Pos:   9.9s    235f ( 0%) 22.74fps Trem:   0min   0mb  A-V:0.000 [182918:0]


7 duplicate frame(s)!
Pos:   9.9s    236f ( 0%) 22.67fps Trem:   0min   0mb  A-V:0.000 [182464:0]


2 duplicate frame(s)!
Pos:  10.2s    237f ( 0%) 22.63fps Trem:   0min   0mb  A-V:0.000 [178447:0]


1 duplicate frame(s)!
Pos:  10.3s    238f ( 0%) 22.59fps Trem:   0min   0mb  A-V:0.000 [177460:0]


1 duplicate frame(s)!
Pos:  10.4s    239f ( 0%) 22.55fps Trem:   0min   0mb  A-V:0.000 [177059:0]


1 duplicate frame(s)!
Pos:  10.4s    240f ( 0%) 22.49fps Trem:   0min   0mb  A-V:0.000 [176664:0]


1 duplicate frame(s)!
Pos:  10.6s    242f ( 0%) 22.41fps Trem:   0min   0mb  A-V:0.000 [175888:0]


1 duplicate frame(s)!
Pos:  10.6s    243f ( 0%) 22.35fps Trem:   0min   0mb  A-V:0.000 [176060:0]


1 duplicate frame(s)!
Pos:  10.7s    244f ( 0%) 22.31fps Trem:   0min   0mb  A-V:0.000 [175680:0]


1 duplicate frame(s)!
Pos:  10.8s    246f ( 0%) 22.21fps Trem:   0min   0mb  A-V:0.000 [174933:0]


1 duplicate frame(s)!
Pos:  10.8s    247f ( 0%) 22.18fps Trem:   0min   0mb  A-V:0.000 [175104:0]


1 duplicate frame(s)!
Pos:  10.9s    248f ( 0%) 22.14fps Trem:   0min   0mb  A-V:0.000 [174737:0]


1 duplicate frame(s)!
Pos:  11.2s    255f ( 0%) 22.13fps Trem:   0min   0mb  A-V:0.000 [174857:0]


1 duplicate frame(s)!
Pos:  11.5s    264f ( 0%) 22.18fps Trem:   0min   0mb  A-V:0.000 [175796:0]


1 duplicate frame(s)!
Pos:  11.9s    274f ( 0%) 22.25fps Trem:   0min   0mb  A-V:0.000 [176833:0]


1 duplicate frame(s)!
Pos:  12.2s    282f ( 0%) 22.31fps Trem:   0min   0mb  A-V:0.000 [177521:0]


6 duplicate frame(s)!
Pos:  12.2s    283f ( 0%) 22.31fps Trem:   0min   0mb  A-V:0.000 [177665:0]


2 duplicate frame(s)!
Pos:  12.6s    286f ( 0%) 22.32fps Trem:   0min   0mb  A-V:0.000 [174323:0]


1 duplicate frame(s)!
Pos:  12.9s    295f ( 0%) 22.37fps Trem:   0min   0mb  A-V:0.000 [175175:0]


1 duplicate frame(s)!
Pos:  13.1s    300f ( 0%) 22.40fps Trem:   0min   0mb  A-V:0.000 [175431:0]


Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 4:3.


Video stream: 175431.469 kbit/s  (21928934 B/s)  size: 288000000 bytes  13.133 secs  300 frames
v4l2: ioctl set mute failed: Invalid argument
v4l2: 302 frames successfully processed, 95 frames dropped.

```

So my question is: what is the reason for that? My camera is HD Pro Webcam C920 connected through USB 2.0, it is certainly capable of HD 1920x1080 30fps so 800x600 30fps should not be a problem. Is it a hardware problem of my notebook?

[LIST]
[*]Is my CPU to slow? I have Intel Core i3 2.13 GHz
[*]Is the harddrive too slow? I have an ATA Samsung SSD disk
[*]Is the USB 2.0 too slow?
[*]Is integrated graphics card not suitable for such task?
[/LIST]

or is it a software problem?
[LIST]
[*]Bad kernel? I have 3.13.0-58-lowlatency
[*]Bad drivers?
[*]Some missconfiguration of the mencoder? I admit do not understand many of its advanced parameters.
[/LIST]

Am I too naive to try to capture webcam video on my notebook with integrated graphics? Should I use a desktop computer with a decent graphics card?

Thanks for any help.

---

### Post by TheFu on 2015-10-18
The C920 doesn't have solid drivers under Linux. It worked back with 12.04, but stopped after that. It is unclear to me why this is true. The C910 does have drivers, if that is an option.

[https://forums.logitech.com/t5/Webcams/C920-driver-for-Ubuntu-VersionX-Fedora-VersionX-or-ArchLinux/m-p/849876](https://forums.logitech.com/t5/Webcams/C920-driver-for-Ubuntu-VersionX-Fedora-VersionX-or-ArchLinux/m-p/849876)

I'm in the same boat. ;(
Bought a c920 when on 12.04 and it worked well.  Since then, bad to zero support. For example, OBS works about 20 min then crashes. Using uvcview/guvcview no video can be captured at all from the c920 - I got it working 8 months ago, but it stopped. No idea why. uvcview/guvcview works fine with the built-in netbook camera.

---

