---
title: "Audio TS DVD A creation"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by iUSER-Mike on 2007-07-09
Hello, In XP (yuk), I was able to create DVD A discs (Audio TS not Video TS). Is there anything like this avaiable for Ubuntu, please?:guitar:

Mike

Cheers

---

### Post by RomeReactor on 2007-07-09
Hi. I know this isn't an ideal solution, but K3B has an option (under **tools**) to make a Video DVD in which it gives you VIDEO_TS and AUDIO_TS folders; you could try to copy/paste the contents of your audio_ts folder into the one K3B offers you and see if it works. I'm not sure if it'll give you an option to make a "pure" audio DVD, though, and apart from K3B, I haven't come across an application that will let you. You can find K3B through Add/Remove, Synaptic, or from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install k3b
```
I recommend you use Synaptic to install it, as it will give you more control over the added components; in Synaptic, search for **k3b**, once it finds it, right-click it and mark for installation all the **Suggested** and **Recommended** packages.

Hope this helps.

---

### Post by Scotty1982 on 2007-07-09
Hi, just a dumb side question... i've always wondered what the audio_ts folder was for. is it what all those audio dvd's use? that's what it sounds like from what's posted in this thread so far.

just wondering 'cuz i've never seen anything in that folder for video dvd's and i don't have any audio dvd's right now to look.

---

### Post by RomeReactor on 2007-07-09
Hi **Scotty1982**. Usually Video DVDs come with empty AUDIO_TS folder, containing the audio tracks in the VIDEO_TS folder. Every once in a while a DVD *will* have information in the AUDIO_TS folder, but I think that's more for providing AUDIO DVD comaptibility (for example, if the DVD comes with the complete soundtrack of the movie and can be played as a standalone AUDIO DVD). I don't know how accurate [this description]("http://www.afterdawn.com/glossary/terms/audio_ts.cfm") is, but it goes along similar lines to what I think the structures of Video and Audio DVDs are. Hopefully someone with concrete knowledge about this issue can comment on this.

---

### Post by iUSER-Mike on 2007-07-10
Audio TS is for music only. Basicaly its a more audiophile way of storing music. 

[http://www.answers.com/topic/dvd-audio?cat=technology](http://www.answers.com/topic/dvd-audio?cat=technology)

 I used Wavelab 5.0 on Xp, got my hands on Vista, cos her indoors likes it, and Wavelab won't work on Vista. Some say they've been able to, but I havn't, not even in Compatibility mode. What I did get was Virtual Pc from Billy Gates's website that lets me run Xp as a virtual PC. Dragging files from host to virtual and back is a pain. Ahead's Nero 7 was supposed to be able to create them, but when I had it installed, I couldn't find how to do it. and Ulead Movie Factory 4.0 did but with only 16Bit files up to 48 khz sampling. 24/96 or 24/192 is more like it.

cheers
:)
Mike

---

