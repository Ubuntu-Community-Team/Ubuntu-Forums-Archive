---
title: "Is it possible to extract the sound from a video and save it as a .mp3?"
date: 2009-02-14
forum: Multimedia Software
---

### Post by RobinReborn on 2009-02-14
Ideally in a simple manner but I am willing to put in some work if anybody has any ideas.

---

### Post by lswb on 2009-02-15
ffmpeg and mplayer can both do this. The command line options may vary depending on the type of source file. For instance to extract an mp3 from a flash video named source.flv to a file named music.mp3,

mplayer -dumpaudio source.flv -dumpfile music.mp3

For .wmv, .wma or other source files you may need additional packages installed, lame comes to mind for converting .wma audio to mp3 for instance.

I don't know the complete command line for extraction/conversion of audio from every type of source file; that can be determined from the man pages or a google search, but most anything that can be played or viewed can certainly have the audio extracted and converted or saved as an mp3.

---

### Post by prshah on 2009-02-15
> **RobinReborn said:**
> Ideally in a simple manner but I am willing to put in some work if anybody has any ideas.

You can do this very easily with ffmpeg, approximately```
ffmpeg -vn -i inputfile.avi soundfile.mp3
```

"-vn" indicates ffmpeg should nullify video output, and audio will be automatically converted to mp3 based on the extention of the output filename.

You can also use (as suggested) mplayer or, if you like a GUI interface, you can use avidemux. All software suggested here are in the repos.

---

### Post by icp on 2009-02-15
I use "Avidemux" to edit Audio/Video tracks.

---

