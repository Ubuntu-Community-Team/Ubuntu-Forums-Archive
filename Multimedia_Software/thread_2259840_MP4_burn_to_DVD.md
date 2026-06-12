---
title: "MP4 burn to DVD"
date: 2015-01-07
forum: Multimedia Software
---

### Post by gordie692 on 2015-01-07
Hey guys I'm in Linux Mint 17.1 and downloaded a movie but never burned it to DVD it's a MP4 format will K3b work or what would be the best tool software to it to DVD

---

### Post by TheFu on 2015-01-07
DVDs are either data or video formats. Which do you want?
Also, mp4 is just a container. The video and audio codec needs to be known to determine whether transcoding is necessary or not, depending on if you want to make a DVD than can be dropped into any cheap DVD player for playback or just want to keep the movie on a disk as a backup.

If you need to transcode, avconv or ffmepg have a preset for dvd output. Then pretty much any DVD burner should take that file, not transcode it,, and burn to a structure that is required for DVD playback.  That's the theory.

---

### Post by ajgreeny on 2015-01-07
I have not had much luck producing a standard DVD in the past without using **devede** to produce the image for burning, but that has always worked fine for me.

---

### Post by scone3 on 2015-01-14
To fast and easily convert MP4 to DVD, I suggest freeware [WinX DVD Author]("http://www.winxdvd.com/dvd-author/") to you.  It is an all-in-one DVD creating tool that can convert and burn almost all popular video files, including converting MP4 to DVD with high quality.

---

### Post by olduse78802 on 2015-01-14
If all you want is a copy stored on a dvd then all you have to do is use k3b and make a data disk.  It has some instructions on how and you could also youtube " burning data disk k3b " search for any how to videos. When ever i burn a disk i usually use 8x burning speed as i seem to get the best long term read results using that.

Hope that helps some.

---

### Post by speartip on 2015-01-14
> **scone3 said:**
> To fast and easily convert MP4 to DVD, I suggest freeware [WinX DVD Author]("http://www.winxdvd.com/dvd-author/") to you.  It is an all-in-one DVD creating tool that can convert and burn almost all popular video files, including converting MP4 to DVD with high quality.
Does this work on Linux? It looks like a Windows program to me.

If you require the movie to play on a normal dvd player, then the program Devede is the way to go. I always tick the box for "dual pass encoding" for better quality.
The process may take between 1 and 2 hours depending on the length of the movie.
The reult will be an iso file which you can then burn to dvd using k3b. It should play in any player.

---

### Post by Rob Sayer on 2015-01-14
> **speartip said:**
> Does this work on Linux? It looks like a Windows program to me...

Since that is the only post by a user who just joined today to recommend a Windows only program in language that reeks of sales bumf, it looks like a spam bot to me.

As far as the OPs question goes, burning the file without re encoding will only work if the video *format* ... the codec doesn't actually matter ... is supported by the player.  For DVD players that's just mpeg-2.

Otherwise, devede is probably the best to convert to DVD compliant video/audio.

---

