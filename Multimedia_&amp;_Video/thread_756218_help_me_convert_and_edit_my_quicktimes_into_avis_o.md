---
title: "help me convert and edit my quicktimes into avis or mpegs"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by davidshere on 2008-04-15
I have a Nikon Coolpix L1.  It takes video, which is great, but stores them in uncompressed MOV format, which is a nightmare.  The files' size-to-length ratios are astronomical.  The following example video (which is a knife edge pass of an F16) is only seven seconds long, but the video is 4.3 Megabytes:
[http://raptor.davidshere.com/Smyrna-Sunday/DSCN0876.MOV](http://raptor.davidshere.com/Smyrna-Sunday/DSCN0876.MOV)

My second example (which, near the end, captures an air show crowd's reaction to the "sneak pass" by the Blue Angles) is 3:30 long and is 131 Megabytes: 
[http://raptor.davidshere.com/Smyrna-Sunday/DSCN0898.MOV](http://raptor.davidshere.com/Smyrna-Sunday/DSCN0898.MOV)
... and I only want to keep the last 20 seconds.  

So I both want to compress and edit these .mov files, preferably into .mpg or .avi.  What are my options, things I should watch out for, and what should should I expect from the process?  Any advice would be greatly appreciated.

---

### Post by ron999 on 2008-04-15
Hi
Avidemux will do the job.

To convert:-
Load the file.
Set video codec to Xvid4.
Set Audio codec to Lame.
Set format to AVI.
Save.*

Afterwards use Avidemux to edit the files.

*Edit. Save as something.avi

---

### Post by davidshere on 2008-04-16
Thanks!  I'm having problems with the audio, though.  After I convert, I have something.avi, which has audio when played in Movie Player but no audio when played in Avidemux.  I edit the file to just the part I want and save it as something2.avi.  This file has no audio in either Movie Player or Avidemux.  

[http://raptor.davidshere.com/Smyrna-Sunday/something.avi](http://raptor.davidshere.com/Smyrna-Sunday/something.avi)
[http://raptor.davidshere.com/Smyrna-Sunday/something2.avi](http://raptor.davidshere.com/Smyrna-Sunday/something2.avi)

Also, both the avis and movs have what I can only describe as "grid points" in the video.  How do I get rid of these?
Also, the edited video something2.avi shows a time of 3:34 in Movie Player, but isn't really that long.  What happened there?

---

### Post by ron999 on 2008-04-16
Hi
I don't know why Avidemux isn't handling the mp3 correctly, it's the same for me too with your clips. Strange.:confused:

Instead, I've converted them using Winff (with the option 'Convert to.... XviD in AVI 4:3').
Then when I edit and save them with Avidemux later (with both codecs set at 'copy') the sound is still OK.
Winff uses ffmpeg to encode the sound, Avidemux uses LAME. Maybe that's the difference.
This is where to find Winff:-[http://www.winff.org/]("http://www.winff.org/")

---

