---
title: "RhythmBox and Banshee Issues - Ripping mp3 files from CDs"
date: 2009-06-08
forum: Multimedia Software
---

### Post by divinityofnumber on 2009-06-08
I have boxes of old compact discs, and I would like to rip them into mp3 file format at a bitrate of 192 or greater. I initially had some problems getting RhythmBox to rip the files in anything over 128kbps, so I decided to try Banshee. 

In Banshee, I can select different bitrates very easily, and I have tried 320, 256, and 192kbps. But, after Banshee rips the files, upon right-clicking one of them and inspecting it, the bitrate is fine, but the other information such as track name, band name, album name, etc, is not recognized. It is all there and looks nice when I am playing the mp3s in Banshee. But, from past experience with my iPod, I know that once I put these files on my iPod, they will all be lumped into an 'untitled' or 'unknown' category. 

I want to rip the files from the Cds, and have the file in 192kbps+, and also have the file show the band name, track name, and album title when right-clicking on the file and going to the top far-right hand tab named 'audio.'

Can anyone out there help me with this?

---

### Post by HappyFeet on 2009-06-08
you could try RipperX. It is in synaptic.

---

### Post by divinityofnumber on 2009-06-08
I downloaded and installed ripperX, but it was a little more complicated than the other programs. Is there an easy way to rip tracks in the manner that I had suggested? 

Sound Juicer will do it at 128kbps bitrate, but I want to rip the tracks at a higher bitrate.

I have the ripping profile set up, Gstreamer pipeline as -  

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux 

I read in a different thread that the bitrate is determines by the quality value, with zero being the best and 10 being the worst. Maybe there is a way to alter this to do what I am desiring. I just want to rip songs at 192kbps or above and have the resulting mp3 file contain the artist, album, and song titles when you right click on it and select the top right tab, 'audio.'

---

