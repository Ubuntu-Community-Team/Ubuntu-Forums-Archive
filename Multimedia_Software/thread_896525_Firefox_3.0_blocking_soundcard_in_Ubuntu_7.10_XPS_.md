---
title: "Firefox 3.0 blocking soundcard in Ubuntu 7.10 XPS 1330"
date: 2008-08-21
forum: Multimedia Software
---

### Post by shanki.na.s on 2008-08-21
I have Dell XPS M1330 with Ubuntu 7.10 working fine (no major problems).
I recently upgraded to Firefox  3.0 and I have been having some problems
with the sound card. I tried searching in several Ubuntu forums without
success; hence, this email.

Basically what happens is the following: When I listen to embedded
videos in the net, like for instance, BBC news the video and audio
works fine. Later, when I decide to listen music using xmms then
xmms reports "Your Sound card is blocked by some other application".

Then, I use the following command

> lsof |grep pcm

where it clearly shows that the firefox is still holding the audio device
(even though, I have stopped the BBC video). I then have to kill the process
and then restart the alsa-utils as a root.

I have been observing this pattern for about 2 weeks. Firefox 3.0 have media
related two addons -- Mediaplayer connectivity and Foxtunes. I guessed that
Mediaplayer connectivity and the firefox 3.0 application manager may
be in conflict and now I have disabled Mediaplayer connectivity.

I did not have any such problem with Firefox 2.0 which I had
used for more than 6 months.

Can some one let me know where is the problem? My
guess is that the flash player is holding the audio.

Thanks,
Shanki

---

