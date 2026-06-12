---
title: "[SOLVED] blender movie editor, i can't hear sound.."
date: 2008-04-09
forum: Multimedia Production
---

### Post by Creative2 on 2008-04-09
yes i am trying to use blender for movie editor ...

but :D i have not sound when i try to play my video just imported on blender.

it seems like cinelerra on this, i have installed by repository but i think i have not some library , i have installed jackd and jack controll , for other use anyway..

- well i have set sampling rate to 44100 but nothing to do ...the same

some ideas ?

---

### Post by oscarsfriend on 2008-04-09
There is a bug in blender affecting the sound: [https://bugs.launchpad.net/ubuntu/+source/blender/+bug/44131](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/44131)

The solution (which worked for me and some others) is to run blender from the terminal like this:
```

export SDL_AUDIODRIVER=alsa && blender -g noaudio

```
Then make sure you click the little speaker icon in the blender sequencer.  You can replace alsa with some other audio driver if you want.  You can easily modify the kmenu entry for blender so that it does the above when you launch blender from there.

---

### Post by Creative2 on 2008-04-09
hey solved :D thanks a lot

---

### Post by cotcot on 2008-04-09
Had the same problem. I made the sound working  by adding [COLOR="Red"]SDL_AUDIODRIVER=alsa[/COLOR] in [COLOR="Red"]/etc/environment[/COLOR] and restarting the computer. Blender start with the normal launcher.
Oscarfriends :BTW lovely Siamese !

---

