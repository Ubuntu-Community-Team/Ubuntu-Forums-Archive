---
title: "Amarok 2"
date: 2009-04-25
forum: Multimedia Software
---

### Post by aaronkirk on 2009-04-25
I've know a great number of people are going to other players, however, I quite like the new Amarok. I particularly like the wide range of internet audio that comes preloaded unlike some other players. I had the same problems as a lot of people at first. BTW can be fixed easily: 

```
sudo apt-get install phonon-xine-backend libxine1-ffmpeg

```

Seemed to fix the audio device failing and no playback.
The only other thing I did was turn off OSD but I guess that's more of a personal preference. After this Amarok has worked well for me. I can't say I like the restyle and I miss the small pop-out style mini player I guess that's gone.

---

### Post by victorgreen on 2009-04-26
phonon-xine-backend isnt found??

I cant get amarok 2 to play ANYTHING at all. I just upgraded it with my whole distro to Jaunty 64.

---

### Post by optimusmedia on 2009-04-28
> **aaronkirk said:**
> 
```
sudo apt-get install phonon-xine-backend libxine1-ffmpeg

```


Should be: 

```
sudo apt-get install **phonon-xine-backend** libxine1-ffmpeg
```

BTW: This got Amarok2 working for me after upgrading to Jaunty 9.04

Found this link fixed all other audio problems I was having:

[http://ubuntuforums.org/showthread.php?t=885437]("http://ubuntuforums.org/showthread.php?t=885437")

---

