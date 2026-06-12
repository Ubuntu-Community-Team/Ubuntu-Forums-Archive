---
title: "[SOLVED] MiniDV problem: is there a way to rip only audio?"
date: 2023-12-25
forum: Multimedia Software
---

### Post by caesar753 on 2023-12-25
Hi, 
I'm trying to transfer my old miniDV cassettes to my PC however I'm encountering audio issue on some of them: in particular the audio is crackling and out of sync from video. Is there a way to rip only audio without video? I tried dvgrab and kino but you can only change the output format (raw, avi type 1, type 2, quicktime) but not get the audio only...

---

### Post by #&amp;thj^% on 2023-12-25
Did you try with FFmpeg?
 ffmpeg (command line). Example:
```

ffmpeg -i infile.wmv -vn -acodec copy outfile.wma
```

Or, if you want an MP3 file:
```

ffmpeg -i infile.avi -vn -ar 44100 -ac 2 -ab 192 -f mp3 outfile.mp3
```
I know some cables are much better suited for "miniDV" Firewire has four pins.

---

### Post by caesar753 on 2023-12-25
but in this case i should yet have the audio/video file (with bad and out of sync audio), i'd like to grab directly from the camera only the audio during the transfer process...

---

### Post by #&amp;thj^% on 2023-12-25
I get that  (with bad and out of sync audio) the ffmpeg can still handle that.(Sourced from the camera)
Is any of the Audio any good?
camcorders use FireWire to communicate with the computer, so you will need a suitable cable.
I pulled my hair completely out when I first attempted to transfer my home videos over.
This was the key>>>The cable you will need is therefore an IEEE 1394 cable. But since there are some with several different pinouts and a different number of pins, you will need an IEEE1394 S400 cable, with a 4-pins end on the camcorder side, and 6-pins end on PC side.

---

### Post by caesar753 on 2023-12-25
I have an IEEE1394 S400 cable both side because I'm connecting it to my (old) laptop and it has this kind of (mini)firewire port.
But with ffmpeg you can catch the stream directly from the camera? My problem is that the audio is very very fast and it is in some way compressed in the first few seconds/minutes and all the remaining video is without audio...

---

### Post by caesar753 on 2023-12-25
I think that one of the problems is that during the acquisition for some reason the video cannot be synchronised with audio, if I can grab audio and video separately I can then merge them with another software (e.g. Obs studio)

---

### Post by #&amp;thj^% on 2023-12-25
> **caesar753 said:**
> 
But with ffmpeg you can catch the stream directly from the camera? 
That is correct, just the audio. And you may have to play around with speed, but I did not have to.

---

### Post by #&amp;thj^% on 2023-12-26
@  caesar753 there is a GUI for Ffmpeg as well if it easier or more convenient "qwinff"
I forgot about that one I don't use many GUI's

---

### Post by mocha on 2024-01-06
You are using Firewire to capture the tapes to the desktop, correct?

Something like this should work (not tested by me):
```

$ dvgrab -frames 0 -size 0 -format raw -showstatus - | ffmpeg -i - -c:v none -c:a aac -q:a 6 -preset medium -threads 0 OUTPUT.AAC

```

I can't remember if the -c:v none part of the command is correct.  The deprecated command switch was -vn which may still work.

---

### Post by caesar753 on 2024-01-06
Thanks a lot! I'll try

---

### Post by caesar753 on 2024-01-18
It worked! thanks again!

---

