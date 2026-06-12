---
title: "is it possible to batch convert .WAV files to .OGG using gst-launch"
date: 2009-08-27
forum: Multimedia Software
---

### Post by grumpthehermit on 2009-08-27
Hello,

I have searched the forums and can't find an answer so I thought I would ask the question.

I can use the following in terminal to convert a single file from .WAV to .OGG

gst-launch filesrc location=music.wav ! wavparse ! audioconvert ! vorbisenc name=enc quality=1.0 ! oggmux ! filesink location=music.ogg

Where "music".wav is changed to the name if the file I wish to convert to .ogg

Is it possible to batch convert a list of files in the same folder without having to re-execute the same command with the next file name over and over ?

I was thinking there might be a file name wildcard or something ?

The reason I am using gst-launch is because Rhythmbox has locked up on a few of my Cd's so I have used cdparanoia to rip these few discs to .wav and now want .ogg's

Thanks, Any thoughts would be apprieciated.

Grumpthehermit  :)

---

### Post by mc4man on 2009-08-27
make sure you have vorbis-tools installed, then simply cd to the folder containing the .wav's and 
```
oggenc -q [COLOR="Blue"]10[/COLOR] *.wav
```

The blue is the quality setting, ranges from 1-10, (1 being lowest q

---

### Post by grumpthehermit on 2009-08-28
That worked a treat, thanks so much for your help.

Grumpthehermit :)

---

