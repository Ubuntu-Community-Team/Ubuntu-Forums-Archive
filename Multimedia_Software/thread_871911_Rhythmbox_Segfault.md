---
title: "Rhythmbox Segfault"
date: 2008-07-27
forum: Multimedia Software
---

### Post by Existentialist on 2008-07-27
I've had this problem since I began using 8.04.  At what seems to be arbitrary times, Rhythmbox shuts down.  Looking at dmesg, I get the following:

rhythmbox[7513]: segfault at 968 rip 7fe3813b3d9c rsp 433d6e70 error 4

It always happens at the transition between songs, but not on any particular songs.  Sometimes it will play for hours, while other times it shuts down every few minuets.  I experience this same problem on my laptop and desktop.  Since all of my music is sill in Apple Lossless format I assume it is an issue with the gstreamer plugins rather than Rhythmbox; but I thought I would see if anybody had any suggestions or had encountered similar issues.

---

### Post by kakyoism on 2009-04-24
Same here. Seems that gstreamer has problem with certain formats. Don't know exactly which kinda encoding but same thing would happen with Banshee or other gstreamer frontends.

---

### Post by odwyerda on 2009-11-25
I got this problem out of nowhere also. Basically making the programme useless


I cant change song, when i do it crashes. 
I removed the programme and reinstalled still having the same issue.

```
Nov 25 12:34:21 XXXXX kernel: [ 3520.465972] rhythmbox[3259]: segfault at 38 rip 7f42b433980f rsp 7fff0d4b9c40 error 4 
```


Using Ubuntu HH and rhythmbox 0.11.5



Dave

---

### Post by chuckh1958 on 2009-12-23
Same here using ubuntu 9.10, rythmbox 0.12.5.

---

### Post by tareksobh on 2010-03-16
I have the same issue too with Rhythmbox... I play Apple Lossless file format, and the sound quality isn't good but becomes much better when the system volume is reduced to half... I much prefer FLAC, but I sadly own an iPod that only allows Apple Lossless...

---

### Post by chuckh1958 on 2010-03-16
> **tareksobh said:**
> I have the same issue too with Rhythmbox... I play Apple Lossless file format, and the sound quality isn't good but becomes much better when the system volume is reduced to half... I much prefer FLAC, but I sadly own an iPod that only allows Apple Lossless...

I thought ipod supported mp3. No? My wife has one and I just add the folder with the mp3's into the itunes library and it syncs them with her ipod.

Why use lossles and not a good quality mp3 or aac? You'll fit *tons* more music on your player that way and won't be able to tell the difference. With a good quality mp3 file the difference between "lossey" and lossles is imperceptible to the human ear. I use mp3 format with 192k VBR and set the VBR quality setting to it's highest quality setting, and a low-pass filter at 19.7k The output files are 1/4 the size of the original flac and I can't tell the difference in sound quality on my portable.

Here's a really good article on lame settings if interested.
[http://jthz.com/mp3/](http://jthz.com/mp3/)

---

