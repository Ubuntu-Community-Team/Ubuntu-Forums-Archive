---
title: "Converting .wav files to mp3"
date: 2010-11-16
forum: Multimedia Software
---

### Post by Timoteo32 on 2010-11-16
I copied some songs off a CD and wanted to convert them to mp3.  Is there a program that I should have used to rip them that would have done that or is there a program that will convert them for me?

---

### Post by arubislander on 2010-11-16
You can configure Rhythmbox to rip your CD's to .mp3 instead of the default (which is .ogg I think) I guess that would be the quickest solution for you by far.

---

### Post by Timoteo32 on 2010-11-16
Sweet man, I'll try that.  Cheers!

---

### Post by Timoteo32 on 2010-11-16
Crap! I went in and when I selected the "Preferred Format" mp3 didn't appear in the dropdown.  I clicked on "Edit" and it showed up on the list there but I couldn't see any options as to how to add those options to my dropdown to actually use....

---

### Post by karthick87 on 2010-11-16
You can convert .wav to .mp3 using sound converter.

```
sudo apt-get install soundconverter
```
or use lame

```
sudo apt-get install lame
```

Its a command line program.

---

### Post by jimmers on 2010-11-16
K3B will rip to MP3


Luck

---

### Post by Old_Man_Unix on 2010-11-16
**Sound Converter** will convert many of the more common formats and it is very easy to use.  I highly recommend it as a general audio file conversion application.  If you had good quality WAV files that you wanted to convert to MP3 files -  or to any other supported format - it would be fine.   

However, you don't actually have WAV files - you actually have  CD audio (CDA). 

Rhythmbox utilizes Soundjuicer- a simple ripping program for converting CDA.  If you have installed the proper MP3 codecs, it  *will* rip a CD by default to what is called "CD quality" MP3.  This may suit your needs.  Or it may not because it really isn't CD quality.

If you are just ripping CDs to, say,  play them on a portable  player, then using the defaults will probably be OK.  

If you are interested in good audio and you have a superior original source - e.g., a well-made CD in good condition -  I would not go this route.  You do have some choices how to go.  One is to adjust the default MP3 quality setting in the Preferences tab of Rhythmbox (actually, in Soundjuicer). Not so straightforward a task, however.  Another is to install a CD ripping program.     In any case, most listeners find the higher quality MP3 formats to be closer to or equal to a CD source.

---

### Post by Timoteo32 on 2010-11-16
Thanks guys! I installed Sound Converter but now it's only giving me the same options as Rhythmbox.  I can only convert to .ogg, .flac, and .wav  :(   I'm wondering if I'm doing something wrong or it's just these songs.  I think I'll try a different CD.

---

### Post by mc4man on 2010-11-16
Soundconveter and rhythmbox need gstreamer plugins for decoding/encoding 
(though for cd's to mp3's you may be happier with the other mentioned apps or some not mentioned

I believe it's the multiverse ugly plugin for mp3 encoding - to install most of the useful gstreamer plugins paste this into a terminal (one command, installs 5 plugins + add. 

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by Timoteo32 on 2010-11-16
Yeah, I was looking around and at the bottom in Music Converter there's a notice that said it wasn't installed with a link to where I could download it.

Thanks everyone for your help.  This is the most help I've gotten in a topic in quite a while.  I appreciate this community so much!

---

