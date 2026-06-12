---
title: "Microphone not recording - A Possible Solution"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by clpc on 2006-11-10
Having spent many hours trying to get my microphone to work and having found a solution I thought I would place a post here just in case it helps someone else.
Firstly the problem was really odd because I could hear my microphone through the speakers if I had the playback mic control unmuted as you would expect but it wouldn't work on Skype or on the sound recorder.
I have both an onboard AC97 soundcard and a Sound Blaster Live Value in the computer.
After trying everything else I rebooted and turned the on board soundcard off and the problem went away.... for some reason the alsa drivers dont line the AC97 and the sound blaster both being installed.

Hope this at least helps someone else.

---

### Post by Choc_Salties on 2006-11-23
I have a problem with the sound as well on my side; I have a SoundBlaster Audigy 4 and an onboard AC97 (which i belive is turned off). Interestingly enough Windows reports it (or doesnt report it in the device manager, but Ubuntu (started on Edgy, moved back to Dapper) sees the device.

Well, one way of testing to to physically remove the SB card and just use the onboard... :( 

I just want Skype to work ](*,) :(

---

