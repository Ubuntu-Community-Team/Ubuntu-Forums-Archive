---
title: "Mythbuntu 9.10 with VDPAU rocks on Acer Aspire Revo"
date: 2009-10-31
forum: Mythbuntu
---

### Post by Captain_Bodge on 2009-10-31
Just wanted to post and say, I installed Mythbuntu 9.10 today and playback with VDPAU really rocks.

My hardware is an Acer Aspire Revo, which is an Intel Atom-based platform with an NVIDIA Ion chipset and HDMI output. I was previously running Mythbuntu 9.04 on an Asus EEE Box, which is similarly specced but with Intel graphics and no HDMI. There is no comparison between the two as far as playback quality is concerned. The Intel Atom isn't up to much, it's not great for video playback so being able to put the load on the NVIDIA hardware makes a huge difference. I used to use my Playstation 3 for playback (via uPnP) if I knew a movie had lots of action but no more, mythtv with VDPAU is great. Nice one guys. HDMI "just worked" and picture quality is superb.

---

### Post by dschobel on 2009-10-31
What did you do to enable VDPAU? I just upgraded to 9.10 and have nvidia hardware which claims to support VDPAU...

---

### Post by Captain_Bodge on 2009-10-31
In mythtv Setup, under TV Settings - Playback Profiles, set Current Video Playback Profile to VDPAU High Quality. That seems to be enough.

---

### Post by dschobel on 2009-10-31
Excellent. It dropped cpu usage on a c2d 2.8ghz from 70-80% to single digits when watching 1080p video.

Thanks!

---

### Post by picbits on 2009-11-01
I'm still struggling with mine.

I've got everything working so far apart from sound in Mythvideo.

I can play 1080p fine and everything now works with my new mythbackend but no sound in Mythvideo lol.

VLC works fine as does pre-recorded programs, just not anything in the Videos section.

I did however install Ubuntu desktop first before installing Mytbuntu on top of that.

I might have to have a play with Mythbuntu 9.10 "out of the box" again

---

### Post by Silver Surfer on 2009-11-06
> **picbits said:**
> I'm still struggling with mine.

I've got everything working so far apart from sound in Mythvideo.

I can play 1080p fine and everything now works with my new mythbackend but no sound in Mythvideo lol.

VLC works fine as does pre-recorded programs, just not anything in the Videos section.

I did however install Ubuntu desktop first before installing Mytbuntu on top of that.

I might have to have a play with Mythbuntu 9.10 "out of the box" again

I'm having the exact same issues with sound through the HDMI port.  It works perfectly with the pre-installed windows xp, but I cannot get sound going with Ubuntu.

---

### Post by Dewey_Oxberger on 2009-11-06
For some help with audio over hdmi make your way to this thread:

[http://ubuntuforums.org/showthread.php?t=1285957](http://ubuntuforums.org/showthread.php?t=1285957)

Download the asound.conf.txt file and have a read.

---

### Post by picbits on 2009-11-07
Well I did get mine going albeit without 1080p and sound through Myth (although I can run Mplayer with VDPAU, 1080p and get sound). Myth (it appears) doesn't allow you to use an external player with storage groups or something like that so that could be the issue with mine - I will have to investigate further.

On the sound side of things, I installed the latest version of the Nvidia drivers, enabled sound through HDMI via clicking on the speaker icon at the top and assigning it to the HDMI digital output, going into Myth Frontend setup and changing the audio output to alsa:plughw:0,3 (or something like that) and the sound worked fine in most of the stuff apart from 1080p.

I cant get to play on the Revo at the moment as I'm working on my new server as a priority, the old one is making rumbling noises so I need to get the new one sorted and everything copied over.

Apart from that, I've got everything else going on the Acer (including LIRC through the MIC port using a cheap £1 IPOD IR adapter I picked up from our local 99p store and adapted - you need to rewire it, add a capacitor, a resistor and grab a USB lead for the power but its less than an hour to do start to finish). I've got it all working with my Sky+ remote control and the TV remote so there is good scope for messing about with these :D

Just as another side note, I've noticed that Mplayer does not release the HDMI port properly when you exit it without it reaching the end of the file its playing. This results in the TV making clicking noises through the HDMI sound until either a sound is played through the desktop or another instance of Mplayer is started up which seems to reset the HDMI output.

Now I just need to get this flaming server working with Mythweb - everything is fine but Ispconfig 3 is giving me grief when trying to run Mythweb on a vhost.

---

### Post by picbits on 2009-11-07
P.s. @ Silver Surfer - my little brother has just bought a house in Irvine - I hear you had rain there the other day :lolflag:

Fantastic place - we went over last March and fell in love with SoCal

---

### Post by jquintana on 2010-01-05
What are you using for DVD/Blu-Ray? About to go pick one of these up but concerned about DVD/Blu-Ray playback.

---

### Post by Captain_Bodge on 2010-01-05
I have a dirt cheap USB DVD drive that works perfectly. I haven't tried Blu-Ray, don't know if there are any external Blu-Ray drives.

---

### Post by davidstoll on 2010-01-16
Sure there are.  Just get a 5.25" USB or eSATA or FireWire enclosure and put any hard drive or optical media drive in it.


> **Captain_Bodge said:**
> I have a dirt cheap USB DVD drive that works perfectly. I haven't tried Blu-Ray, don't know if there are any external Blu-Ray drives.

---

