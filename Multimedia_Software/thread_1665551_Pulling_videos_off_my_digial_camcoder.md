---
title: "Pulling videos off my digial camcoder?"
date: 2011-01-12
forum: Multimedia Software
---

### Post by HDave on 2011-01-12
I have a brand spanking new Samsung HMX-H200 digital video camera.  

Anyone have the slightest idea how to get the videos off this thing onto Ubuntu 10.04?

---

### Post by HDave on 2011-01-12
OK, I figured out that I can put the SD card in a card reader and pull off all of the MP4 video files.

The MP4 playback is jittery and I need to concatenate these together...but those are different problems...

---

### Post by wkulecz on 2011-01-12
See this thread about poor mp4 playback of camcorder videos:

[http://ubuntuforums.org/showthread.php?t=1302249](http://ubuntuforums.org/showthread.php?t=1302249)

---

### Post by no2498 on 2011-01-12
installing smplayer has helped me with mp4 files
type it in a terminal it tells you how to install it

---

### Post by HDave on 2011-01-12
> **no2498 said:**
> installing smplayer has helped me with mp4 files
type it in a terminal it tells you how to install it

smplayer is cool...but no joy.  I get perfect audio, but almost no video...just the first couple frames and then video freezes.

---

### Post by BicyclerBoy on 2011-01-12
The linked post does not really explain the problem at all. Neither do I.

It could be because the file type is transport stream.
Did VLC play it any better ?

You could use ffmpeg to demux & remux with timestamps.

ffmpeg -i video-in.mp4 -vcodec copy -acodec copy -copyts video-out.mpg

May need to fiddle with stream order with some arrangement of -map 0:0 -map 0:1

So post the result of ffmpeg command stdout with stream info.
Only if you are interested tho'.
I'm just curious but do not have the files.

Can use ffmpeg to join videos together using -newvideo -newaudio.

---

### Post by HDave on 2011-01-12
To summarize the situation at this point:

totem:    Lots of stuttering
vlc:      Jittery, some stuttering
mplayer:  Smooth, but video quality is low and sound is off...probably from not dropping frames
miro:     One frame about every 5 seconds
smplayer: Video freezes after first couple frames

---

### Post by HDave on 2011-01-12
> **BicyclerBoy said:**
> You could use ffmpeg to demux & remux with timestamps.

ffmpeg -i video-in.mp4 -vcodec copy -acodec copy -copyts video-out.mpg


When I do this, I get the following error:

```
error, non monotone timestamps 9009 >= 3003
```

Any ideas?

---

### Post by BicyclerBoy on 2011-01-13
Can you please post ALL the ffmpeg output messages ?
So can see version & stream info

Also try it without the -copyts..

This has been solved/worked around in the past by re-encoding the audio

Try replacing the "-acodec copy"
"-acodec mp2 -ab 128k -ac 2"

&/or try "-vsync 2"..

---

