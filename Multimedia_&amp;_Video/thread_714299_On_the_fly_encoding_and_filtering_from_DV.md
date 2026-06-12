---
title: "On the fly encoding and filtering from DV"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by frankerooney on 2008-03-03
I've searched around alot and still can't find the answer to my question. I can easily, using pipes and dvgrab and ffmpeg convert video from a DV camcorder on the fly into mpeg video. I want to, however, be able to build filter chains, usually a sharpening filter, into the on-the-fly encoding process. mencoder and transcode both seem to support filtering but are not happy with taking stdin input (or I'm doing something wrong there). VLC can also encode to mpeg using --sout option but doesn't do filtering. I've got a fairly ballsy computer which should cope with the process, so does anyone know how to do it?
Thanks in advance!

---

### Post by frankerooney on 2008-03-28
Just updating my own post in case it's useful. Just to recap I wanted to be able to record off the tv without .dv files taking up half my hard disk for an hour or so's recording.

There's two ways of doing streaming straight to mpeg or similar;

using FFMPEG, so a script might look like
dvgrab --noavc - | ffmpeg -i $1 -target pal-dvd -b 3.5m $2

Works fine, but I've changed to using VLC, as I didn't like the output from ffmpeg quite as much - it's blocky in comparison. Below is my script to encode video using VLC's transcode facility. This is obviously just the line that does the business, you'd need to build in error handling etc. It's for PAL, and I found a bit rate of 3500kb/s was the best compromise. You can change the audio codec for mpga if you want mp2 audio. The main disadvantage to using vlc is that despite the aspect ratio option, it creates a file that dvdauthor complains about having an "unknown aspect ratio", so I have to include a second long mpeg of blank screen with the correct aspect ratio in my dvdauthor xml file to sort it out. (or re-run it through mencoder)

dvgrab --noavc - | vlc /rawdv:- --sout '#transcode{width=720,height=576,deinterlace=disable,vcodec=mp2v,vb=3500,fps=25.0,acodec=a52,ab=192,scale=1,channels=2,audio-sync}:std{access=file,mux=ps,dst='$1'}' --aspect-ratio="4/3"

I'd love to be able to use mencoder to allow the filtering, or transcode, but can't work it out. In fact, I'm sure mencoder doesn't allow pipes, and doesn't seem to function with a FIFO file. I think transcode is the same unless someone can correct me.

:-) Andy

---

