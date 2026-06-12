---
title: "codec error in VLC"
date: 2010-06-20
forum: Multimedia Software
---

### Post by raymondvillain on 2010-06-20
I am running Ubuntu 9.10 64 bit version.  Want to capture a short audio stream from a DVD.

VLC has a command "Open Capture Device" that gives the user options for ripping (I think) the audio tracks.  I made the relevant choices and got this message:

Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG AAC Audio.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.

What is to be done?

I went to synaptic package manager and I have FFMPEG, libavcodec, and AAC installed.

Any suggestions?

---

### Post by mc4man on 2010-06-20
You need a libavcodec that has aac (libfaac) enabled.

The easiest way would be to enable medibuntu and then install/upgrade to their extra version of libavcodec (libavformat, libavutil also wouldn't hurt

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


[package list]("http://packages.medibuntu.org/karmic/index.html")

---

### Post by raymondvillain on 2010-06-20
Thanks, mc4man.

I went to Synaptic Package Manager and it says that I already have libavutil-extra-49 installed, also libavformat52.

I'm beginning to think that VLC is not the best tool for my purpose.

---

### Post by mc4man on 2010-06-20
> I went to Synaptic Package Manager....
All ubuntu repo versions of libavcodec have been stripped of aac encoding, only the medibuntu one has it enabled
(other than a ppa or self built

> 
I'm beginning to think that VLC is not the best tool for my purpose. 
Thay may be true - best to describe exactly what you're trying.

---

### Post by raymondvillain on 2010-06-20
Well now it started working, sort of.

I open VLC media player and under Media>open disc there are choices.  I indicate the title number, and chapter.  Enable the check box "show more options" and one can select "stream, play, or convert" from a drop down box.

I select "convert" and then type in the destination file, and from a drop down box choose the conversion type to be "audio-flac".

This creates a flac file which I can then play on amarok or rythmbox.  Unfortunately for me it rips the audio of the entire chapter, not just the 45 seconds I want.

Does anyone know a way to drill down to exactly the selection of interest?

---

