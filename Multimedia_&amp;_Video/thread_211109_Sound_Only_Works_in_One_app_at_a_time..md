---
title: "Sound Only Works in One app at a time."
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by jak-_- on 2006-07-07
Ok, being a gamer, this is really starting to peeve me off...

I run vent -> run game, no sound ingame.

I run game -> run vent, no sound from vent...

Gives an error similar to: 'sound device in use'.. which.. well I'm not too sure what it's trying to imply, but it sounds pretty messed up, anyone got any idea's before I go insane?

---

### Post by LordRaiden on 2006-07-08
You need to configure both you game and ventrilo to use alsa output. Otherwise, download alsa-oss (sudo apt-get install alsa-oss) then run your programs like so 

```
aoss /path/to/program
```

---

### Post by rivethead on 2006-07-09
That doesnt work , ive set up vent in cedega and wine to use Alsa and run Quake4 using alsa aswell, same problem as above sound only works in one app at a time.

---

