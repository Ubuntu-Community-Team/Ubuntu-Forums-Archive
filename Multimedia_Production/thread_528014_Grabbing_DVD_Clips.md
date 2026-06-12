---
title: "Grabbing DVD Clips"
date: 2007-08-17
forum: Multimedia Production
---

### Post by marksy1984 on 2007-08-17
Hello. I would like to be able to grab (2.5 minute) DVD clips from any DVD and convert them to a format I can use in presentations. 

On Windows XP I used a combination of DVD43, Handbrake, and MPEGStreamclip. 

Can anyone point me in the right direction to do the same in Ubuntu 7.04? 

Is there any alternative software?

---

### Post by sarriola on 2007-08-17
Avidemux is a program that  you can use to do this . Use
"Add/Remove Applications" or Synaptic to install it.

   The first thing you need to do is copy the VIDEO_TS folder on the DVD to your hard disk. If your DVD is encrypted then you need to do 
the DeCSS thing before you do this.

The second step is to  open the *.vob files that are in the VIDEO_TS folder on your hard disk; filter on the the *.vob files and try to load one of them. You will be asked if you want to index the file, click "OK" . This creates an index file in the same directory which is the reason 
why you copy the VIDEO_TS folder to your hard disk. The video will be loaded and then you can edit what is loaded. Cut and crop  until
 you have the piece you  wanted to grab, then save it to one of the
 output formats Avidemux  supports.  If you chose one of the MPEG
 formats to output to then you can  specify "copy" for the video and 
audio which  means your clip  won't be re-encoded. 

Another tactic is to convert the whole DVD to mpeg4 using k9copy.
And then experiment with one of the other video editors or with Avidemux itself to see if you can edit things down to your clips.
I'm experimenting with this now to see if it's do able.

   Sam A.

---

### Post by stmiller on 2007-08-20
Dvd:Rip (apt-get install dvdrip) has a nice GUI where you can pick specific frames to rip and encode into many formats.

Handbrake does perhaps the best job quality wise, if you want good high quality H.264.

---

### Post by nalakag on 2007-08-22
You could also use acidrip. Easy to use.

---

