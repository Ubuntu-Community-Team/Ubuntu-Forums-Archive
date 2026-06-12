---
title: "Creating DVD videos from the command line"
date: 2013-03-01
forum: Multimedia Software
---

### Post by George Heine on 2013-03-01
Hello -  

For several months I was successfully creating video DVDs using tovid ([http://tovid.wikia.com/wiki/Installing_tovid](http://tovid.wikia.com/wiki/Installing_tovid)).  This all went bust after upgrading my system to Ubuntu 12.04.  The tovid package in the repo went backwards from 0.34 to 0.33.  I did manually reinstall 0.34, but it didn't seem to help.   When I try and run "tovid mpg" on one of my video clips, it fails about half the time with a message:
```
[tovid]: tovid encountered an error during encoding:
[tovid]:     Could not identify source video: <video name>
```This message seems to come from tovid's "idvid" script (lines 1123-1125):
```
   if eval $(idvid -terse "$IN_FILE" 2>/dev/null); then :; else
        runtime_error "Could not identify source video: $IN_FILE"
    fi
```Anyway, figured it's time to throw away the tovid crutch and learn how to use ffmpeg, mplayer, mpeg2enc, or other command-line tools, directly, to convert one of my existing video clips to a video-DVD compliant format.  Can anyone help me with this?  In the USA, using an NTSC DVD player.   Attached below is sample output from "mplayer -identify" one one of my short videos.  This example comes from a Samsung camera in MOV format.  As an additional complication, the original was taken with the camera held sideways, so the video needs to be rotated 90 degrees counterclockwise.  I know how to do this in ffmpeg (using   -vf "transpose=2" ), but not how to turn that result into something that will play on my DVD. 

Hope this is clear - any help would be much appreciated!

```
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
Playing IMG_0037.MOV.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  1920x1080  24bpp  24.000 fps  17156.8 kbps (2094.3 kbyte/s)
Clip info:
 major_brand: qt
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=qt
 minor_version: 0
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=0
 compatible_brands: qt
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=qt
 creation_time: 2012-12-27 23:18:48
ID_CLIP_INFO_NAME3=creation_time
ID_CLIP_INFO_VALUE3=2012-12-27 23:18:48
 encoder: 6.0.1
ID_CLIP_INFO_NAME4=encoder
ID_CLIP_INFO_VALUE4=6.0.1
 encoder-eng: 6.0.1
ID_CLIP_INFO_NAME5=encoder-eng
ID_CLIP_INFO_VALUE5=6.0.1
 date: 2012-12-27T17:18:48-0600
ID_CLIP_INFO_NAME6=date
ID_CLIP_INFO_VALUE6=2012-12-27T17:18:48-0600
 date-eng: 2012-12-27T17:18:48-0600
ID_CLIP_INFO_NAME7=date-eng
ID_CLIP_INFO_VALUE7=2012-12-27T17:18:48-0600
ID_CLIP_INFO_N=8
Load subtitles in ./
ID_FILENAME=IMG_0037.MOV
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=17156808
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=1080
ID_VIDEO_FPS=24.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=62704
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=1
ID_START_TIME=0.00
ID_LENGTH=58.26
ID_SEEKABLE=1
ID_CHAPTERS=0
```

---

### Post by andrew.46 on 2013-03-01
I have not done this for a while but perhaps you could use at least part of the notes I have made on the subject:

```

Create dvd :

Use FFmpeg to create the correct format:
ffmpeg -y -iinput.mkv -target pal-dvd -aspect 16:9 -vol 512 -ac 2 output.mpg

For dvdauthor: Just create a text file $HOME/.config/video_format and write into
this file "PAL" or "NTSC". Then:

dvdauthor -t -o dvd --video=pal -f output.mpg
dvdauthor -T -o dvd

Create the iso:
mkisofs -dvd-video -o output.iso dvd/

Burn to DVD:
growisofs -dvd-compat -Z /dev/sr0=output.iso

```

You would need to use an FFmpeg video filter to rotate your video as well and change the syntax throughout to ntsc. I have never ceated menus etc either I'm afraid...

---

### Post by George Heine on 2013-03-03
Some partial success to report.  I fortunately had a 2-second trial video on the camera to play with.  The orginal (sideways) video had dimensions of 1920x1080.  I rotated this 90 deg counterclockwise with ```
  ffmpeg -i infile.mov -vf "transpose=2" step1.avi
```  The result was a correctly-oriented video of dimensions 1080x1920.  In order to fit this into a 720x480 box as required by the NTSC standard, it was necessary to shrink the height from 1920 to 480.  To keep the aspect ratio, the width needed to be shrunk by the same proportion: 480/1920=0.25;  0.25*1080=270.  ```
ffmpeg -i step1.avi -filter:v scale=270:480 -acodec copy step2.avi
```  Next step (not sure it was necessary) was to center the resulting 270x480 video on a 720x480 plain-color background:```
 convert -size 720x480 xc:brown4 bg.png
ffmpeg -loop 1 -i bg.png -vcodec png -t 2 bg.avi
ffmpeg -i bg.avi -vf "movie=step2.avi [bg]; [in][bg] overlay=(main_w-overlay_w)/2:0 [out]" step3.avi
```.  "Tovid mpg" accepted the resulting 720x480 and created a DVD-compliant image.  The logfile seems to show that tovid called "mplayer -vo yuv4mpeg" with output sent to "mpeg2enc{.

Next steps:  1) analyze the logfile and create something that can be typed at the command line; 2) revise the steps above so that the 720x480 video can be created in the minimum number of passes, with the least degradation in quality (maybe use mkv or some other format rather than avi); 3) make sure that audio is being integrated.  

Any comments would be welcome.  In any case, I intend to keep plugging away at this and plan to send an update when there is something to report.

---

### Post by George Heine on 2013-03-05
More progress.  I was able to combine the video-filtering steps:
```
ffmpeg -i IMG_0037.MOV -i bg.mkv -filter_complex "[0:v] scale=480:270,transpose=2[front]; [1:v][front] overlay=(W-w)/2:0 " -acodec copy tmp.mkv
ffmpeg -i tmp.mkv -target ntsc-dvd out.mpg
``` 
Probably could have combined these two commands, but haven't tried it yet.
Did this with several other videos, then created a minimal dvdauthor xml file:
```
<dvdauthor dest="Test">
<vmgm>
</vmgm>
<titleset>
  <titles>
    <video  format="ntsc" />
    <pgc> <vob file="file2.mpg"  /> </pgc>
    <pgc> <vob file="file3.mpg"  /> </pgc>
    <pgc> <vob file="file4.mpg"  /> </pgc>
  </titles>
</titleset>
</dvdauthor> 

```
Dvdauthor gave plenty of complaints, "audio out of sync, please rerun mplex", but did create a dvd filesystem which I was able to burn (again, with errors) but the result was a working, playable DVD.  The audio and video were indeed out of sync, guess the next step is to try and fix that.

---

### Post by George Heine on 2013-03-06
With  Andrew's suggestions (thanks, Andrew) and LOTS of experimentation, the  following was succesful:

```
ffmpeg -i IMG_0039.MOV -i bg.mkv -y -filter_complex "[0:v] crop=in_w/2:in_h,scale=480:540,transpose=2[front]; [1:v][front] overlay=(W-w)/2:0, setdar=16/9 " -acodec copy  -target ntsc-dvd tmp.mpg

# Run dvdauthor, writing to a logfile in case something goes wrong
dvdauthor -o Test/ -t tmp.mpg 2>&1|tee  log2.txt 

# repeat above with several different videos; then
dvdauthor -T -o Test/
genisoimage -dvd-video -o Test.iso Test/
growisofs -dvd-compat -Z /dev/sr1=Test.iso

```

Some notes:  
- the static background bk.mkv must be at least as long as the video overlaying it, otherwise the result will be truncated
- the numbers in the "scale" command need to be manually computed.  In this case, the original video was 1920x1080;  which became 960x1080 after cropping.  We want to scale to
fit within a 480x720 box, which becomes 720x480 after rotation.  The width is scaled to 480=960/2, the height is scaled by the same proportion (1080/2=540) to preserve the aspect ratio.
- "setdar=16/9" needed to be included to eliminate voluminous warnings from dvdauthor about "Can't determine aspect ratio".  Including this seemed to also eliminate all the warnings about video and audio being out of sync.  
-The resulting video is very basic.  Each of the videos will be written to disc as a separate "title", and there are no menus.  Play stops at the end of each title (at least on my dvd player), and you need to hit the ">>|" button to see the next title.   For more complicated discs, I believe the xml file will be required.

But anyway, have met my original goal, to author a disc entirely from the command line without the use of tovid.  Am marking this thread "solved",

---

### Post by andrew.46 on 2013-03-07
Good news :). Hard work but once it is done you have code snippets to use by hand or incorporate into a script...

---

### Post by FakeOutdoorsman on 2013-03-07
The "-acodec copy" is being ignored and is superfluous because you placed it before "-target ntsc-dvd", and  "-target ntsc-dvd" will re-encode the audio to the proper format anyway. I recommend removing "-acodec copy"; not just because it is being ignored, and if it was not copying arbitrary audio streams may result in incompatible, non-standard outputs for DVD.

---

### Post by George Heine on 2013-03-09
> The "-acodec copy" is being ignored and is superfluous because you  placed it before "-target ntsc-dvd", and  "-target ntsc-dvd" will  re-encode the audio to the proper format anyway. I recommend removing  "-acodec copy"; not just because it is being ignored, and if it was not  copying arbitrary audio streams may result in incompatible, non-standard  outputs for DVD.
Thanks for the tip.  Tried this out and can verify that, as you say, audio is re-encoded properly without the "-acodec copy".

---

