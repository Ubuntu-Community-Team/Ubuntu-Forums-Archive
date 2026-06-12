---
title: "KDENLIVE help with exporting"
date: 2007-09-27
forum: Multimedia Production
---

### Post by staticvoid on 2007-09-27
Hey could someone give me some setting I could use in the export box for kdenlive ? All I need is a video that I can upload to google video then post to a blog. Whenever I try to export it as a .mov. mpeg and AVI file, it plays all messed up, with the colors all strange or the sound all off. If someone could fill me in that would be great, it was hard enough trying to figure out getting 19:6 wide screen .MOD files to edit. Now I just need to export it all. I love all the options, but I can't get one of them to work. Help would be a ppreciated :D

Static Void

---

### Post by staticvoid on 2007-09-29
I'm sure someone here who uses KDE know how to render a file from the timeline...

sv

---

### Post by flawedprefect on 2007-10-01
Yeah... formats are always a sort of "black art" no matter what platform. One of the things I find that KDEnlive doesn't quite deliver on is allowing you access to tweak each format. I would suggest two things:

Go to File>>Export TImeline.

1 - play around until you find a setting that works well. My suggestion would be Medium Quality, Quicktime 352x288 - it compresses it well enough on my machine - and then try a few similar ones.

2 - export a high quality render in a DV format, then use another compressor like ffmpeg to tweak your settings.

---

### Post by staticvoid on 2007-10-01
Hey thanks :) I'll mess around with it a litle more. I suspect that that is not the problem though: what I have exported to so far has always had the same errors: audio is off and colors are messed up. I'll try quicktime and dv though

sv

---

### Post by flawedprefect on 2007-10-01
One thing you might want to research - for your own interest - is how different compressions work. I come from a mac environment, and I use tools such as Final Cut Pro, Compressor, Episode Pro, etc, and most of these programs give you a lot of control over bitrates, audio compression, image size, etc. KDEnlive seems to only give you a list of presets - a fairly lengthy list, however! :) But without the option to tweak them... or I haven't discovered how.

I think some of the compressions look a bit dodgy cos of how Linux handles the codecs... but I could be wrong. I found screen aspects a little skewed on some; yes, I experienced the weird color flicking, and the audio bitrate was a bit off.

A good habit for now with audio: stick to bitrates like 22050khz or 44100khz. I've generally found they're more stable on Linux than 48000 - which is the digital standard.

I've found websites that deal in video compression (youtube, blogger, etc) give me weird speeds if I upload a video wtih 48000khz. I'll keep looking into compression, because it's the one thing making this great tool FRIGGIN AWESOME.

---

### Post by staticvoid on 2007-11-06
Hey, thanx a ton for the tips! I will definatly make use of what you said about the audio.

sv

---

