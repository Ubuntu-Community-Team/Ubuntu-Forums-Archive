---
title: "Full screen toggle with mplayer"
date: 2008-11-29
forum: Multimedia Software
---

### Post by JeppeV on 2008-11-29
Hey all!

After some work, I got (K)ubuntu up and running. It's great - No more windows:P

Anyway, i ran into some problems regarding playing videofiles.

I use this command to watch vids: mplayer -ao alsa -vo ggi filename.format.

I have to use GGI, or else the vid gets unwatchable. It's like every 10th frame is a black screen, hard to explain- Any thoughts?

Moving on. When I use the before mentioned command, I get a rather small screen, but the video plays without problems. The only thing is, I can't get it to go to full screen mode?! I have looked everywhere, but can't find anything:( Can I somehow add -fs or -f to the command? I'd like to use Vlc player, but can't find the GGI output option:(


My GC is an ATI hd2600xt, and yes - I have installed the 3d drivers etc.




Looking forward to your thoughts:)

Thanks.

Jeppe, Denmark.



SOLVED: Solution: Apparently GGI doesn't support full screen mode. Instead, I used the GL2(Open GL 2) output. I still have the frame error, but in full screen it's all gone

I used this command: mplayer -ao alsa -vo gl2  'directory'

---

### Post by JeppeV on 2008-11-29
Come on guys:( Saturday night and no movies?:(

---

### Post by mc4man on 2008-11-29
don't know if this will help or hurt

[http://packages.ubuntu.com/hardy-updates/vlc-plugin-ggi](http://packages.ubuntu.com/hardy-updates/vlc-plugin-ggi)

or click the intrepid tab if that's what your using

What happens if you use 

mplayer -ao alsa -vo ggi -fs filename.format

or click the intrepid tab if that's what your using

---

### Post by JeppeV on 2008-11-29
> **mc4man said:**
> don't know if this will help or hurt

[http://packages.ubuntu.com/hardy-updates/vlc-plugin-ggi](http://packages.ubuntu.com/hardy-updates/vlc-plugin-ggi)

or click the intrepid tab if that's what your using

What happens if you use 

mplayer -ao alsa -vo ggi -fs filename.format

or click the intrepid tab if that's what your using

Hey!

See first post i about 2 minutes. Thank you for your time:)

Jeppe.

---

