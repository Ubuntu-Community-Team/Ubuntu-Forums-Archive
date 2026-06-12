---
title: "Command Line Audio Visualization Tool?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by scottfinman on 2008-06-14
I am looking for a tool that runs from the command line that will allow me to create a graph (PNG, GIF, or JPEG export) of the audio activity contained within an audio file.

The particular application of this is for a radio scanner that monitors local emergency frequencies, and generates 10 minute sound clips all day long of the received signals. What I would like to do is translate each 10 minute sound clip into something more visual, so I can quickly identify times of interest.

Any suggestions?

---

### Post by weskey5644 on 2010-05-03
I agree. Has anyone found anything like this?

---

### Post by Pithikos on 2011-09-29
You could probably use projectM-pulseaudio and glc.
projectM-pulseaudio is just an OpenGL visualisation for songs. I am sure you can just find a preset visualisation that is quite simple or just build your own.
Glc is a capturer for OpenGL.

Both can be installed from the repos:
```
sudo apt-get install projectm-pulseaudio
sudo apt-get install glc

```
Once installed just make sure that the audio goes to pulse audio and start glc:
```
glc-capture -s projectm-pulseaudio
```

A file will appear in the current folder which will scale insanely. Once done you can play it with:
```
glc-play filename
```

You could probably set glc to record in very low frames and no audio and maybe pipe with some other program to send the recorded segment directly to an other program that will keep only some specific frames and save them as jpb or whatever. Hopes it helps!

---

