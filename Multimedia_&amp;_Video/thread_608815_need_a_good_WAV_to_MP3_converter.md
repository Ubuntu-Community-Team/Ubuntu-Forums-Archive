---
title: "need a good WAV to MP3 converter"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by t2000kw on 2007-11-10
I have tried SoundConverter and SoundKonverter to convert a WAV file to MP3. The latter program crashes and disappears. The former one converts part of the WAV file, anywhere from 6 seconds to a minute and a half (out of 5 or so minutes) and stops there. What is created is playable but not the whole file. It does the same when converting to OGG format. 

Can anyone recommend a converter for Ubuntu that actually works and doesn't do part of the job or fail to work altogether?

I would prefer to not have to compile the program but will consider it if there are no other reliable alternatives.

---

### Post by disturbedite on 2007-11-10
soundkonverter is the best imo.  but, just like with other programs, you must have the proper codecs installed.  did/do you?

---

### Post by tubasoldier on 2007-11-10
You can use the command line to convert them all to MP3. 
```
lame {options} input.wav output.mp3
```

type lame --help for a simple list of options
type lame --longhelp for a detailed list of options

for instance if you want to convert an entire folder of wav files to mp3 then it would be something like:
lame -b 256 -brief *.wav *

Someone should verify this. or copy the files to a new folder and try it out before you commit it to your original files.

---

### Post by Keith Hedger on 2007-11-10
Been converting some youtube vids and extracting the mp3's with this:
lame -m j -h -b 128 --resample 48 inputfile.wav  outputfile.mp3
It gives pretty good results

---

### Post by t2000kw on 2007-11-10
> **disturbedite said:**
> soundkonverter is the best imo.  but, just like with other programs, you must have the proper codecs installed.  did/do you?

I installed every codec imaginable. At least, every one I could find.

---

### Post by t2000kw on 2007-11-10
> **tubasoldier said:**
> You can use the command line to convert them all to MP3. 
```
lame {options} input.wav output.mp3
```
.


I tried lame name-of-wave-file.wav name-of-output-file.mp3 and got an MP3 file full of static, no useful information. 

Here's the output of the terminal window in case there's somethign I needed to do that I didn't. There appears to be an error but it didn't abort the process. The warning message surprises me as I can play the wav file through its entirety with no problems at all. Maybe I need a program to capture its output at the sound card? Is there such a thing for Linux?

donald@donald:~/Music/test$ lame pope2.wav Michangelo.mp3
Warning: corrupt or unsupported WAVE format
Assuming raw pcm input file
LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE
Using polyphase lowpass filter, transition band: 16538 Hz - 17071 Hz
Encoding pope2.wav to Michangelo.mp3
Encoding as 44.1 kHz 128 kbps j-stereo MPEG-1 Layer III (11x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
   122/122   (100%)|    0:00/    0:00|    0:00/    0:00|   14.486x|    0:00 
-------------------------------------------------------------------------------
   kbps        MS  %     long switch short %
  128.0      100.0        97.5   1.6   0.8
Writing LAME Tag...done
ReplayGain: -11.1dB
donald@donald:~/Music/test$

---

### Post by t2000kw on 2007-11-10
I found the problem!

I had downloaded this wav file a long time ago. Apparently, it's really a layer 3 MPEG file. I did a simple rename to mp3 form wav and it still plays, so it should now be able to be put on an audio CD.

---

