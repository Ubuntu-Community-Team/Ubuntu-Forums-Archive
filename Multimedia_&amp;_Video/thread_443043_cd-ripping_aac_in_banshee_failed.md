---
title: "cd-ripping aac in banshee failed"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by mrpeenut24 on 2007-05-14
So I just spent the past 24 hours ripping dozens of cds in banshee in aac format.  When I synced them onto my mom's ipod none of them played.  When I look at the files in the directory, they show an average 5MB file, so they seem to be accurately sized.  When I look at them in banshee, they show a time length of exactly 4x their actual length, yet when I play them in banshee and on the ipod, they start to play, then skip on to the next one as if the length of each one is less than a millisecond, even though it shows their times as around 20 minutes.
  I'm using feisty with gstreamer0.10 with the good, bad, and ugly plugins from the multiverse, as well as faac (here's the pipeline: audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4).  Since the files won't play on the ipod, they obviously didn't encode correctly, but is it all lost?  Can I convert them to mp3 and see if they work?  This wouldn't be so bad if the ipod wasn't a mother's day present (along with switching her OS from XP to Feisty!) as I'm sure my mom wants to use it as soon as possible.
By the way, I'm not getting a "format not supported" like a lot of others, but when I look at the metadata info on the m4a file in banshee it shows the bitrate at 0kb even though the encoding was set to 128kb.  Hope that helps!

---

### Post by l0c0m0c0 on 2007-05-15
I'm having the exact same problem I hope we can figure this out, i'll update you if I do.

---

### Post by mrpeenut24 on 2007-05-16
I just went ahead and re-ripped them in mp3s.  But I would like to find out what the problem was.

---

### Post by l0c0m0c0 on 2007-05-16
I can't find an option in banshee or rhytmbox to rip in .mp3 how did you do it?

---

### Post by mrpeenut24 on 2007-05-20
First you have to make sure you have the multiverse repositories enabled.  Then, in a terminal, do:
> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gstreamer0.10-plugins-good
sudo apt-get install gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-ugly-multiverseI think this should let banshee show the mp3 encoding option.

---

### Post by sloggerkhan on 2007-07-15
I had this same issue ripping mp4, aac files. What works for me is using GRIP to rip them. I think what happens (this is speculation) is that the encoder for banshee is given a direct pipe from the cd data stream and that the CD data stream goes slower than the aac encoding, which leaves gaps while the encoder is waiting for data. Once again, this is a highly speculative theory, and if there were a way to control caching, might not be a problem. Anyway, GRIP works perfectly for me, and is in the repos. Only downside is it doesn't seem to have a metadate editor. (if you find one, let me know.)

---

