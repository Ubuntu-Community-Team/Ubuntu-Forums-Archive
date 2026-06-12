---
title: "Fixed Crackly Sound in Games, Somehow?!"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by psylem on 2008-01-01
I'm running a fresh install of Kubuntu Gusty on an ASUS A8J. The sound was crackling in games as has been reported by people using older versions on ubuntu with no real nice solution listed.

**I thought it was fixed but I was wrong...**
> I've already resolved this somehow, just thought it might be handy to post here what I found in case it helps others, and maybe someone else can help resolve it properly in the distribution. I don't know if it's a bug in Ubuntu, but it does greatly reduced user experience.

Well it seems I'm still getting issues, but it's now better than it was (as far as I can tell). I was using Sauerbraten to test it with and now that one is acceptable, but I noticed that I can still hear crackling a little, I checked the rest of the games and some are really bad still.

Amorak plays MP3's perfectly fine only games sound crackly.

Games I've tested:
Sauerbraten (tolerable if the music is low)
Tremulous (This one doesn't seem to be affected at all)
Warzone 2100
Enemylines7
Scorched3D
Starfighter
SuperTux (I cant' actually tell if this one is affected)
Ur-Quan Masters
Wormux (only sound effects affected, not music)

Basically, to try and fix it I blindly typed in commands I found around the place on slightly similar issues posted on these forums. Pretty dangerous, but eventually found a solution that worked on a post that was unrelated but they had the same model sound card. I don't understand how this fixed it but I just modified /etc/modprobe.d/alsa-base and added this line to the end of that file...```
options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0
```

Something else I tried before this was uninstalling libsdl1.2debian-alsa. This had tradgic results, I then quickly learned that adept doesn't warn you before uninstalling any packages which are dependant and doesn't have any history option like Synaptic, so you must always preview your changes :(. I then tried installing only libsdl1.2debian-oss but then later installed libsdl1.2debian-all (as well as reinstalling all my games again as well as Amarok, still don't know if I'm missing any multimedia packages now though).

At some stage I also ran this command:
```
sudo  apt-get install libsdl1.2debian-all alsa-oss
export SDL_AUDIODRIVER=dsp
```

If anyone has any ideas I'd be very grateful. This is really annoying :(.

References:
[http://ubuntuforums.org/showthread.php?t=370900](http://ubuntuforums.org/showthread.php?t=370900)
[http://ubuntuforums.org/showthread.php?t=407045](http://ubuntuforums.org/showthread.php?t=407045)

---

