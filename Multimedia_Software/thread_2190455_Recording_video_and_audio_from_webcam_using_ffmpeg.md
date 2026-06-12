---
title: "Recording video and audio from webcam using ffmpeg"
date: 2013-11-27
forum: Multimedia Software
---

### Post by volkerbradley on 2013-11-27
Am using Ubuntu 13.10, 64-bit.
When I record a video from my webcam with the following command:
ffmpeg -y -f alsa -ac 2 -i pulse -acodec pcm_s16le -f v4l2 -r 25 -s 640x480 -i /dev/video1 out.mkv 
I get a video in which the sound starts after the video.  I found many posts about this problem on the Internet.
At [https://trac.ffmpeg.org/ticket/692](https://trac.ffmpeg.org/ticket/692), I found a message that states:
**"The original problem - that starttime is broken for -f v4l2 apparently leading to completely broken A/V sync - was fixed by adding some options specific for -f v4l2, see ffmpeg -h full ("V4L2 indev AVOptions")."**
I looked at the V4L2 indev AVOptions in my v4l2.  They are:
V4L2 indev AVOptions:
  -standard          <string>        .D.... set TV standard, used only by analog frame grabber
  -channel           <int>             .D.... set TV channel, used only by frame grabber (from -1 to INT_MAX) (default -1)
  -video_size        <image_size> .D.... set frame size
  -pixel_format      <string>       .D.... set preferred pixel format
  -input_format      <string>       .D.... set preferred pixel format (for raw video) or codec name
  -framerate         <string>        .D.... set frame rate
  -list_formats      <int>            .D.... list available formats and exit (from 0 to INT_MAX) (default 0)
     all                                     .D.... show all available formats
     raw                                    D.... show only non-compressed formats
     compressed                        .D.... show only compressed formats
  -list_standards    <int>            .D.... list supported standards and exit (from 0 to 1) (default 0)
     all                                     .D.... show all supported standards
  -timestamps        <int>           .D.... set type of timestamps for grabbed frames (from 0 to 2) (default 0)
     default                               .D.... use timestamps from the kernel
     abs                                    .D.... use absolute timestamps (wall clock)
     mono2abs                           .D.... force conversion from monotonic to absolute timestamps
  -ts                <int>                .D.... set type of timestamps for grabbed frames (from 0 to 2) (default 0)
     default                               .D.... use timestamps from the kernel
     abs                                    .D.... use absolute timestamps (wall clock)
     mono2abs                           .D.... force conversion from monotonic to absolute timestamps
  -use_libv4l2       <int>             .D.... use libv4l2 (v4l-utils) convertion functions (from 0 to 1) (default 0)

Do you know what parameter one needs to change to delay the video portion for 1.5 seconds?

---

### Post by leeper69 on 2013-11-27
Hi volkerbradly have you tried kdenlive using your web cam as a vidio input and your mike as audio input I dont know how to run ffmpeg from the command line sorry I cant help with that but have used kdenlive and audacity to solve a simuler problem.

---

### Post by FakeOutdoorsman on 2013-11-27
First of all, please use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code) to help differentiate commands and outputs from your comments. As it is your post is hard to read. You should make it easy for those trying to help out: otherwise we'll just go on to the next question.

That bug report has been fixed in ffmpeg from FFmpeg, but Ubuntu uses a buggy, old, fake ffmpeg from a buggy fork. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017) You can simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

For the lazy (and this is what the code tag does):
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
```

Then run ffmpeg (note the "./" before "ffmpeg"):
```
./ffmpeg -y -f alsa -ac 2 -i pulse -acodec pcm_s16le -f v4l2 -framerate 25 -video_size 640x480 -i /dev/video1 out.mkv 
```

You should always include the complete ffmpeg console output that goes with your command.

---

### Post by volkerbradley on 2013-11-28
Thanks for your suggestion.
I have used kdenlive in the past.  However, I'm interested in getting this right with ffmpeg.

---

