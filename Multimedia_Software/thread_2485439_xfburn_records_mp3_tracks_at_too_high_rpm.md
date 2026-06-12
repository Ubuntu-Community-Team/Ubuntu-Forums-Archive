---
title: "xfburn records mp3 tracks at too high rpm"
date: 2023-03-29
forum: Multimedia Software
---

### Post by him610 on 2023-03-29
Xubuntu 22.04.2

Normally, I use a USB device to transfer files from computer to player, but we have a couple of near-vintage vehicles that do not accept USB devices, only CD audio discs. We want to play home-recorded MP3 compilation CDs in our vehicle players; however, every audio CD on which I have attempted to record MP3 files come out having been recorded at a higher rpm than normal using xfburn. You know, like Alvin and the Chipmunks.
This is the first time I have encountered this issue. The last time I created an audio CD a couple of years ago, the CDs came out playable. This occurs on two different computers, both with Xubuntu 22.04.2.

Purchased audio CDs and locally stored mp3 files play just fine using Parole Media Player. 
I have searched the Multimedia forum for similar issues with no success. 
Does anyone what is going on here?

---

### Post by #&amp;thj^% on 2023-03-29
What wrilte speed are you using, for Audio files I'll use a lower write speed, (4x)
All USB drives I've used on 22.04 have worked as expected. I don't own any writable CD's (sorry)
EDIT:
```
 xfburn -V
Gtk-Message: 13:35:12.632: Failed to load module "xapp-gtk3-module"
xfburn version 0.6.2 for Xfce 4.18
	built with GTK+-3.24.32, linked with GTK+-3.24.33.
	GStreamer support (built with 1.20.0, linked against 1.20.3)

```
The below will spew a lot of info so best post that to a pastebin.
```
GST_DEBUG=4 xfburn
```

---

### Post by him610 on 2023-03-29
Thanks for the suggestions 1fallen,

Well, I have not been able to get xfburn to successfully burn an audio cd; however, I was able to come up with a workaround. I downloaded brasero, another disc burning application. It took a little extra download because when I selected brasero in synaptic, all of its necessary parts were not recommended for installation. 
The reason that I had been using xfburn the last several years (maybe 10) is because I could not successfully burn discs using brasero.

I will close this out. Even though, I was able to come up with an alternative way to produce an audible cd; The original issue with xfburn is still there. I will work with it a while longer; if I can not be successful with xfburn, I will submit a discrepancy report.

---

### Post by scdbackup on 2023-04-02
Hi,  whatever goes wrong with Xfburn, it is not the recording speed. Audio CDs are a digital medium, after all. The replay speed is defined by the data.  What you report looks like a problem with the conversion of your input files to the uncompressed audio format which is prescribed for CD-DA. The specification for the uncompressed file format is: ```
 headerless PCM (i.e. uncompressed), 44100 Hz sampling rate, 16 bits per sample, stereo (2 channels), big-endian byte order 
``` Typically you find this in files with ending .wav, which have little-endian byte order and will get byte swapped by the burn backend (libburn) on  request of the user or the burn frontend (Xfburn).  I bet on the sampling rate being too low. Both Xfburn and Brasero employ external programs to convert formats like .mp3 to the uncompressed PCM. Brasero seems to make the right choice of program and its options, with Xfburn there seems to be a mistake.  I see in the 16 year old README of cdrskin proposals to do this as human. E.g. for MP3: ```
 lame --decode -t /path/to/track3.mp3 track03.cd 
``` (It's called .cd and not .wav, because the WAVE header is omitted here.)  So you could try to find out what Brasero uses for the conversion of your files and then convert them yourself before giving them to Xfburn. Hopefully Xfburn will recognize that no conversion is needed.  Have a nice day :)  Thomas

---

