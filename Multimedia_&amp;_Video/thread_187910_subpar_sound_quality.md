---
title: "subpar sound quality"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by qiemem on 2006-06-03
Unfortunately, I recently had to reinstall XP on my machine and thus am now dual booting. However, since doing this, I have noticed that the sound quality is much better while running XP than Ubuntu. Most notably, there seems to be a significant lack of bass and overall clarity. Any ideas? 

I tried using gnome-alsamixer, messing around with the setting there, including reducing PCM (as I read that this can help elsewhere) but it just made it quieter, not better. Master mono (strangely) seemed to increase the bass, but as its not subject to audio controls (it doesn't seem to go through the normal master), this isn't really a desirable solution. 

So far, I've only noticed this while using audio players (any audio player) and haven't tested videos (though flash sound exhibits reduced quality as well). I haven't used external speakers in a while, but I seem to remember them having somewhat reduced quality as well (though I managed to fix that alright by adjusting their eq). That's not necessarily related though.

Please, save me from having to depend on Windows for music... Any help would be most appreciated.

---

### Post by qiemem on 2006-06-04
bump

Anyone? Has anyone else experienced this too? Sound is just fuller when I'm running windows... Is this a driver issue or what? Anybody?

---

### Post by JoWilly on 2006-06-04
In the gnome mixer (sound volume) preferences you can select the options you want to control.

I.ex: for my SB audigy, i can select tone, bass, front, surround, etc...

Alsa does not support all settings for all cards, but check if these setting s (tone/bass) are available to you.

---

### Post by wayanwolvie on 2006-06-08
Yeah, I also find that Windows sounds richer than Ubuntu. But I found something interesting. If I use Ubuntu and run my Windows XP as guest OS using VMWare then play music inside the Windows, it still sounds better than play music using Amarok or XMMS. Quite strange, isn't it?

---

### Post by qiemem on 2006-06-08
[quote="wayanwolvie"]
If I use Ubuntu and run my Windows XP as guest OS using VMWare then play music inside the Windows, it still sounds better than play music using Amarok or XMMS. Quite strange, isn't it?
[/quote]
Hey, that is really weird. I don't know enough about VMWare or any of this to really know what would cause that, but... I don't know... Anyone?

[quote="JoWilly"]
 	In the gnome mixer (sound volume) preferences you can select the options you want to control.

I.ex: for my SB audigy, i can select tone, bass, front, surround, etc...

Alsa does not support all settings for all cards, but check if these setting s (tone/bass) are available to you.
[/quote]
Ya, I have none of these options. Is there anything else I can try?

---

### Post by lognok on 2006-06-17
Don't know if this is related, but here goes:

I experienced quite a bit of distortion when I played a cd thru Ubuntu (with Master and PCM sliders all the way up), compared to no distortion in WinXP.
  After a lot of tweek'n with the audio-control sliders, I was about to give up playing music in Ubuntu, when I noticed that the application (Sound Jucier on this occasion) had it's own volume control.
  When I adjusted the volume control down in Sound Jucier, the distortion dissapeared and I was able to max the Master slider and PCM slider without any distortion and still have enough volume thru the speakers to satisfy me :p 

note: I later changed to Banshee player and it also has it's own volume control that distorts outpu if turned up enough.

I hope this reply is helpful, if not, please excuse me...

---

### Post by jx2150 on 2006-06-19
Why does this happen though?

I want to be able to play my music just as loud in Ubuntu as I do in Windows... but I can't, without distortion.

Really a drawback.

-Jack

---

### Post by JoWilly on 2006-06-19
[quote=jx2150]Why does this happen though?

I want to be able to play my music just as loud in Ubuntu as I do in Windows... but I can't, without distortion.

Really a drawback.

-Jack[/quote] 
Don't forget to post a bug report (after searching) on launchpad so that the dev know about it and can fix the alsa defaults for your card, and also don't forget to complain to your sound card manufacturer who's offering subpar drivers (or no drivers at all, what is your card ?) on linux.

---

