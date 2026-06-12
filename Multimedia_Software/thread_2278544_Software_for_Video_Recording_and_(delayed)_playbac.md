---
title: "Software for Video Recording and (delayed) playback"
date: 2015-05-17
forum: Multimedia Software
---

### Post by daniel-herrmann1 on 2015-05-17
Hi,

I am looking for a specific recording / capture software. I have an external device (or a USB webcam, depends on situation), which are connected to my laptop running Ubuntu 14.10.

Playback is possible with VLC without problems. I am looking for a solution to perform the following tasks:

- Delayed Live TV of the Input (3-10s delay)
- Buffer at least the last 30 minutes, older material may be deleted
- Possibility to go back and watch scenes again
- Ideally, watching frame by frame

Can you recommend such a software?

Thank you in advance

---

### Post by TheFu on 2015-05-17
Recording video and recording TV are very different things. TV inputs require a tuner connected to an antenna, CATV, satellite, (or something else) and the needed tuner is highly locality dependent - recording TV in the USA is different than recording TV in South America or Europe or Asia ... for example. We all have different inputs, different drivers for the tuner devices, and many do not work in Linux. HiDef vs Std-Def and analog vs digital - each matter.

Recording from a webcam generally doesn't have anything to do with playback. The playback solution is normally separate. I've never seen them be the same process, even if they are the same program (like VLC can both record AND playback). The key for playback is the codecs used for  video and audio must create the header at the start of the recording. Highly compressed versions of mkv and/or mp4 do not do that.

Sounds like you want a TiVo, but there isn't any mention of audio - do you care about audio?

So - if you post back which TV standards are used and which video codecs are required, hopefully someone will be able to provide options.

---

### Post by daniel-herrmann1 on 2015-05-17
Hi TheFu, thank you for your answer.

First: audio does not matter at all.

We either use a camera and an external grabber ([example]("http://www.amazon.com/TOTMC%C2%AE-Video-Capture-Adapter-Windows/dp/B00M7T8T1E/ref=sr_1_3?ie=UTF8&qid=1431886758&sr=8-3&keywords=video+grabber")) or a webcam directly attached via USB to record a sports event. Due to the analog recording, HiDef is not important. As mentioned before, I actually also do not care about persistent storage. We only need to be able to go back a certain time (for example 30 minutes), to review scenes for referees. We have no special requirements regarding codes. As we are located in Europe, PAL is used.

Hope this helps, If any further information are required, I will by happy to provide.

---

### Post by TheFu on 2015-05-17
> **daniel-herrmann1 said:**
> Hi TheFu, thank you for your answer.

First: audio does not matter at all.

We either use a camera and an external grabber ([example]("http://www.amazon.com/TOTMC%C2%AE-Video-Capture-Adapter-Windows/dp/B00M7T8T1E/ref=sr_1_3?ie=UTF8&qid=1431886758&sr=8-3&keywords=video+grabber")) or a webcam directly attached via USB to record a sports event. Due to the analog recording, HiDef is not important. As mentioned before, I actually also do not care about persistent storage. We only need to be able to go back a certain time (for example 30 minutes), to review scenes for referees. We have no special requirements regarding codes. As we are located in Europe, PAL is used.

Hope this helps, If any further information are required, I will by happy to provide.

That is extremely helpful and gets me out of "recording TV" thoughts.

I do not have any direct solution, but is there a reason you wouldn't just record the entire event? Begin with hidef capabilities now, since for reviewing calls, the higher resolution really can matter.  I record stuff all the time, but generally keep the entire recording until it is watched and not needed any longer. For the 30 rolling capture, you are forced into a codec that doesn't require headers.  I think that means mpeg2 TS or PS. 3hrs of hidef recording will be less than 50G and easily fit onto a cheap SSD with the OS.  For webcam recording, I use ....  **guvcview**. It is nice and works.
[http://wiki.oz9aec.net/index.php/Gstreamer_cheat_sheet#Webcam_Capture](http://wiki.oz9aec.net/index.php/Gstreamer_cheat_sheet#Webcam_Capture)
[http://www.oz9aec.net/index.php/gstreamer/345-a-weekend-with-gstreamer](http://www.oz9aec.net/index.php/gstreamer/345-a-weekend-with-gstreamer)

Perhaps getting a used TiVo and hooking up the input from the video source might work? If it is on, it is recording video whenever a channel seems to be tuned.

I'm really just brainstorming now. Don't know of a specific "tivo like" solution.

Someone else asked a similar question here: [https://superuser.com/questions/907467/how-to-record-video-into-circular-buffer](https://superuser.com/questions/907467/how-to-record-video-into-circular-buffer) No answers.

If you can accept a 1-2 sec drop every 30 min, you could have a small script capture the webcam output into a file for 30 min, stop, restart capture and rotate through perhaps 3-4 of these files.  gstreamer, xvidcap, and other tools like that are easily automated for the recording part.  Provided the output video file is a format that allows concurrent playback while the recording is still being written, I think this is a viable option.  I'm curious myself - let me see if I can build a script like this in the next hr or 2.  I'll be using a logitech c920 webcam and bash scripting.

Interesting problem.

Update: Some Proof of Concept code
```
#!/bin/bash

WEBCAM=/dev/video0
OUTBASE=./capture
RES="1280×720"
FPS=30
KILL_TIME=5
CNT=5

while [ $CNT -gt 0 ] ; do

   # #########################################
   # Capture the webcam video, put in background
   /usr/bin/avconv -f video4linux2 -s hd1080 -r $FPS -b 1150k \
          -i $WEBCAM -acodec aac -vcodec mpeg4 \
          "$OUTBASE-$CNT.mp4" &
   # Save the PID
   PID=$!

   # Delay some time min, then kill avconv
   sleep $KILL_TIME
   kill $PID
   CNT=$((CNT-1))

done

```

---

