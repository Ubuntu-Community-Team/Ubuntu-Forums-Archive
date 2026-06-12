---
title: "external player won't play video if mythfrontend is open"
date: 2011-04-07
forum: Mythbuntu
---

### Post by david1212@gmail.com on 2011-04-07
I have a fresh install of mythbuntu 10.10.

I added some things like nautilus, kde, phpmyadmin and some other packages.

I try to play a video file using vlc or any player external to mythfrontend while mythfrontend is running. The result is the video will not play. It just sits there with a black screen. If I quite mythfrontend the video will begin to play.

It seems like mythfrontend has something like sound locked and is not sharing it.

I have googled but I haven't found a similar problem posted. Probably because I am searching for different terms than were used by someone with a similar problem.

Can you help point me in the right direction to finding a  better definition to this problem and possibly a solution?

---

### Post by jyavenard on 2011-04-09
> **david1212@gmail.com said:**
> 
I try to play a video file using vlc or any player external to mythfrontend while mythfrontend is running. The result is the video will not play. It just sits there with a black screen. If I quite mythfrontend the video will begin to play.

It seems like mythfrontend has something like sound locked and is not sharing it.



Is mythfrontend doing anything?

If sitting in the menus; the mythfrontend doesn't use the audio card. so it's available for any other applications.
When using ALSA, as a rule of thumb, only one application can use the audio device at a time, unless you use pulseaudio.

Are you using VDPAU? depending on the drivers you are using, you can only have one application using VDPAU at a time

---

### Post by david1212 on 2011-04-12
No mythfrontend is not doing anything.

I have been using linux and mythtv for years, but it seems like a new ball game with every version I put on. 

I don't know if I am using ALSA and I wouldn't know a VDPAU from a vanilla late.

I am a computer geek, power user, etc. but I just can't seem to keep with all the curve balls coming with every fresh install I do, and I have done alot of them. I did a fresh install of 7.10 years ago, then 8.10, 9.04, and now 10.10. It seems like a struggle each time. 

Sorry, I guess I am venting. 

What's my next move?

---

