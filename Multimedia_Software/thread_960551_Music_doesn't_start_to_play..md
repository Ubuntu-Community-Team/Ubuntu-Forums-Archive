---
title: "Music doesn't start to play."
date: 2008-10-27
forum: Multimedia Software
---

### Post by gryzzly on 2008-10-27
Sometimes after I boot my computer and start music player (whatever which one of them: exaile, movie player, rhythmbox etc...) It loads files and it just doesn't start to play. 

I can move "playing" bar, but no result also.

When I reboot everything is usually fine.

Anyway, I was preety much sure that it has something to do with my notebook or something, and for me it was not that big problem, cuz in such a case I was just starting some streaming-flash radio over web. 

But I installed ubuntu on my parents machine and music is preety important part of their computer use, and this is thing is happening to them also. And I can't tell my father to reboot all the time, but I don't want to install windows back as well. 

Please help.

---

### Post by unknownmosquito on 2008-10-27
I have this problem also, from time to time, but generally if I'm listening to music and using flash on the internet...

I usually log out and log back in and that works. Try running
```
$ pulseaudio -k && pulseaudio &
```

If it's for your parents you could always (I know this is really hackish but I digress) throw that into something like fix_my_sound.sh and then give them a shortcut on their panel/desktop.

---

### Post by gryzzly on 2008-10-27
Thanks for response. Right, it has something with flash, I also think. When I can use flash, then I can't use usual music and vice versa.

GHmmm. I am sure ther is some solution. Hardy is third distro I am using and I didn't have it before some time...

---

### Post by gryzzly on 2008-11-02
> **unknownmosquito said:**
> I have this problem also, from time to time, but generally if I'm listening to music and using flash on the internet...

I usually log out and log back in and that works. Try running
```
$ pulseaudio -k && pulseaudio &
```

If it's for your parents you could always (I know this is really hackish but I digress) throw that into something like fix_my_sound.sh and then give them a shortcut on their panel/desktop.

I tried this line and it didn't do the trick. Thanks for response 

:(

---

### Post by waffen on 2008-11-02
Are you try install the flashplugin-nonfree? I use a 64bit Ubuntu, where I was read is usual see flash errors but in my case I dont have any... Flash works fine with my Firefox...

---

### Post by gryzzly on 2008-11-07
> **waffen said:**
> Are you try install the flashplugin-nonfree? I use a 64bit Ubuntu, where I was read is usual see flash errors but in my case I dont have any... Flash works fine with my Firefox...

Thank you for response.
No, it's not that I am trying to install flash-plugin, actually flash worsk fine. Only sometimes sound stop working or for flash (if I am listening to usual mp3s, for example), or for usual mp3s if I was listening to some music through flash (some internet radio, for example).

And the same happens to my father's computer. Which is worse, cuz he's not geek and I don't want to tell him any time “open terminal, type «sudo» and do something else...” — I want to set everything up and let him just use it. Like home media center. So with this music problem it doesn't seem so good media center :(

---

