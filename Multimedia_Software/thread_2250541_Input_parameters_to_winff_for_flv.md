---
title: "Input parameters to winff for flv"
date: 2014-10-29
forum: Multimedia Software
---

### Post by ski-brimson on 2014-10-29
[FONT=arial]I am trying to convert a 1080i video to flv from a camera that uses the AVCHD format.  The error is that flv does not support that sample rate, choose from (44100, 22050, 11025), but I have chosen 44100.  I want to keep the screen resolution the same.
[/FONT]
[FONT=arial]Here are the commands it says it will use (I want two pass):[/FONT]
[INDENT][FONT=lucida console]usr/bin/avconv -i "/home/klugja/Videos/00022.MTS" -vcodec flv  -f null -r:v 59.94 -filter:v scale=1920:1080,yadif  -aspect 16:9 -b:v 16594k -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1  -ac 2 -r:a 44100 -b:a 16594k -b:v 16594k -b:a 16594k  -an -passlogfile "/home/klugja/00022.log" -pass 1  -y /dev/null

/usr/bin/avconv -y -i "/home/klugja/Videos/00022.MTS" -vcodec flv -f flv   -r:v 59.94 -filter:v scale=1920:1080,yadif  -aspect 16:9 -b:v 16594k -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1  -ac 2 -r:a 44100 -b:a 16594k -b:v 16594k -b:a 16594k  -passlogfile "/home/klugja/00022.log" -pass 2  "/home/klugja/00022.flv"[/FONT]
[/INDENT]
[FONT=arial]
It clearly says 44100.[/FONT][INDENT][FONT=lucida console]
Here is some output:
Input #0, mpegts, from '/home/klugja/Videos/00022.MTS':
  Duration: 00:02:53.72, start: 0.855522, bitrate: 16594 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.94 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, stereo, fltp, 192 kb/s
    Stream #0.2[0x1200]: Subtitle: pgssub
[h264 @ 0x1319300] Ignoring NAL unit 9 during extradata parsing
Output #0, null, to '/dev/null':
  Metadata:
    encoder         : Lavf54.20.4
    Stream #0.0: Video: flv (hq), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=2-31, pass 1, 16594 kb/s, 90k tbn, 59.94 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> flv)
Press ctrl-c to stop encoding
[h264 @ 0x1323f80] Ignoring NAL unit 9 during extradata parsing
frame=10411 fps= 13 q=2.0 Lsize=       0kB time=173.72 bitrate=   0.0kbits/s    
video:349994kB audio:0kB global headers:0kB muxing overhead -100.000000%
avconv version 9.16-6:9.16-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Aug 10 2014 18:16:02 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)

...
Input #0, mpegts, from '/home/klugja/Videos/00022.MTS':
  Duration: 00:02:53.72, start: 0.855522, bitrate: 16594 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.94 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, stereo, fltp, 192 kb/s
    Stream #0.2[0x1200]: Subtitle: pgssub
[flv @ 0x69dd80] [lavc rc] Using all of requested bitrate is not necessary for this video with these parameters.
[h264 @ 0x693c60] Ignoring NAL unit 9 during extradata parsing
[flv @ 0x69d840] flv does not support that sample rate, choose from (44100, 22050, 11025).
[/FONT][/INDENT]
[FONT=lucida console]
[FONT=arial]Is there an easier tool for doing this?  What parameters would I use?[/FONT]
[/FONT]

---

### Post by andrew.46 on 2014-11-04
It might be a little easier to use avconv or FFmpeg directly. Is there a special reason that you need flv? I ask mostly because the flv container will hold a reasonably wide range of video and audio codecs these days so you are not limited to the codecs that WinFF specifies...

---

### Post by ski-brimson on 2014-11-08
I am trying to create a video that plays reasonably well on Citrix, which I believe runs over flash, and they claim to have flash optimization.  Maybe that has nothing to do with flv?  The original MTS (AVCHD) does not play well over Citrix.  The typical 1080 vertical resolution youtube video works just fine (though I know they are not always flash these days).

---

### Post by andrew.46 on 2014-11-08
My knowledge of citrix and media playback would be pretty much zero I am afraid! Perhaps if you modify the original file a little there may be better playback, it is a huge file in terms of kbs. So for an experiment first make sure you have the extra codecs:

```

sudo apt-get install avconv libavcodec-extra-54

```

and then try to skinny the file a little, lose the ac3 and pack it all into an flv container:

```

avconv -i $HOME/Videos/00022.MTS \
        -c:v libx264 -preset slow -crf 22 \
        -c:a libmp3lame -q:a 4 -ar 44100 \
        $HOME/Videos/test.flv

```

An alternative is to simply copy the video stream. I am a little uncertain about the flv container as I would normally use an mp4 container, but if citrix uses this container best I will have to take your word for that. Other codecs can be used in this container so some experimentation may be ahead for you...

---

