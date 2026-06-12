---
title: "slow video and no audio"
date: 2009-07-26
forum: Multimedia Software
---

### Post by tafito45 on 2009-07-26
Hi, I'm new with ubuntu I don't know what else to do..
I've installed many packageds and things but nothing seems to work.

When I see a video I can see it, but very very slow like if a didn't have the right codec. AVI format, MPEG 4, etc but i have installed many packaged codecs.

And with the sound just can't listen audio.

Ihave a HP pavilion Dv4 1212la

Tip, when I see the pulseaudio volumen device and play a song .. in the status bar of the volumen it shows like it's playing but i don't listen to it, a mean, the bar is moving..


thanks you very much.

---

### Post by tafito45 on 2009-07-26
> **tafito45 said:**
> Hi, I'm new with ubuntu I don't know what else to do..
I've installed many packageds and things but nothing seems to work.

When I see a video I can see it, but very very slow like if a didn't have the right codec. AVI format, MPEG 4, etc but i have installed many packaged codecs.

And with the sound just can't listen audio.

Ihave a HP pavilion Dv4 1212la

Tip, when I see the pulseaudio volumen device and play a song .. in the status bar of the volumen it shows like it's playing but i don't listen to it, a mean, the bar is moving..


thanks you very much.

tip2:
when i see drivers on the terminal shows me this:
tomas@tomas-laptop:~$ lspci | grep Audio -i
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
but i don't know if i'm using the right card..
and when i go to audio device, preferencess:
SELECT DEVICE:
HDA ATI SB(alsa mixer)
that's what I'm using. I have many options but the default one is this.

---

### Post by igorzwx on 2009-07-26
** 	[COLOR=#980101][B][ubuntu]**[/COLOR] pulseaudio on jaunty, HUGE headache!!!
[http://ubuntuforums.org/showthread.php?t=1221556](http://ubuntuforums.org/showthread.php?t=1221556)
[/B]

---

### Post by igorzwx on 2009-07-26
** 	[COLOR=#980101][B][ubuntu]**[/COLOR] Cannot hear music/videos  [/B]
[http://ubuntuforums.org/showthread.php?t=1220603](http://ubuntuforums.org/showthread.php?t=1220603)

---

