---
title: "Muxing an MP4 with dual (AAC and AC3) audio."
date: 2008-12-10
forum: Multimedia Software
---

### Post by sexyclient on 2008-12-10
I'm trying to mux a video file with two audio files (AAC and AC3) into an MP4 container, but I don't know if this is possible (on linux).  

I checked mp4creator, but the version that comes with Hardy (what I'm using on this machine) doesn't let you mux an AC3 audio file.  The mp4creater on sourceforge.net, however, will allow this and even has a gui - but it's a windows-only affair...  To make matters worse, the file isn't WINE-compatible (at least the GUI mp4muxer isn't, I'll try the command line mp4creator next, but using wine for a command-line windows app isn't very appealing).

Is there any Ubuntu/Linux option for ac3 and aac muxing into the MP4 container?

---

### Post by darious on 2008-12-19
I'm looking for a simliar solution. (Ubuntu 8.10 Intrepid amd64)

I'd like to recode h.264 & AC3 MKVs to h.264, AAC & AC3 mp4s for use with an apple tv.

I've figured out the majority of the workflow,

1. Extract the raw streams from the mkv using mkvextract
2. Recode the streams (video and AC3 to AAC) using ffmpeg
3. Remux recoded video and AAC audio with the orginal AC3 into an mp4

This final step is the problem. FFMPEG won't/can't do it. The versions of MP4Creator in the repository is too old to do it as it the version of MP4Box (in GPAC).

I've tried downloading and building these from source (as I did with x264 and ffmpeg) but I've run into a number of issues (can't detail now, I'm supposed to be working).

I'm going back to trying to figure it out tonight, if I manage to get it all working, I'll hook up a shell script to automate the process and post the details here.

---

