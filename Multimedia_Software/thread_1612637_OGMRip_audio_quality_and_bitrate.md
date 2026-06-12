---
title: "OGMRip audio quality and bitrate"
date: 2010-11-03
forum: Multimedia Software
---

### Post by sammy07 on 2010-11-03
Hello folks,

here is a simple question, which prevents me from using OGMRip:
how does the audio quality setting 0-10 (set in the OGMRip profile) correspond to the bitrate?? 
Its default value is 3, whatever it means. Its not documented, nowhere (at least, I found nothing). 
Yeah I know, there is handbrake; thats not the question and also not the solution. I can also set the quality to 10, but I dont want to spend more place than necessary for the sound track.
Its really simple: I want OMGRip with AAC coding with either 128 or 160 kbps. How do I do this?

Thanx in advance!

---

### Post by meyierman on 2011-12-25
In the log file you can find the exact command options for the various tools that ogmrip uses. With the default audio quality setting of 3 I see this audio encoding command in the log file:

faac -P -R 48000 -C 2 -X -q 157 --mpeg-vers 4 -o /tmp/audio.6TH36V /tmp/fifo.5KH36V

i.e.: quality 3 means a bitrate of 157.

---

