---
title: "amaroK problems"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by luc1fersflowers on 2006-09-17
Ok, so I've got an interesting situation here. I'm on a dell inspirion 6000, running Ubunutu-686, I also have a Audigy 2nx USB soundcard. My problem is that 90% of the time amaroK plays through my laptop speakers (Intel ICH6) regardless of what sound out-put i'm using. The only sound engine I'm running is xine. Is this a problem because i'm not running it under KDE desktop envirionment? or is this a bigger issue with my sound? Sometimes I can get it to play through my A2nx but only for one song, and when it changes songs it goes right back to my laptop speakers. Also, everything works great with other audio players xmms, rythmbox, etc. in regards to always playing through my usb sound card. I just really like amaroK, and is it just me or does it sound better? Thx for any help guys, i love this community, it is honestly what makes linux what it is. <3

---

### Post by drFUNK on 2006-09-17
Try going to settings > Configure Amarok then go to the engine tab.  Then select alsa as the output plugin and press apply.  Then under Alsa Device Configuration type "hw:1,0" in the stereo field.  I have an Audigy 2 zs PCMCIA card and this is what I had to do for playback through the sound card.

---

### Post by luc1fersflowers on 2006-09-19
where is alsa device configuration?

---

### Post by Aramil Moonmist on 2007-03-20
> **drFUNK said:**
> Try going to settings > Configure Amarok then go to the engine tab.  Then select alsa as the output plugin and press apply.  Then under Alsa Device Configuration type "hw:1,0" in the stereo field.  I have an Audigy 2 zs PCMCIA card and this is what I had to do for playback through the sound card.

after 3 days of scanning these forums (what can i say, ive found a passion for fixing bugs) , i finally stumbled on this post.....5 seconds later, crystal clear sound running through my speaker system, thanks : D

---

