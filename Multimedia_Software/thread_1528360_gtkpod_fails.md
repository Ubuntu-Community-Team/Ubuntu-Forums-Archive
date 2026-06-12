---
title: "gtkpod fails"
date: 2010-07-10
forum: Multimedia Software
---

### Post by JakeFrederix on 2010-07-10
Hi everyone,

I recently purchased an Ipod classic 160GB. I've tried putting video-files on it with both Rythmbox and Gtkpod. I must be doing something wrong.

Things I've done;

1) convert files to .mov files using avidemux. => files are 0 seconds long (even though they are not 0 bytes big). I can put these on my ipod, but since they are 0 seconds long, ipod briefly shows black screen and returns.

2) put mp4 file on ipod with gtkpod (gtkpod aac). => Even though it is the 'aac'-version I still get the warning about not having compiled it with the library that supports mp4-files. I also get a warning saying "The following track could not be processed (filetype is known, but analysis failed) ... '

3) put mp4 file on ipod with rythmbox. => Simply doesn't do anything. No warning, no copying of files.

I was hoping someone would be able to shed some light on this.

Thanks,
Jake

---

### Post by JakeFrederix on 2010-07-11
I've installed the restricted extras, and this changed some things.
For instance now I can copy .mp4 files to my ipod. They have a size != 0 and a length != 0 seconds. The ipod still shows a black screen (briefly) and then returns to the menu.

Of course, Ubuntu is able to show all videos (even the ones that are problematic in ipod).

---

### Post by JakeFrederix on 2010-07-11
The problem does not occur on all videos.
I cannot yet determine what makes a video problematic or not.

---

### Post by PDA1 on 2011-12-03
I've found the same problem with my 160g and that the solution was to only load videos that were 320x240.

I use FFMPEG to convert all of the videos that aren't in that size.  Here's the code;

ffmpeg -i INPUT_FILE.mp4 -vcodec libx264 -preset medium -vpre ipod320 -crf 24 -acodec libfaac -aq 100  -vf scale="320:trunc(ow/a/2)*2" OUTPUT_FILE.mp4

---

### Post by enjoijesus94 on 2011-12-04
hello JakeFrederix
try to download Winff

sudo apt-get install winff

---

### Post by PDA1 on 2011-12-05
I tried Winff- and couldn't wait to delete it.  The presets are out of date, don't work or require a master's degree in computer science to you.

---

