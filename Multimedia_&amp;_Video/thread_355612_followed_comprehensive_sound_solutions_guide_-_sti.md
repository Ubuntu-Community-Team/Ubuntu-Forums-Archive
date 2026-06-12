---
title: "followed comprehensive sound solutions guide - still have problems"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by dckirba on 2007-02-07
Hello all,

My sound disappeared after I tried installing a new gdm theme. I was pointed towards this excellent thread :
**comprehensive sound solutions guide** here [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound")

However, I have tried every single step listed and still have no module installed.

I have a VIA sound card that needs the VT82xx driver. I reinstalled alsa, even tried compiling it again, but it still gives me this error:

```
david@david:~$ aplay -l 
aplay: device_list:221: no soundcards found...
david@david:~$
```

alsamixer starts up when logged in as root, but not as normal user. All channels unmuted.
```

david@david:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```

Any suggestions are most welcome :) While we're at it, has anyone successfully installed this theme [http://www.gnome-look.org/content/show.php?content=50468]("http://www.gnome-look.org/content/show.php?content=50468"), because that's what started the problem?

I hope I can fix this without having to reinstall. 

Before I forget. i am using Dapper Drake. 

Startup sound works, login sound and everything after doesn't.

system>preferences>sound shows no default sound card.

And for /proc/asound/cards, I get this output ```
david@david:~$ cat /proc/asound/cards 0 [V8233A         ]: VIA8233A - VIA 8233A
                     VIA 8233A with ALC200,200P at 0xe400, irq 12
david@david:~$
```

Thanks a ton,
cheers,
David K

p.s: I had posted in the beginners forum before posting here. Sorry for crossposting, but the guide did say that if I still had problems after following the guide to post in this forum stating that I'd followed the guide.

EDIT: Problem resolved: [http://www.ubuntuforums.org/showthread.php?t=354506&page=1]("http://www.ubuntuforums.org/showthread.php?t=354506&page=1")

---

