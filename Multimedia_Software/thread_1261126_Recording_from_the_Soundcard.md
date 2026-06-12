---
title: "Recording from the Soundcard"
date: 2009-09-08
forum: Multimedia Software
---

### Post by chome4 on 2009-09-08
How can I record directly from my soundcard? Can't get Audacity to work! What other types of software are out there?

---

### Post by ron999 on 2009-09-08
Hi
I followed this guide here:-
[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")
I wasn't able to encode to mp3 in real-time, maybe my PC isn't up to it.
But I could record to a wav file then encode later.
When it's set up right all that's needed is the instruction
```
arecord -f cd output.wav
```

---

### Post by chome4 on 2009-09-08
When I type:

arecord -f cd output.wav

I see:
Recording WAVE 'output.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

But I can't find the wav file.

Where does it save the file to?

---

### Post by ron999 on 2009-09-08
It saves it here:-
**/home/ron/output.wav**

---

### Post by chome4 on 2009-09-08
When I'm in Alsamixer, I can't get 'capture' to show up.

I've got a file called 'output.wav' but it plays silent. It has a size of several megabytes so it did record but produces no sound.

---

### Post by ron999 on 2009-09-08
Use tab key (next to Q)to toggle between Playback, Capture, All.

---

### Post by chome4 on 2009-09-08
Works OK now. Distorted but I can adjust levels to get things right!

Thank you very much.

---

### Post by ron999 on 2009-09-08
> **chome4 said:**
> Works OK now.
Good.
Maybe you will have success with mp3.
When I tried it said 'Buffer overrun'. When I listened it hiccupped. I think that my PC couldn't keep up.
Experiment.
:guitar: :-({|=:lolflag::shock: :cool:
Edit
There's also a typo in the article.
He says:-
> arecord -f cd -t raw | lame -x -r &#8211; out.mp3
But it should be:-
> arecord -f cd -t raw | lame -x -r - out.mp3
(There's a minus sign, not a dash)

---

### Post by markbuntu on 2009-09-09
You can also do it this way which will get your sound set up optimized as a bonus;

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by SuperMike on 2009-11-07
What happens if all I get are a series of clicks?

---

