---
title: "Some .mp3 files sound really distorted"
date: 2016-03-20
forum: Multimedia Software
---

### Post by naomibrown on 2016-03-20
I've got some .mp3 files that sound really distorted when I play them in Rhythmbox on Ubuntu 14.04 but when I play the same file in iPlayer on Windows they don't sound distorted. However, I've got some .mp3 files that work fine in Rhythmbox! 

I've tried to fix this by using the [troubleshooting guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit") but I've got the whole way through it without any improvement. 

Any ideas? 

Thanks!
Naomi

---

### Post by naomibrown on 2016-03-27
Examples of the files that I'm having problems with can be found at: [http://www.wolston.org/sermonsortalks.htm]("http://www.wolston.org/sermonsortalks.htm")

---

### Post by speartip on 2016-03-27
Hi Naomi,
I'm using Xubuntu 14.04 with Banshee & Audacious as my media players. The files you linked to play absolutely fine here.
Do you have the ubuntu-restricted-extras package installed?
Also you may want to install pavucontrol, and check your volume levels. Sometimes too high can cause distortion.

---

### Post by speartip on 2016-03-27
Actually on second listen some of those files have a tinny echoey feedback sound.
If that's the problem you're referring to, it's not your system, it's the quality of the recording thats poor.
Even so it would help you to install the programs in the above post.

---

### Post by naomibrown on 2016-03-27
Thanks for the suggestions!

I already had the ubuntu-restricted-extras package installed. 
I tried listening to the files in Banshee and they sound the same as they did in Rhythmbox. 
I installed pavucontrol and have turned the volume down so that it doesn't go too high any more, but I still seem to have the same problem, both in Rhythmbox and Banshee. 

Finally I installed Audacious and I can hear the sound files really well. Yes, there is a little tiny bit of echo but I can now listen to the files without getting incredibly annoyed!!! 

Do you have any idea why listening to the same file in Banshee and Rhythmbox sounds so different to Audacious? And also, is there something similar that I could use on my Ubuntu phone? 

Thanks so much!!!
Naomi

---

### Post by speartip on 2016-03-27
It is probably a codec thing. Software like audacious and vlc pull in their own codecs, solving your issue. They are 2 programs I always install. Can't help with your ubuntu phone issue. Sorry.

---

### Post by yoshii on 2016-03-29
You will also want to check any ReplayGain settings within your playback software as well as embedded within each MP3.  
You can use Foobar2000 via Wine or something similar to remove the ReplayGain from every MP3 if you like.

---

### Post by Rob Sayer on 2016-03-30
I was thinking replay gain too or something similar.  Do you have volume normalization enabled on the program you're getting distortion with?  A lot of mp3s that people dl were normalized when encoded, and doing that twice will create distortion.

---

### Post by Yellow Pasque on 2016-03-30
Banshee and Rhythmbox both use gstreamer. IIRC, some folks had the same issue (poor playback of some mp3's) with the gstreamer-fluendo mp3 decoder. If you're sure that men in uncomfortable shoes aren't going to come knocking on your door (check local laws), try removing gstreamer1.0-fluendo-mp3 and make sure gstreamer1.0-plugins-ugly package is installed. That will use a different gstreamer codec to decode mp3 (either the libmad or mpg123 decoder).

---

