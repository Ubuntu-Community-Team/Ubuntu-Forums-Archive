---
title: "DX-SC7.1 and Alsa"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by Ramaddan on 2006-07-06
Hi,

1 - I bought the Dynex 7.1 sound card of eBay, and the manufacturer
refuses to tell me what the pins layout of the card is,
because I did not buy it from their dealers. :-x 

If anyone knows what the pins layout is, could they post it here,
or send me a message? Thanks.

I can see the pins on the board to which I can plug the PC case
output/input wires for the microphone and headset at the front,
but I don't know how to plug the wires, since I don't know which
pin is for which.

2- The other problem is just more of a nuisance than a problem.

It's to do with ALSA (I think). Sometimes when I play a flash video
in Firefox, it blocks sound being played anywhere else, until the flash
video is exited.

Or if I play sound else where, like in mplayer, then I cannot hear sound
from a flash video in firefox till I restart firefox.

It seems there are problems of sharing the sound card.
I think the Dynex 7.1 uses the CMI8768 audio chip from C-Media.

I also attached a picture to this post of the card,
hoping that it helps in any way.

Thanks for your help.

---

### Post by Ramaddan on 2006-07-08
Hi,

Maybe I should mention that the ALSA problem is a more important problem,
and I noticed many have this problem.

Thanks

---

### Post by LordRaiden on 2006-07-08
If you are using GNOME, I think you have to pick what card and output type it uses. 

If not do the following.

```
sudo apt-get install alsa-oss
```

then run firefox with

```
aoss firefox
```

It should work.

After that change the firefox link from 'firefox' to 'aoss firefox'

However, I thought that this issue was solved a while ago, as I no longer need to do this configuration.

---

### Post by Ramaddan on 2006-07-08
Hi Raiden,

Thanks for your help. The workaround worked :-D

Now I hope that someone can help me with my first problem.

Thanks.

---

