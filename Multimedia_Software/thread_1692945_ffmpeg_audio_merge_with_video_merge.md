---
title: "ffmpeg audio merge with video merge"
date: 2011-02-22
forum: Multimedia Software
---

### Post by kuldeep.kamboj on 2011-02-22
Hi all,

I am using ffmpeg for merge wav files to a mov video. My doing is below

1. First extract audio (wav file) from video
2. Create wav file from mp3 track 1
3. Create wav file from mp3 track 2
4  Merge extract audio from video with track 1 and track2.
Now finally create a new video with original video's video stream and merged audio stream.

Process is working. However final video is 3-4 times greater than original one. I want that final video should be near about size of original video. As I understand, all three wav files (created from ) make video larger. 

Example commands i using is as below 


----------
<< Video Audio >>
ffmpeg -i /original/test.mov -t 00:00:56 -ss 00:00:00 -ar 44100 -ac 2 /tmp/videoAudio.wav


----------
<< Track1 Audio >>
sox -r 44100 -c 2  songs/track1.mp3 /tmp/track1.wav  trim 0 54


----------
<< Track2 Audio >>
sox -r 44100 -c 2  songs/track1.mp3 /tmp/track2.wav  trim 0 74


----------
<< Combine Tracks >>
sox --combine concatenate /_tmp/track1.wav /tmp/track2.wav /_tmp/videoAudio.wav /tmp/combineAudio.wav


----------
<< Final Video >>
ffmpeg -i /tmp/combineAudio.ogg -i /original/test.mov -acodec copy -vcodec copy /tmp/test.mov



Any body have optimize solution for this?

---

### Post by aeiah on 2011-02-22
are you muxing wav audio into the ogg container at the end?

you seem to be producing a .wav audio mix but your final statement takes .ogg audio as input. but anyway, if the audio you're muxing in at the end is larger than the audio you extracted at step 1, then the filesize is bound to be larger.

---

### Post by ron999 on 2011-02-22
.......

---

### Post by kuldeep.kamboj on 2011-02-22
Hi aeiah,

Sorry for wrong last line. 

Read last line  like that 
ffmpeg -i /tmp/combineAudio.ogg -i /original/test.mov -acodec copy -vcodec copy /tmp/test.mov

Actually i tried with ogg formats for less size also but faced many setbacks.

---

### Post by kuldeep.kamboj on 2011-02-22
I am resubmitting my code sample as

----------
<< Video Audio >>
ffmpeg -i /original/test.mov -t 00:00:56 -ss 00:00:00 -ar 44100 -ac 2 /tmp/videoAudio.wav


----------
<< Track1 Audio >>
sox -r 44100 -c 2  songs/track1.mp3 /tmp/track1.wav  trim 0 54


----------
<< Track2 Audio >>
sox -r 44100 -c 2  songs/track1.mp3 /tmp/track2.wav  trim 0 74


----------
<< Combine Tracks >>
sox --combine concatenate /tmp/track1.wav /tmp/track2.wav /tmp/videoAudio.wav /tmp/combineAudio.wav


----------
<< Final Video >>
ffmpeg -i /tmp/combineAudio.ogg -i /original/test.mov -acodec copy -vcodec copy /tmp/test.mov

---

### Post by aeiah on 2011-02-22
just convert the audio into a more compressed format than .wav before muxing it into the video (or convert as you put it in). might as well go for mp3 unless there's a reason not to.

---

### Post by kuldeep.kamboj on 2011-02-22
One more time same error ;)

----------
<< Video Audio >>
ffmpeg -i /original/test.mov -t 00:00:56 -ss 00:00:00 -ar 44100 -ac 2 /tmp/videoAudio.wav


----------
<< Track1 Audio >>
sox -r 44100 -c 2  songs/track1.mp3 /tmp/track1.wav  trim 0 54


----------
<< Track2 Audio >>
sox -r 44100 -c 2  songs/track1.mp3 /tmp/track2.wav  trim 0 74


----------
<< Combine Tracks >>
sox --combine concatenate /tmp/track1.wav /tmp/track2.wav /tmp/videoAudio.wav /tmp/combineAudio.wav


----------
<< Final Video >>
ffmpeg -i /tmp/combineAudio.wav -i /original/test.mov -acodec copy -vcodec copy /tmp/test.mov

---

