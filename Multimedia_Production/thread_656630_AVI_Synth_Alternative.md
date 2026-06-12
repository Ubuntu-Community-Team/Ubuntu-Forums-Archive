---
title: "AVI Synth Alternative"
date: 2008-01-02
forum: Multimedia Production
---

### Post by mailbox on 2008-01-02
I'm looking for a Linux alternative for AVI Synth. I have two Law and Order episodes a friend gave me, but there's a lot of popping and hissing in the audio tracks. There's a textfile that came with the episodes telling me about the two included .avs files and how I can use them to correct the audio with AVI Synth, although it appears the corrections are made in real-time, so wine won't really work with MPlayer, as far as I know. I'm looking for some way to make the audio fixes permanent. I can extract the audio from the video and edit it seaperately in some program, that's no problem, I just don't know what program to use.

Thanks in advance.

---

### Post by eye208 on 2008-01-03
Audacity has some functions to de-noise audio. You can use them on the extracted stream, then replace the audio stream of the video file using MEncoder or some other tool.

---

### Post by Creative2 on 2008-01-03
if you want syncronize audio video you can do with this 

mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT

(Fuoco tools interface or ConvertIT)

---

### Post by mailbox on 2008-01-03
Ah, thanks for the idea. I'll give that a shot, although I'm not sure how well Audacity will be able to cope.
The reason I wanted something like AVI Synth is that these two files that came in addition to the .avi's are specifically generated to correct each individual audio track.

Creative2: I think you misread something somewhere, but thanks anywho.

---

### Post by theacoustician on 2008-01-04
Who needs an alternative?  [AVISynth 3.0 is available for Linux]("http://avisynth3.unite-video.com/download.html").

If that alpha is a bit too shakey for you, give Avidemux a whirl.

---

### Post by mailbox on 2008-01-05
Oh wow, this is awesome. I don't know how I overlooked this.
Thanks!

---

