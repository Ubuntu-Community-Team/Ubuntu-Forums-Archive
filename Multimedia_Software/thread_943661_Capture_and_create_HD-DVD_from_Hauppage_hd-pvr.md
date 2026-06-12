---
title: "Capture and create HD-DVD from Hauppage hd-pvr"
date: 2008-10-10
forum: Multimedia Software
---

### Post by xzero1 on 2008-10-10
To create a 720p video on a 4.7GB dvd-rw playable on a HD-DVD player captured from the Hauppage hd-pvr 1212:

Since I capture audio using the beta driver and spdif ac3, I modified the driver source to default to spdif input with ac3 encoding as follows:

in /home/user_name/hdpvr/linux/drivers/media/video/hdpvr
find and change the default_options structure in hdpvr-core.c to

```
static const struct hdpvr_options hdpvr_default_options = {
    .video_std    = HDPVR_60HZ,
    .video_input    = HDPVR_COMPONENT,
    .audio_input    = HDPVR_SPDIF,
    .bitrate    = 65, /* 6 mbps */
    .peak_bitrate    = 90, /* 9 mbps */
    .bitrate_mode    = HDPVR_CONSTANT,
    .gop_mode    = HDPVR_SIMPLE_IDR_GOP,
    .audio_codec    = V4L2_MPEG_AUDIO_ENCODING_AC3,
    .brightness    = 0x86,
    .contrast    = 0x80,
    .hue        = 0x80,
    .saturation    = 0x80,
    .sharpness    = 0x80,
};
```recompile and install
for reference see:
[http://www.mythtv.org/wiki/index.php/Hauppauge_HD_PVR](http://www.mythtv.org/wiki/index.php/Hauppauge_HD_PVR)
[http://www.avsforum.com/avs-vb/showthread.php?t=1069799](http://www.avsforum.com/avs-vb/showthread.php?t=1069799)

I captured the file using TME because I had not modified the driver and was getting no sound (sound was being captured from the back rca jacks as default).
after modifiying the driver, cat /dev/video1 > x.ts  does work although I have not authored to hd-dvd yet 
note: (be sure to choose the correct video device!)


Convert file to 2 channel mpg2:
ffmpeg -i x.ts -ac 2 -ar 4800 -ab 128k -s hd720 -b 8000k -threads 2 -f dvd x.mpg

If file is bigger than target split file with Avidemux or similar program.

Burn to dvd media using windows Ulead DVD MOVIE FACTORY. (I actually used windows xp)

NOTES:
The last step is a problem since windows IS required to author the hd-dvd.
The conversion step and windows should not be necessary if there was a way to put the original h264 ac3 files directly into an EVO container!
Nero for linux will burn but I don't think it creates an EVO container.
The file played back fine using a Venturer SHD-7000 HD-DVD player.
I used memorex DVD-RW as the burn medium.

**UPDATE!** -- Burn dvd without transcoding!

convert captured ts file to BD with tsMuxer
import BD folder using MOVIE FACTORY 6+:
  import dvd-video
  import dvd folder
Burn to dvd

Notes:
cat /dev/video1 >x.ts used to create video
Captured video was 720p @ 6Mb/s using 1 dvd-rw
I used the pvr beta firmware but v1.1 still seems to work with linux driver
new method is fast since transcoding not needed
windows still required

---

### Post by xzero1 on 2008-10-12
The ffmpeg bitrate parameter was in error. The parameter -b 8000 should be -b 8000k. The original post has been corrected.

---

### Post by xzero1 on 2008-10-25
:popcorn: New method needs no transcoding! See original edited post.

---

