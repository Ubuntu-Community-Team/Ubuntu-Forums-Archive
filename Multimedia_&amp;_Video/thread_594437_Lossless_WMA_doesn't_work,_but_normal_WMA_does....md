---
title: "Lossless WMA doesn't work, but normal WMA does..."
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by pcmattman on 2007-10-28
Hi everyone,

I've looked around for a couple of days now trying to figure out how to play lossless WMA files in Rythymbox.

I'm able to play them in Totem, but Totem doesn't have a library system and I like Rythymbox.

I tried out a non-lossless WMA file in Rythymbox to test if it was WMA files but it played back perfectly, so I'm pretty sure w32codecs installed properly.

There are several hundred music files I want to play in Ubuntu, all of them lossless WMA files. Any ideas as to how I can play them, without losing quality?

---

### Post by crono141 on 2007-10-30
by "lossless WMA" do you mean WMA encoded with WMA10?

Because if so, I have the same problem with ripped DVDs that use WMA10 for audio.

---

### Post by pcmattman on 2007-10-30
I mean tracks I've ripped from a CD in the lossless format (in Rip Settings). I'm currently trying to figure out how to convert all of the tracks to mp3 while keeping the folder structure and the old files.

---

### Post by jasontan6 on 2007-11-10
Am having the same problem here too. Normal WMA works (bit rate less than ~350kbps), but lossless WMA (~1000kbps) doesn't play at all.

I have installed these packages:

Ubuntu Restricted Extras and Multimedia Codecs (from Automatix)
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

I've ripped many CDs in WMA lossless, I hope I won't need to convert just to play in Ubuntu :(


EDIT: Okay this is weird, I cannot explain why. At the time of writing this post neither Rhythmbox, Exaile nor Amarok could play WMA lossless. Following that I took the advice from[ this post ]("http://ubuntuforums.org/showpost.php?p=2369680&postcount=3")and it didn't work. After that I fired up Automatix and installed W32-DVD Codecs. All of the sudden Amarok is able to play WMA lossless! (Exaile and Rhythmbox still can't, however).

In the interest of trial and error I removed the two aforementioned packages to see if Amarok still plays WMA lossless, and surprisingly, it can! I am not sure if this is some random dependency package which is not removed, or whether it is a result of my inconsistent experimenting. :-P

---

