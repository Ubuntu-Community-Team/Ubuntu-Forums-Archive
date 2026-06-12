---
title: "CPU required for 1080p x264 playback"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by pgroudas on 2007-07-16
Anybody have experience playing back 1080p x264 encoded video?  I want to build a new htpc box and want it capable of doing it smoothly.  What clock speed is necessary for both core 2 duos or athlon x2's?  

I know that I could just get a nvidia 8500 and use windows, but obviously I'd rather spend $100 on the cpu and do the decoding in software and keep using ubuntu.  Thanks!

---

### Post by wolfen69 on 2007-07-16
any cpu made in the last 2 yrs. will be just fine. probably even older.

---

### Post by pgroudas on 2007-07-16
Thats not really true...I have a core duo 1.7 ghz that can't even touch 1080p.

---

### Post by Motoxrdude on 2007-07-16
My core2duo 6600 plays 1080p videos just fine.

---

### Post by pgroudas on 2007-07-16
Thanks!  Sounds good, now I'm just wondering if anything a little slower would be sufficient, as I am a total cheapskate.

---

### Post by Motoxrdude on 2007-07-16
The minimum i would go with is a amd x2 4600, but i would seriously consider getting a core2duo 6400 at least. I mean, i wouldnt want to "just get by". Leave yourself some head room.

---

### Post by Mr.Auer on 2007-12-12
Pentium 4  at 2.8 Ghz with Compiz Fusion running on Nvidia 7300 GT is NOT enough. Periodic slowdowns, audio cuts out at times, skips frames now and then. Im going to try with regular Metacity yet...

On my system Gxine worked better than VLC. Just tried this yesterday with Happy Feet animation in Matroska container, 1080p x264.

---

### Post by mcduck on 2007-12-12
> **pgroudas said:**
> Thats not really true...I have a core duo 1.7 ghz that can't even touch 1080p.

It depends a lot on the graphics card. My old desktop machine with Athlon XP 2800+ (@ 2300MHz) and Radeon 9600XT plays 1080p h.264/x.264 with no problems.

And any AMD/Intel CPU made in last 2 years is far more powerful than that old Athlon XP :D (don't let the clock speed fool you, it's not a measurement of computing power unless you are comparing two different speed models of the same CPU)

---

### Post by jasnix on 2007-12-16
> **Motoxrdude said:**
> My core2duo 6600 plays 1080p videos just fine.


Can you please explain to me what software you use to play x264/h264 files? I have heard that neither vlc or mplayer in the gutsy repo's support these containers.  Are you using software from CVS? 

I have tried to play these movies with mplayer, vlc, gxine etc... and the sound is always a little off sync with the video. Do you run into these kinda problems?

Thanks,
JasNix

---

### Post by theacoustician on 2008-01-03
> **jasnix said:**
> Can you please explain to me what software you use to play x264/h264 files? I have heard that neither vlc or mplayer in the gutsy repo's support these containers.  Are you using software from CVS? 

I have tried to play these movies with mplayer, vlc, gxine etc... and the sound is always a little off sync with the video. Do you run into these kinda problems?

Thanks,
JasNix

"These containers"?  How are your files muxed?  mkv, mp4, avi?  How is the audio encoded?

---

### Post by Lostincyberspace on 2008-01-04
I use smplayer it is great GUI for mplayer and has 99% of the features mplayer has.

---

### Post by btucker on 2008-01-04
I have a mini-mac with two cores @ 1.83Ghz.   It is possible to play back and enjoy almost all 1080p content - one core will get pushed very hard (mplayer) and the other one will be at  20-30% (xorg) - there is still idle time. 

Having said that, I watch HD-DVD video ( which isn't x264, I think it's vc1) and a couple of titles have outpaced my processor.  I suspect this is because it's still early days with the decoders.


My tips for HTPC
1) pay alot of attention to your video card and then sound system.  SPDIF cannot carry the newer audio formats (re BW) so your audio will have to travel over HDMI.  

2) your remote control

3) WAF - fan noise & looks


PS: I have a SVN mplayer version that supports it all ( MPlayer dev-SVN-r25384-4.1.2 ).  I did have to patch it for eac3.

---

