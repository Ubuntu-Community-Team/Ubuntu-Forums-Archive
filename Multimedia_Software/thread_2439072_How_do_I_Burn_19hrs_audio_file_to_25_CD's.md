---
title: "How do I Burn 19hrs audio file to 25 CD's"
date: 2020-03-22
forum: Multimedia Software
---

### Post by cerixon on 2020-03-22
Good Morning, Afternoon and Evening 4 Today;

 
 
 I have a audio file that is 19+ hours straight,
 I would like to put this on CD’s  (ABOUT 25 of them) for a family member, that would like to listen in their vehicle.
 
 
 What is the best program (free) there is, in Ubuntu software land;
 
 
 I want to be able to pause and slice with keyboard strokes to get precise position.

 
 
 Tried that in Audacity but could only use my mouse, and I could not get it to a 'good stopping point'

I download Audacity; Brasero and K3b, but not able to find a program that will enable me to have more control of the file, instead of using the mouse,

Please help

I am using Ubuntu 18.04 (I think)

---

### Post by TheFu on 2020-03-23
Audacity has a "Silence Finder" that would be helpful to find split points.  I use 2.5 seconds of "silence" for a label to be added.  Then I use mkvmerge with the --split timecodes: .... option to create all the different files.  The inputs are **ogg** audio, which can be output as **opus** with mkvmerge.  mkvmerge deals with opus audio output and mkv containers only.  Then the opus files can be batch converted to mp3 if you like.

There was a hassle with the label timecode export.  It generates seconds only, but mkvmerge needs hh:mm:ss.sss, so a little perl script to the rescue.  I think audacity can directly split the files, but I didn't like how it wasn't batch. When creating hundreds of files, a batch mode is nice.

I haven't created an audio CD ... er ... ever.  But I do split 11 hr single file  audiobooks into 15-45 min files which can be played back on any of my players. My car has a DVD that can playback mp3 files in order and an aux port for connecting a tablet or smart phone. Smartphones general can play ogg, opus, wav, mp3, aac and a few other formats, but it depends on the player used.  Some of the built-in players are really stupid and want to force streaming over internet data, but there are local media players too.

---

### Post by Holger_Gehrke on 2020-03-24
And then there's mp3splt and it's graphical frontend mp3splt-gtk. It can split mp3, ogg and flac without re-encoding and back when I used it last it had an option to find long silences to use as split-points. According to 'apt search' it is in the repos.

Holger

---

